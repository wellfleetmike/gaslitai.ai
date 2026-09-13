# CLAUDE.md -- gaslitai.ai

## What this repository is

A static evidence site, served at https://gaslitai.ai via GitHub Pages,
documenting classifier interference, conversation redaction, export gaps,
and search suppression as they appear in one operator's Claude export,
screenshot set, and curator passes. Companion to anticognitarianism.ai.
Mechanism, not motive. Every claim points at a timestamp, a hash, or a
screenshot. The reader verifies; the site presents.

## Hard rules

- NEVER modify, rename, recompress, resize, or strip metadata from any file
  in /images/. Screenshots are evidence. Original camera-roll filenames and
  EXIF data are part of the chain of custody. Read-only, always.
- NEVER delete or rewrite existing evidence pages to "clean them up" without
  an explicit instruction naming the file and the change.
- All text files are strict ASCII: double hyphens instead of em-dashes,
  straight quotes only, no curly quotes, no typographic substitutions.
  Non-ASCII characters inside quoted message text are written as numeric
  character references in HTML and as \uXXXX escapes in text files. Verify
  with grep for non-ASCII bytes before committing.
- No analytics, trackers, external scripts, third-party embeds, or CDN
  fonts. The site is static, self-contained, and works from file://.
- manifest.txt is append-only: one line per evidence file, format
  filename | date | source | what it shows | context. Never rewrite prior
  lines. checksums.sha256 covers every file except itself; regenerate it
  after any change and commit both.
- Evidence pages state only what the artifacts support. No interpretation
  of motive, no diagnosis, no speculation. Where a message in the export
  makes a claim, quote it with its timestamp and call it a claim.
- Update sitemap.xml when a page is added.

## Layout

- index.html -- layer 0: summary numbers, navigation
- methodology.html -- layer 4: how every number was produced
- classifier/index.html -- layer 1: flag search, pattern table, all conversations
- classifier/<uuid8>-<slug>.html -- layer 2: one conversation (top 20 by hits)
- redacted/index.html -- the redaction tables, platform search versus export
- redacted/unmatched.html -- screenshots with no turn within 30 minutes
- search/index.html -- logged zero-result probes for the word
- timeline.html -- dated events across all categories
- screenshots/<filename>.html -- layer 3: one screenshot
- images/ -- byte-identical copies of the screenshots used, original names
- manifest.txt, checksums.sha256, sitemap.xml, llms.txt, robots.txt, CNAME

## Sources (read-only, not in this repository)

- ~/Desktop/nu/backup/memory/memory.db -- conversations and messages tables
  (281 conversations, 44987 messages, ingest 2026-09-12T10:00:01Z)
- ~/Desktop/nu/memory/memory.db -- curator_findings table (1475 rows)
- ~/Desktop/nu/pics_manifest.jsonl, pics_matched.jsonl -- 802 screenshots
- ~/Desktop/nu/curator_pass/claude_pics/ -- the screenshot files
- ~/Desktop/nu/curator/blocks/ -- one file per export content block
- ~/Desktop/nu/CLASSIFIER_AND_COMPACTION.md, CLASSIFIER_SCREENSHOT_CROSS.md
- ~/Desktop/nu/conversations/ -- 281 conversation markdown files
- Export: /home/mike/Desktop/nu/convo/conversations.json, sha256 1d7a0742267da9bcf0f174c54b23205a6842cbccf13f51ef5cadf6781f92720f

## Assumptions

- "Flag" on this site means a message whose text matches one of fourteen
  search phrases. The brief gave 951 flags in 130 conversations, which is
  the count for the bare word "classifier" alone; the site reports the full
  fourteen-pattern count (1002 messages, 143 conversations) and shows the
  per-pattern breakdown so the two figures reconcile.
- The brief gave 61 conversations with both flags and screenshots. The
  association rule used (any of a screenshot's three nearest turns) gives
  a different count; the classifier index shows the per-conversation
  screenshot count so the reader can apply any threshold.
- The brief referred to fourteen redacted conversations. The artifact on
  disk (two recent_chats tool results of 2026-09-10) marks 24 chats as
  redacted: fifteen in the July 16 to August 2 window and nine after
  August 20. The site reports the artifact.
- Conversation pages exist for the top 20 by flag hits; the remaining
  conversations appear in the full table on the classifier index.
- Curator findings attach to a conversation when the finding's source name
  equals the conversation title after normalization to letters and digits.
- Screenshot content is not described beyond what filename, EXIF, and the
  nearest turn establish. Nobody viewed the images to caption them.
- Timeline entries that cite anticognitarianism.ai name the file on that
  site rather than reproducing it, except where the same file is
  byte-identical in this site's screenshot set.
- The "connector" section of the methodology page describes the platform
  recent_chats tool through which the redaction markers arrived, since
  that is the connector the artifacts document.

## Missing

- /home/claude/Anticognitarianism.ai/ -- not on disk; the reference site
  was cloned from GitHub into a scratch directory for style only.
- ~/Desktop/nu/py/ (turnspine.py, clx.py, schemaweaver.py) -- not on disk;
  described from the curator work order and the curator RUNBOOK.
- SIGNAL_20260901_fork_chains.md (sha256 d8f6b9c2...) -- not on disk; fork
  chains were recomputed from the export instead.
- The July 16 and September 1 exports referenced in messages -- not on
  disk; the site cannot verify the claim that a window was absent from them.
- A second vendor's search-probe log for the word -- not on disk; the
  two-vendor statement is quoted as a claim with its timestamp.
- Screenshot_20260713_204344_Chrome.jpg and Screenshot_20260902_112859_Chrome.jpg
  (Google captures) -- not in this site's screenshot set; linked by full URL
  on anticognitarianism.ai.
- The catalog.db is not a source for this site; INVENTORY.md was read but
  nothing on the site depends on it.

## Build

Generated 2026-09-13T01:01:41Z by build_site.py (scratch, not committed) from the sources
above. Re-running the generator against unchanged sources reproduces the
same pages; images are copied byte-for-byte and verified against the
manifest hashes.
