---
name: ms-japanese-style-docs-plus
description: >-
  Creates Japanese PowerPoint decks, Word documents, and Excel workbooks whose
  text follows the public Microsoft Japanese Localization Style Guide plus
  explicit house rules — Microsoft
  voice, half-width/full-width punctuation and spacing, noun-phrase headings,
  ですます調 body text, and customer-facing polite tone. Use when the user asks
  to "create a PowerPoint/Word/Excel file in Japanese", "make a deck or
  document following the Microsoft style guide", "日本語でスライド/資料/
  ドキュメント/表を作って", "Microsoft スタイルガイドに沿った提案書・報告書・
  一覧表", "customer deck or proposal in Japanese", "日本語で Word の資料を
  作って", "日本語で Excel の一覧表を作って", or to apply Microsoft Japanese
  style to slide, document, or worksheet text. Do NOT use for English-language deliverables, or for
  reviewing wording without producing a .pptx / .docx / .xlsx file.
  Authored by Takuya Ohta (Takuya Ohta 作成).
license: MIT
metadata:
  category: writing
  icon: SlideText
  version: "2.0.0"
---

# MS Japanese Style Docs+

_作成者: Takuya Ohta (Created by Takuya Ohta)・作成日: 2026 年 7 月・更新日: 2026 年 11 月 21 日・バージョン: v2.0.0 (公開資料ベース版)_

Generate Japanese PowerPoint decks, Word documents, and Excel workbooks whose
wording, punctuation, spacing, and tone conform to the **Microsoft Japanese
Localization Style Guide**. This skill owns the *language and style layer* only;
file construction is delegated to the built-in `pptx`, `docx`, or `xlsx` skill
depending on the deliverable.

This public edition is based on the official public guide and explicitly
identified house rules.

## When to Use

Use when the user wants a Japanese deliverable that reads like polished
Microsoft content — internal briefings, customer/sales decks, product overviews,
proposals, reports, manuals, SOPs, checklists, item lists, trackers — or asks
explicitly for the Microsoft style guide to be applied to a deck, document, or
worksheet.

Trigger examples:
- "日本語でプレゼンを作って" / "この内容でスライドを作成して"
- "Microsoft のスタイルガイドに沿った PowerPoint にして"
- "make a customer deck in Japanese"
- "顧客向けの提案資料を PowerPoint で"
- "apply the Microsoft Japanese style to these slides"
- "日本語で提案書/報告書を Word で作って"
- "Microsoft スタイルガイドに沿った Excel の一覧表を作って"

## When NOT to Use

- **English (or non-Japanese) deliverables** — use the built-in `pptx` / `docx`
  / `xlsx` skill directly.
- **PDF deliverables** — use the built-in `pdf` skill.
- **Reviewing wording without producing a file** — just answer inline using the
  rules in `references/style-rules.md`; do not build a file.
- **Fabricating business facts** — if the user hasn't supplied the content and
  it can't be found in M365, leave a clearly-marked placeholder; never invent
  figures, quotes, customer names, or dates.

## Reference Material

- [style-rules.md](./references/style-rules.md) — core rules for all three
  formats. Always read it, starting with the explicit house rules in §0.
- [document-conventions.md](./references/document-conventions.md) — document
  structure, UI labels, keys, numbers, and product names. Always read it too.
- [kana-kanji-okurigana.md](./references/kana-kanji-okurigana.md) — a concise
  lookup procedure grounded in the public guide's character references. Read
  it when unsure about kana, kanji, or okurigana; it is not a dictionary.
- [Microsoft Japanese Localization Style Guide](https://aka.ms/japanese-styleguide)
  — the public source of truth, except for the explicit house rules in §0.
  The PDF is not bundled with this public skill.
  Consult it when a case isn't covered by the cheat sheet. The official
  [style guide catalog](https://learn.microsoft.com/ja-jp/globalization/reference/microsoft-style-guides)
  provides the current download link.

## Workflow

1. **Pick the target format first.** Slides / deck / プレゼン → `pptx`;
   prose document, 提案書, 報告書, 手順書, 議事録, letter → `docx`;
   row/column data, 一覧, 表, 台帳, 予算, トラッカー → `xlsx`. If the user names
   a format, honor it. If not, choose by the shape of the content and say which
   you chose.
2. **Gather the content.** If the user supplied the material, preserve its facts,
   numbers, names, dates, conditions, and intended meaning while adjusting
   wording, tone, punctuation, and spacing according to this skill's rules.
   Keep exact quotations and fixed strings unchanged, and honor explicit
   requests to retain the original wording.
   If they named a topic but no content, search M365 (`SearchM365`,
   `ListMessages`, `ListCalendarView`) for the real facts before drafting. Use
   clearly-marked placeholders (e.g. `<Q3 の売上を記入>`) for anything missing —
   never fabricate.
3. **Load the rules.** Read [style-rules.md](./references/style-rules.md) and
   [document-conventions.md](./references/document-conventions.md). Consult
   [kana-kanji-okurigana.md](./references/kana-kanji-okurigana.md) for spelling
   questions. For edge cases not covered there, consult the relevant section of
   the public guide linked above; do not read the whole guide unnecessarily.
   If external access is unavailable, explicitly flag any unresolved rule and
   ask the user for the relevant source before finalizing the affected text.
   Do not guess a rule or claim it was verified against the official guide.
4. **Draft the Japanese text, applying the style layer:**
   - **Headings, titles, bullet item names, Word 見出し, Excel の列見出し・
     シート名 → 原則として体言止め (noun phrase)**.
     Use a short plain-style verb phrase when a noun phrase would obscure the
     meaning, keeping the same heading level consistent.
   - **Body / explanatory text → ですます調**, consistent within each file.
   - **Punctuation & symbols**: follow §0 and §3. Keep Japanese 。、「」『』・ー;
     use ASCII forms for punctuation that has an ASCII equivalent, including
     `()` for parentheses. Use `...` for ellipses and 「から」 or `-` for ranges.
     In Japanese prose, place one space on each side of `:`. Do not alter
     colons in fixed strings such as URLs, times, paths, code, or formulas.
     Use ・ for names or parallel words, not to split katakana compounds.
   - **Spacing**: one half-width space between full-width and half-width text
     (`Word を使用` / `第 3 章` / `Shift キー`), honoring the §4 exceptions.
   - **Document elements**: follow the public rules and separately marked
     house conventions in `references/document-conventions.md`.
   - **Word choice**: swap stiff words for everyday ones (可能です→できます,
     推奨→お勧め, 再度→もう一度, 詳細な→詳しい); drop unneeded あなた/私.
   - **Tone**: for customer/sales decks use polite 丁寧語 (ご確認ください,
     お使いいただく) and 弊社 for Microsoft; avoid over-polite/mechanical phrasing.
   - **Terminology**: match Microsoft product/UI names; leave untranslated when
     unsure rather than guessing.
5. **Self-check against the §7 checklist** in `references/style-rules.md` before
   building anything. Fix any violation in the text first.
6. **Build the file via the matching built-in skill**, passing the finalized
   Japanese text. **Fonts (mandatory, all three formats): Japanese (kana, kanji,
   full-width punctuation) → `Yu Gothic UI`; English/Latin (ASCII letters,
   digits, half-width symbols) → `Segoe UI`.** For mixed strings, split by script
   and set the font per run so each script uses its own face — no exceptions or
   substitutes.
   - **`pptx`** — keep line lengths short; full-width text clips sooner than
     Latin. Set `fontFace` per run.
   - **`docx`** — apply the two fonts to every style used (見出し, 本文, 表,
     キャプション): East Asian font `Yu Gothic UI`, Latin font `Segoe UI`. Use
     原則として体言止め for headings and ですます調 throughout the body; keep one consistent
     level of politeness across the whole document.
   - **`xlsx`** — set the two fonts on all cells including headers. Column
     headers and sheet names use 原則として体言止め and stay short; notes/説明 cells use
     ですます調. Numbers use half-width digits with half-width `,` separators and
     a half-width space between digits and units (`2,000 ページ`); dates follow
     the §3 half-width rules (`2011/1/13`). Never let style rewriting change a
     numeric value or a formula.
7. **Deliver.** Confirm the file exists in `output/` (`Glob output/**/*`), then
   tell the user the file is ready and note 2-3 style choices you applied (e.g.
   "見出しは体言止め、本文はですます調に統一しました").

## Output Format

- A `.pptx`, `.docx`, or `.xlsx` file saved to `output/`, matching the format
  chosen in step 1.
- A short plain-language summary: what the file covers, and the key Microsoft
  Japanese style conventions applied. Flag any placeholders the user must fill.

## Guardrails

- The **public guide is the source of truth** except for the explicit house
  rules in `references/style-rules.md` §0. Apply those house rules where they
  differ and identify them as this skill's choices, not official requirements.
  All other disagreements are resolved in favor of the public guide.
  The official PDF is referenced by URL rather than redistributed.
- Use only publicly available sources and the explicit house rules. If a rule
  cannot be verified publicly, flag it rather than guessing.
- **Consistency within a file**: don't mix ですます調 and である調 in body text;
  keep heading, 見出し, and column-header style uniform across all slides,
  sections, and sheets.
- **Excel data integrity**: style applies to labels and prose only — never alter
  numeric values, formulas, IDs, or product names to satisfy a wording rule.
- **Never fabricate** names, numbers, quotes, dates, or customer references —
  use visible placeholders instead.
- **Don't over-apply casual voice** to formal customer deliverables; balance the
  "warm and relaxed" principle with appropriate 丁寧語.
- **Fonts are fixed in every format** (pptx / docx / xlsx): Japanese →
  `Yu Gothic UI`, English/Latin → `Segoe UI`, on every text element (title,
  headings, body, captions, notes, table cells, column headers). Split mixed text
  by script and assign the font per run. Never substitute Meiryo, Yu Gothic, Noto
  Sans JP, Arial, Calibri, or any other face.
- Produce the final artifact in `output/`; verify before announcing it's ready.

## License

Original content in this skill is licensed under the MIT License.
Copyright (c) 2026 Takuya Ohta. Microsoft source materials, trademarks, and fonts
are excluded. Include the repository's `LICENSE` when redistributing this skill.
