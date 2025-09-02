# Mini Form Builder (Local, URL-Shareable)

A single-file HTML+JS **form builder & renderer**.  
- **Local only** (no backend needed)  
- **JSON-driven DSL**  
- **Share via URL hash** (`#f=...`) with base64url-encoded JSON  
- **Render-only mode** when a hash is present (Typeform-style share page)  
- Optional **POST** to your endpoint (`send.url`)  
- **Export HTML** to a standalone file

---

## Quick Start
1. Open `form-builder.html`.
2. Edit JSON in the left panel → **Apply**.
3. **Share Link** to encode JSON into the URL hash and copy to clipboard.
4. Visit the shared link: page loads **render-only** (no editor), with your form.
5. **Submit** to see a local preview of submission JSON (and optional network send).

**Note:** This project stores your last JSON in `localStorage`.

---

## DSL (Schema)

### Form
```json
{
  "title": "string",
  "description": "string (optional)",
  "fields": [ /* field objects */ ],
  "send": {
    "url": "https://your.endpoint (optional)",
    "method": "POST|PUT|PATCH (default POST)",
    "headers": { "Content-Type": "application/json", "...": "..." }
  }
}
```

### Field
```json
{
  "key": "unique_field_key (required)",
  "label": "Label shown to the user (optional; defaults to key)",
  "type": "text|email|number|password|date|textarea|select|radio|checkbox|url|tel|range|color",
  "required": true,
  "placeholder": "hint (optional)",
  "options": ["only for select/radio"],
  "value": "default value (or true/false for checkbox)"
}

```

### sample URL hash for testing of the hash feature:

#f=eyJ0aXRsZSI6IkhBU0ggREVNTyAxMjMiLCJkZXNjcmlwdGlvbiI6IklmIHlvdSBjYW4gcmVhZCB0aGlzLCB0aGUgaGFzaCB3b3JrZWQuIiwiZmllbGRzIjpbeyJrZXkiOiJuYW1lIiwibGFiZWwiOiJZb3VyIE5hbWUiLCJ0eXBlIjoidGV4dCIsInJlcXVpcmVkIjp0cnVlLCJwbGFjZWhvbGRlciI6IkphbmUgRG9lIiwidmFsdWUiOiJKYW5lIERvZSJ9LHsia2V5IjoibGlrZV9pdCIsImxhYmVsIjoiRG8geW91IGxpa2UgaGFzaGVzPyIsInR5cGUiOiJyYWRpbyIsIm9wdGlvbnMiOlsiWWVzIiwiTm8iLCJNYXliZSJdLCJ2YWx1ZSI6IlllcyJ9LHsia2V5Ijoic2hhcmUiLCJsYWJlbCI6IkxldCBvdGhlcnMgZWRpdCIsInR5cGUiOiJjaGVja2JveCIsInZhbHVlIjp0cnVlfV19