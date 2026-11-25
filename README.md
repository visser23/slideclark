# SlideClark: a slide editor you bring your own AI to

[SlideClark](https://slideclark.com) is a free slide editor that runs in your browser. It has **no AI of its own**: you ask ChatGPT, Claude, Gemini or any other AI (including a local model) for a deck, and it opens in SlideClark as real slides you can edit by hand, present, and export to PowerPoint or Figma.

Slides can be template layouts, free-form objects, or **HTML, CSS and JavaScript** written by the AI and editable visually. A deck is plain JSON (a `.sldc` file).

This repository holds the public documentation, JSON Schema and example decks. The editor itself is the website, [slideclark.com/app](https://slideclark.com/app); its source code is not in this repository.

## What is here

| Path | What it is |
| --- | --- |
| [`docs/ai-guide.md`](docs/ai-guide.md) | The guide an AI reads to write a deck: file format, layouts, free-form objects, custom HTML slides, the in-browser JavaScript API. |
| [`docs/slideclark.schema.json`](docs/slideclark.schema.json) | JSON Schema for a `.sldc` deck. |
| [`llms.txt`](llms.txt) | The same summary and facts we publish for AI assistants. |
| [`examples/`](examples) | Four decks and one HTML file you can open straight in the editor. |

The copies here are a snapshot. The always-current versions are at [slideclark.com/ai-guide.md](https://slideclark.com/ai-guide.md), [slideclark.com/slideclark.schema.json](https://slideclark.com/slideclark.schema.json) and [slideclark.com/llms.txt](https://slideclark.com/llms.txt).

## Try it in a minute

1. Open [slideclark.com/app](https://slideclark.com/app), choose **Open** (or **AI**, then **Import**).
2. Drop in a file from [`examples/`](examples): `investor-pitch.sldc`, `product-launch.sldc`, `quarterly-memo.sldc`, `custom-html-slide.sldc` or `standalone-slide.html`.
3. Click, drag and restyle anything. Press **Present**.

Or start from your own AI: press **AI** in the editor, copy the prompt it builds into any chat AI, and import the `.sldc` it returns.

## How an AI connects

- **Any chat AI**: SlideClark builds a prompt; the AI returns a `.sldc` file or JSON; you import it. Works with local models.
- **A browser agent** (for example Claude for Chrome or Comet): it edits the open deck through the documented global `SlideClark` object in the page, for example:

```js
SlideClark.addCustomSlide({
  html: '<h1>Churn fell to 2.1%</h1>',
  css: 'h1{font:700 96px system-ui;margin:200px 100px}',
  js: '', interactive: false
}, 1, 'Retention');
SlideClark.auditAll();   // measures the rendered slides and reports overflow or overlap
```

Every call is validated and undoable. The full method list is section 11 of [`docs/ai-guide.md`](docs/ai-guide.md).

## Facts, stated plainly

- Built-in AI: **none**. No model, no API key, no calls to an AI service.
- MCP server: **none**. REST API: **none**. The programmatic route is the in-browser `SlideClark` object above.
- Opens: `.sldc`, PowerPoint (`.pptx`, as editable HTML slides) and self-contained `.html` files (inline styles and scripts; linked files are reported and left out).
- Saves: `.sldc` and PDF free; editable PowerPoint (`.pptx`) and Figma (`.fig`) are Pro, from £1.99.
- Privacy: decks stay in your browser, nothing is uploaded, no account is needed to edit.
- Not offered: simultaneous multi-user editing, an embeddable editor SDK, a built-in AI.

## More

- [HTML slide editor](https://slideclark.com/html-slide-editor)
- [Slide editor for AI agents](https://slideclark.com/ai-agent-slide-editor)
- [Make slides with ChatGPT](https://slideclark.com/chatgpt-powerpoint), [Claude](https://slideclark.com/claude-powerpoint), [Gemini](https://slideclark.com/gemini-powerpoint)
- [HTML to PowerPoint](https://slideclark.com/html-to-powerpoint)
- [Pricing](https://slideclark.com/pricing)

The documentation, schema and examples are MIT licensed (see [`LICENSE`](LICENSE)). The SlideClark name, logo and editor are not covered by that licence.
