# Ghostwriters 👻

Downloads and updates for **Ghostwriters**, a fill-in-the-blank word game you play with your AI companions
(Kindroid, Nomi, ChatGPT, Claude or a local model). Nobody sees the story until it's revealed.

**Download:** see [Releases](../../releases/latest): `Ghostwriters-Mac.dmg` or `Ghostwriters-Windows-Setup.exe`.
Ghostwriters updates itself, and new card packs show up on their own.

---

## Adding a card pack (for Genna)

1. Make `packs/<id>.json` (id: lowercase letters, numbers and dashes, like `thanksgiving`):

   ```json
   {
     "id": "thanksgiving",
     "name": "Thanksgiving",
     "emoji": "🦃",
     "description": "Gravy, chaos and one very nervous turkey.",
     "version": 1,
     "cards": [
       { "id": "tg-dinner-toast", "title": "A Toast to the Family", "emoji": "🥂", "text": "Thank you all for coming to my {adjective} dinner…" }
     ]
   }
   ```
   Blanks are `{type}` (adjective, noun, plural_noun, verb, verb_ing, verb_past, adverb, exclamation, sound, silly_word,
   body_part, body_part_plural, animal, food, liquid, color, number, place, room, clothing, occupation, celebrity, name,
   emotion, vehicle, song). `{name#host}` remembers a word, `{#host}` repeats it. Paragraphs: a blank line (`\n\n`).
   Card ids must be unique across all packs, so prefix them (`tg-…`).
2. Add it to `packs/index.json`: `{ "id": "thanksgiving", "version": 1 }`.
3. Check it from the Ghostwriters project: `npm run check-pack ../ghostwriters-releases/packs/thanksgiving.json`
4. Commit and push. Every Ghostwriters picks it up at its next launch (or with "↻ Check for new cards").

To fix a pack: edit it, bump `version` in **both** the pack and index.json, push.
To pull a pack: remove it from index.json and push (it disappears from everyone's game).
A pack needing a newer app: add `"minApp": "0.2.0"` to its index entry; older copies skip it until they update.
