# Parrobyte bgremove - AI Background Remover Pro

A free, privacy-focused, browser-based AI background removal tool. Remove backgrounds from images instantly using AI — no uploads, no signups, no watermarks, 100% client-side processing.

**Live at:** `https://bgremove.parrobyte.co.in`

---

## Features

| Feature | Description |
|---|---|
| **AI Background Removal** | Uses Transformers.js with MODNet model, runs entirely in your browser |
| **100% Free** | No limits, no watermarks, no signup required |
| **100% Private** | Images never leave your device. All processing happens locally |
| **Drag & Drop** | Drop images anywhere to upload |
| **Clipboard Paste** | Paste images directly (Ctrl+V) |
| **Camera Capture** | Use your device camera to take photos |
| **Batch Processing** | Upload and process multiple images at once |
| **Multiple Formats** | Supports JPG, PNG, WEBP, BMP, TIFF, AVIF, HEIC |
| **Transparent PNG Output** | High-quality transparent PNG output preserving original dimensions |
| **Before/After Slider** | Compare original and result side-by-side |
| **Edge Refinement** | Smooth or sharpen edges after processing |
| **Feather Control** | Soften edges for natural-looking cutouts |
| **Threshold Adjustment** | Fine-tune mask sensitivity |
| **Auto Crop** | Automatically crop transparent borders |
| **Background Replace** | Replace background with blur, solid color, gradient, or custom image |
| **Batch Download** | Download all results as individual files or ZIP package |

---

## Tech Stack

| Technology | Purpose |
|---|---|
| [Transformers.js](https://huggingface.co/docs/transformers.js) | Browser-based AI/ML inference |
| [MODNet](https://github.com/ZHKKKe/MODNet) | AI model for human matting/background removal |
| [Tailwind CSS](https://tailwindcss.com) | Utility-first CSS framework |
| [DaisyUI](https://daisyui.com) | Tailwind CSS component library |
| [Font Awesome](https://fontawesome.com) | Icons |
| [JSZip](https://stuk.github.io/jszip) | ZIP file generation for batch downloads |
| Vanilla JavaScript (ES6+) | All application logic |

---

## Quick Start

### Option 1: Open Directly (Simplest)

Double-click `index.html` to open in your browser.

> **Note:** Due to browser security restrictions (CORS), the AI model download from HuggingFace may fail when opening directly via `file://`. For best results, use a local server (Option 2).

### Option 2: Local Server (Recommended)

```bash
# Using npx (no installation required)
npx serve .

# Using Python 3
python3 -m http.server 8080

# Using Node.js http-server
npx http-server -p 8080

# Using PHP
php -S localhost:8080
```

Then open `http://localhost:8080` in your browser.

### Option 3: Deploy to Static Hosting

Deploy `index.html` to any static hosting service:
- [Vercel](https://vercel.com)
- [Netlify](https://netlify.com)
- [Cloudflare Pages](https://pages.cloudflare.com)
- [GitHub Pages](https://pages.github.com)
- [Surge.sh](https://surge.sh)

---

## How It Works

```
1. Upload Image(s)
   -> Browser reads file locally (no upload to server)

2. AI Processing (client-side)
   -> Transformers.js loads MODNet model from HuggingFace (cached after first use)
   -> Model runs inference: analyzes pixels, detects foreground/background
   -> Generates grayscale alpha mask

3. Post-Processing
   -> Mask is resized to original image dimensions
   -> Edge refinement, feathering, threshold applied
   -> Alpha channel composited onto original image

4. Output
   -> Transparent PNG ready for download
```

### Processing Steps

The app shows a clear 5-step progress indicator during processing:

1. **Load AI Model** - Downloads model on first use (~40MB), cached locally
2. **Read Image** - Loads image into memory
3. **AI Analyzing Pixels** - Neural network processes the image
4. **Generate Mask** - Creates foreground/background separation mask
5. **Apply & Finalize** - Composites mask with original, applies edge adjustments

---

## Architecture

Single-file architecture — everything is contained in `index.html`:

```
index.html
├── <head>          SEO meta tags, CDN imports, Tailwind config
├── <body>
│   ├── Navbar      Logo, navigation, theme toggle, settings
│   ├── Hero        Landing section with CTA
│   ├── Upload      Drag/drop zone, paste, camera, file browser
│   ├── Processing  3-step stepper + detailed progress panel
│   ├── Preview     Before/after slider, zoom, pan, fullscreen
│   ├── Features    Feature cards with SEO-optimized content
│   ├── Settings    DaisyUI drawer with preferences
│   ├── Footer      Links, branding, privacy note
│   └── Mobile Bar  Bottom action bar for mobile
└── <script>        All JavaScript in ES6 module
    ├── Transformers.js Import (AutoModel, AutoProcessor, RawImage)
    ├── Configuration    Model ID, formats, limits
    ├── State Management Global state object
    ├── DOM Cache        All DOM element references
    ├── Utilities        Helper functions (resize, format, etc.)
    ├── Particle System  Animated background particles
    ├── Confetti         Success celebration effect
    ├── Theme Manager    Light/dark mode
    ├── Upload Module    Drag/drop, paste, camera, metadata
    ├── AI Module        Model loading, inference, mask extraction
    ├── Processing       Post-processing, edge refinement, feathering
    ├── Preview Module   Comparison slider, zoom, pan, views
    ├── Download Module  PNG, WebP, ZIP export
    ├── Settings Module  Preferences panel
    ├── Navigation       Scroll, anchors, keyboard shortcuts
    ├── Welcome Modal    First-time user onboarding
    ├── Sample Image     Canvas-drawn demo parrot image
    └── Keyboard         Ctrl+U, Ctrl+S, Ctrl+V, Esc shortcuts
```

---

## SEO Optimization

The app is optimized for the keyword **"bgremove"** and targets `bgremove.parrobyte.co.in`:

- **46+ mentions** of "bgremove" throughout content
- **JSON-LD structured data**: SoftwareApplication, WebSite, WebPage, FAQPage schemas
- **Open Graph** and **Twitter Card** meta tags
- **Canonical URL** pointing to `https://bgremove.parrobyte.co.in/`
- **DNS prefetch** and **preconnect** for CDN resources
- Proper heading hierarchy (H1 > H2 > H3)
- Semantic HTML with ARIA labels
- 45 "bgremove
## SEO Optimization

The app is optimized for the keyword **"bgremove"** and targets `bgremove.parrobyte.co.in`:

- **46+ mentions** of "bgremove" throughout content
- **JSON-LD structured data**: SoftwareApplication, WebSite, WebPage, FAQPage schemas
- **Open Graph** and **Twitter Card** meta tags
- **Canonical URL** pointing to `https://bgremove.parrobyte.co.in/`
- **DNS prefetch** and **preconnect** for CDN resources
- Proper heading hierarchy (H1 > H2 > H3)
- Semantic HTML with ARIA labels

---

## File Structure

```
/mnt/agents/output/
├── index.html          # Single-file application (~170KB)
├── README.md           # This file
└── .git/               # Git repository
```

No build tools. No dependencies to install. No `package.json`. Just open `index.html` in a browser.

---

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl + U` | Upload files |
| `Ctrl + V` | Paste image from clipboard |
| `Ctrl + S` | Download processed image |
| `Ctrl + Z` | Reset/restore original |
| `Esc` | Close settings drawer / exit fullscreen |

---

## Browser Compatibility

| Browser | Status |
|---|---|
| Chrome 90+ | Fully supported |
| Edge 90+ | Fully supported |
| Firefox 90+ | Fully supported |
| Safari 15+ | Supported (may be slower) |
| Mobile Chrome | Fully supported |
| Mobile Safari | Supported |

**Requirements:**
- WebGL support (for GPU-accelerated AI inference)
- ES6 module support
- Modern JavaScript features (async/await, optional chaining)

---

## AI Model Details

| Property | Value |
|---|---|
| **Model** | `Xenova/modnet` (MODNet via Transformers.js) |
| **Type** | Portrait Matting / Salient Object Detection |
| **Size** | ~40MB download (quantized), cached locally |
| **Input** | Any resolution (resized internally to model input size) |
| **Output** | Grayscale alpha mask, bilinear-resized to original dimensions |
| **Quantization** | Enabled by default (faster download, slight quality trade-off) |
| **Backend** | ONNX Runtime Web (WebGL / WebGPU / WASM) |

**Note on Model Choice:**
- `Xenova/rmbg-1.4` - Requires HuggingFace authentication (blocked for public use)
- `Xenova/modnet` - **Currently used**. Publicly accessible, optimized for human portraits
- `Xenova/u2net` - Alternative salient object detection model

MODNet is optimized for **human portraits** and works best with:
- Single person in frame
- Clear foreground/background separation
- Good lighting and contrast

It may struggle with:
- Complex scenes with multiple subjects
- Transparent or reflective objects
- Backgrounds similar in color to foreground
- Fine details like individual hair strands (use edge refinement tools)

---

## Configuration

Edit the `CONFIG` object in the JavaScript section of `index.html`:

```javascript
const CONFIG = {
  MODEL_ID: 'Xenova/modnet',           // AI model to use
  MAX_IMAGE_SIZE: 2048,                 // Max image dimension (pixels)
  SUPPORTED_MIMETYPES: ['image/jpeg', 'image/png', 'image/webp', ...],
  SUPPORTED_EXTENSIONS: ['.jpg', '.jpeg', '.png', '.webp', ...],
  CHUNK_SIZE: 1024 * 1024,              // Processing chunk size
};
```

---

## Known Limitations

1. **file:// Protocol**: Opening the HTML file directly (`file://`) may cause CORS issues when downloading the AI model from HuggingFace. Use a local HTTP server instead.

2. **First-Load Model Download**: The AI model (~40MB) must download on first use. This is a one-time cost - subsequent uses load from browser cache instantly.

3. **Large Images**: Very high-resolution images (>2048px) are automatically resized for performance. Original dimensions are preserved in output.

4. **Device Performance**: Processing speed depends on device GPU/CPU. Mobile devices may take 10-30 seconds per image. Desktop GPUs typically process in 2-5 seconds.

5. **Browser Memory**: Processing multiple large images simultaneously may cause memory issues on low-RAM devices.

---

## Privacy & Security

- **Zero server communication** - The app runs entirely client-side
- **No image uploads** - Images are processed in-browser using Canvas API
- **No tracking or analytics** - No Google Analytics, no cookies, no telemetry
- **No external API calls** after page load (only model download from HuggingFace CDN)
- **No localStorage** used for images (only for settings preferences)

---

## Performance Tips

1. **Use Chrome or Edge** - Best WebGL performance for AI inference
2. **Enable GPU acceleration** in browser settings
3. **Close other tabs** - Free up RAM for image processing
4. **Use smaller images** - Resize before upload for faster processing
5. **Enable "Fast" mode** in settings for quicker (lower quality) results

---

## Troubleshooting

### "401 Unauthorized" or "CORS blocked" error
**Cause:** Opening file directly via `file://` protocol
**Fix:** Use a local server:
```bash
npx serve .
# Then open http://localhost:3000
```

### Model download is very slow
**Cause:** Large model file (~40MB)
**Fix:** Wait for it to complete. The model is cached locally after first download.

### Processing is very slow
**Cause:** Device GPU/CPU limitations
**Fix:** Try "Fast" mode in settings, or use a device with better GPU.

### Images don't appear after upload
**Cause:** Browser security restrictions
**Fix:** Check browser console for errors. Ensure JavaScript is enabled.

### "Out of memory" error
**Cause:** Too many large images
**Fix:** Process images one at a time, or resize images before uploading.

---

## Development

Since this is a single-file application, development is straightforward:

1. Open `index.html` in your preferred code editor
2. Make changes
3. Refresh browser to see changes (use a local server for full functionality)

### Code Organization

The JavaScript is organized into modules within the single `<script type="module">` tag:

| Module | Purpose |
|---|---|
| `CONFIG` | Constants and configuration |
| `state` | Global application state |
| `DOM` | Cached DOM element references |
| `Utils` | Helper functions |
| `Toast` | Toast notification system |
| `ParticleSystem` | Animated background particles |
| `ConfettiSystem` | Success celebration animation |
| `Theme` | Light/dark theme management |
| `Upload` | File upload handling |
| `AI` | Transformers.js model loading and inference |
| `Processing` | Post-processing and edge refinement |
| `Preview` | Image preview and comparison tools |
| `Settings` | Settings panel and preferences |
| `Navigation` | Scroll behavior and navigation |
| `WelcomeModal` | First-time user modal |
| `SampleImage` | Demo parrot image generation |
| `Keyboard` | Keyboard shortcut handling |

---

## Contributing

Contributions are welcome! Since this is a single-file project:

1. Fork the repository
2. Make your changes to `index.html`
3. Test thoroughly across different browsers
4. Submit a pull request with a clear description of changes

### Areas for Improvement

- [ ] Better model (currently using MODNet, could upgrade to RMBG-2-Studio)
- [ ] WebGPU backend support for faster inference
- [ ] Progressive Web App (PWA) with offline support
- [ ] Multi-language support (i18n)
- [ ] Better hair/fur detail preservation
- [ ] Real-time preview during edge adjustments
- [ ] Undo/redo for editing operations
- [ ] Image size/compression before processing

---

## License

MIT License - feel free to use, modify, and distribute.

**Attribution:**
- AI Model: [MODNet](https://github.com/ZHKKKe/MODNet) by ZHKKKe
- Transformers.js by [Hugging Face](https://huggingface.co/docs/transformers.js)
- UI Framework: [Tailwind CSS](https://tailwindcss.com) + [DaisyUI](https://daisyui.com)
- Icons: [Font Awesome](https://fontawesome.com)

---

## Connect

- **Website:** [parrobyte.co.in](https://parrobyte.co.in)
- **App:** [bgremove.parrobyte.co.in](https://bgremove.parrobyte.co.in)

---

## Changelog

### v2.0 (Current)
- Rebranded to "Parrobyte bgremove"
- Added 3-step stepper progress indicator (Upload > AI Processing > Complete)
- Added 5-step detailed progress list with live status updates
- Added timer showing elapsed processing time
- Added numbered progress bar with animated shimmer effect
- Added upload feedback: loading spinner, success flash, compact state, banner
- Added staggered pop-in animation for image grid
- Added per-image status badges (PENDING / DONE)
- Added "Add More" button in compact upload state
- Improved error handling for file:// protocol CORS issues
- Added protocol detection with user-friendly warnings
- SEO optimization: 46+ "bgremove" mentions, JSON-LD schemas, meta tags
- Added keyboard shortcuts (Ctrl+U, Ctrl+V, Ctrl+S, Ctrl+Z)
- Added parrot clay-style sample image (Canvas-drawn)
- Mobile bottom action bar
- Theme toggle (light/dark)
- Settings drawer with preferences

### v1.0
- Initial release with basic background removal
- Drag & drop upload
- Before/after comparison slider
- Edge refinement, feather, threshold controls
- Background replacement options
- PNG/WebP/ZIP download
