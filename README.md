# Overnight changelog

## 22 November 2026, football content batch
- Expanded source snapshot to 50,940 distinct player profiles, 817 first-tier club records, 124 national teams. Transfer history also has 17,554 club-name nodes, not claimed as full club profiles.
- Includes 876 distinct Egyptian 2025/26 squad-page players across 21 clubs, and 813 Saudi-linked player profiles. Forty-three Egyptian players listed under multiple clubs have club and shirt fields excluded.
- Generates 54,478 question variants across 12 field-based types. These are not 54,478 independently edited trivia questions. Four fame-proxy tiers from peak valuation, caps, league and last season. No inferred trophy or all-time-top-scorer data.
- Twenty-one thousand nine hundred seventy-nine transfer-history paths before tier filtering. They are selected recorded stations, not guaranteed complete careers.
- Content fetched only when requested or entering a fast/local game, compressed into 19 text transport chunks, about 4.5 MB before HTTP compression. Crossword remains immediately usable without the pack.
- Basic snapshot frozen 6 July 2026, Egypt 2025/26 season pages retrieved 22 November. Names mostly in original Latin script. No crests/photos.
- Tested two independent browser contexts through five risk rounds and five career rounds, same shared choices, hidden answers, matching scores, no JS errors. Re-tested local eight formats and crossword. Not a physical phone/carrier test.

Previous documentation below remains historical where it describes smaller content banks. PWA installation, expanded identity rounds, more crosswords and Arabic entertainment are next batches, not yet shipped in this entry.

---

# عمدة الكورة

Standalone Arabic football web game. Live: https://youssecemad22-stack.github.io/omdet-elkora/

## Main game: تقاطع الكورة
- Seven original connected mini-crosswords, nine answers each, max 12×12. Sparse interlocking grids, not newspaper-standard fully checked grids: not every letter is crossed.
- Shared daily selection using the Africa/Cairo calendar date. Seven-board starter bank rotates weekly. The same answers can occur in multiple boards; these are not 63 unique facts.
- Arabic right-to-left across words and top-to-bottom down words. One letter per square. A visible Arabic keyboard, cell selection, crossing-direction toggle, clue list, backspace and undo.
- Normalization: أ/إ/آ become ا, ى becomes ي, spaces are omitted. ة and ه remain distinct.
- Word check adds 20 seconds. Revealed letter adds 45 seconds. Wrong typing has no penalty. Assistance is virtual time only, never money.
- Letters and assistance costs save to localStorage per Cairo date and board. Time currently measures the current open session, not a reliable cross-session record. No cloud history, streaks or global ranking.
- Two-phone race: same puzzle/start, private letters, shared filled-cell counts. Host validates completed grids and records elapsed time plus declared assistance. Finish after both complete or 15 minutes. No winner is awarded on detected disconnect. Friendly play only: client code contains answers, hints can be manipulated by a modified client, and the host controls timing. No anti-cheat claim.
- Direct PeerJS public signaling and Google STUN. No paid relay/TURN. Restrictive mobile networks can fail. Keep both pages foregrounded. No reconnect/resume.

## Preserved secondary games
Three simultaneous tap-choice online modes: risk quiz, selected player careers, and flag/original-kit identity. Two-second start, shared reveal, paced automatic next round. Four editorial difficulty tiers, not measured ratings. Some small identity pools repeat.

Nine local shared-device formats: bank, risk, password, imposter, auction, careers, rondo, charades, identity. Optional Arabic speech input on selected free-recall fields, supported browser required, opt-in microphone, transcript confirmed before use. Audio may be processed by the browser's service. Real iPhone recognition accuracy is untested.

## Content and provenance
216 question variants, including 24 additions on selected 2025/26 major finals, not full coverage of all completed competitions. Original historical bank: 192 variants on 64 finals. Career snapshots cover selected stations through 2024, not full live careers. Identity bank: 24 entries, flags drawn with original SVG and club clues using original shirts/colors, no copied club crests or player photos. Source URLs are stored beside entries. Disputed AFCON 2025 winner questions are excluded. Research folder distinguishes source attempts, readable sources and applied ideas.

## Build
`npm ci && npm run build && python compact.py`
- src/: editable React/TypeScript source.
- make-crosswords.py: deterministic grid generation and crossing validation.
- build.mjs: standalone inline HTML, Cairo font under its OFL license.
- compact.py: gzip/base64 wrapper for deploy size, using DecompressionStream (current browser required).
- dist/index.html: full standalone build, useful offline for solo. Online needs network.
- dist/index-compact.html: deployed wrapper.
- test-crossword.mjs: solo assistance/save/solve/practice, responsive overflow checks, two-context real WebRTC race and score validation.
- test-tap-rounds.mjs: three online tap-choice flow tests, updated for the crossword home. Historical test scripts may contain prior UI selectors; they are retained as source, not all current passing claims.

No backend or accounts added. No paid services or app-store release. Repository is a standalone project, separate from Meshwar.
