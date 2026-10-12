# School Contributions – Bago National High School

Live lookup page: https://raymartvalbarez.github.io/school-contributions/

Static `index.html` (no build step) on GitHub Pages. On every load it reads the Google Sheet
`1q586zU0z4bvMp44lQprMWLjcnkaTiG3jPcXl7k53nnY` live (CSV export per tab gid + cache-buster,
then gviz CSV fallback, then the embedded `SNAPSHOT` as a last resort). Sheet edits show up on
refresh – no redeploy needed. The sheet must stay "Anyone with the link – Viewer".

## Adding rows
No header row. Column A = name, column B = amount (if B is blank the tab's fixed amount is used:
₱400 road, ₱50 balloons). Just type the new row in the sheet.

## Adding a tab (new collection)
1. Add the tab in the sheet, open it and copy the number after `gid=` in the URL.
2. In `index.html`, add an entry to `COLLECTIONS`, e.g.
   `{key:"xmas", title:"Christmas Party – ₱200", short:"Xmas ₱200", gid:"123456", fixed:200, firstNameOnly:false}`
   and add `xmas:\`\`` to `SNAPSHOT`.
3. Commit and push; GitHub Pages republishes in about a minute.

## "Not yet paid" list
The faculty list is read live from column A of the condolence sheet
(`1kSqsrgzDbwP-M8v_v5WBc0qKsnHsWhq_jrxsBcg0hcc`). Names match case-insensitively, ignoring middle
initials; `firstNameOnly` tabs also match by first name. If a first name fits more than one teacher,
the entry is shown as written (not guessed). Names not on the faculty list are still shown as paid.
