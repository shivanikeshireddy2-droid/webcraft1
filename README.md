# WebCraft AI — AI-Powered Website Generator Agent

A production-minded, full-stack AI website builder and interactive IDE that turns natural-language descriptions into complete, responsive website experiences with live preview, interactive editing, targeted regeneration, runnable code export, and instant sharing.

---

## 🌟 Key Features

- **Conversational AI Generation:** Generates domain-specialized website specifications (SaaS, Student Portfolios, Artisan Restaurants, Universities, E-Commerce, Conferences, Agencies) with structured data and rich components.
- **Interactive Live Preview:**
  - Real-time rendering of validated React components.
  - Multi-device viewport toggling: **Desktop (100%)**, **Tablet (768px)**, and **Mobile (375px)** with authentic device bezels.
  - Smooth zoom scaling (50% to 150%) and vertical scrolling.
  - Visual outline highlighting and in-canvas direct section action toolbar (Move Up, Move Down, Delete, Edit).
- **Interactive Visual Editor (Right Panel):**
  - **Section Navigator:** Reorder sections, toggle visibility, delete, duplicate, and add new sections from a library of 15 components.
  - **Property Inspector:** Live text editing (headings, subheadings, badges), button links, image URLs, layout alignments, and card item management.
  - **Theme & Styles:** Preconfigured color palettes (Violet Dark, Emerald Glow, Cyberpunk Blue, Sunset Amber, Rose Luxury, Clean Light), custom hex color pickers, typography font selectors (Inter, Plus Jakarta Sans, Outfit, Playfair Display, Roboto), and corner radii.
  - **SEO & Metadata:** Custom website title, meta description, and keywords.
- **Conversational Refinement & Targeted Regeneration:**
  - AI chat understands follow-up instructions in context (e.g., *"Change theme to emerald green"*, *"Make the hero more punchy"*, *"Add three pricing plans"*, *"Remove testimonials"*).
  - Preserves unaffected sections and stable section IDs.
  - Target individual sections for AI regeneration directly from canvas or chat.
- **Undo & Redo History:**
  - Full revision stack with shortcut keys (`Ctrl+Z`, `Ctrl+Y`).
- **Export & Share Workflows:**
  - **Export ZIP:** Generates a complete, standalone, independently runnable Vite + React + Tailwind CSS project repository containing `package.json`, `index.html`, `vite.config.ts`, `src/App.tsx`, and a setup `README.md`.
  - **Share Snapshot:** Generates a live preview URL encoded snapshot with single-click clipboard copying.
- **Zero-Failure Architecture & Offline Demo Mode:**
  - Includes a built-in **Smart Generation Engine** that operates seamlessly offline without requiring paid API keys.
  - Ready to connect with **Google Gemini** or **OpenAI** via environment variables or the in-app Settings dialog.

---

## 🛠️ Technology Stack

- **Frontend:** React 19, TypeScript, Vite 8, Tailwind CSS v4, Lucide React icons, JSZip, FileSaver.
- **Backend:** Node.js, Express, TypeScript (`tsx`), CORS, Dotenv.
- **Validation & Security:** Zod schema validation, string/URL sanitization, bounded retries, error boundaries.
- **Testing:** Vitest, Testing Library, JSDOM (25 tests passing).
- **Linter:** Oxlint (0 errors, 0 warnings).

---

## 🚀 Getting Started

### Prerequisites

- Node.js v18+ (tested on Node v24.20)
- npm v9+

### Installation

```bash
# Clone or navigate to the repository
cd tricity

# Install dependencies
npm install
```

### Environment Configuration

Create a `.env` file in the project root (optional for basic usage):

```env
PORT=3001
GEMINI_API_KEY=your_gemini_api_key_here
OPENAI_API_KEY=your_openai_api_key_here
```

> **Note:** If API keys are omitted, WebCraft AI runs in **Smart Engine (Demo Mode)**, generating diverse, production-ready website structures offline. You can also paste an API key directly in the in-app **Settings** modal at any time.

### Development Commands

Run both backend and frontend concurrently:

```bash
npm run dev
```

- **Frontend:** [http://localhost:5173](http://localhost:5173)
- **Backend API:** [http://localhost:3001](http://localhost:3001)

Alternative individual commands:
```bash
# Run backend server only
npm run server

# Run frontend client only
npm run client
```

---

## 🧪 Testing and Quality Assurance

Run the comprehensive unit test suite:

```bash
npm run test
```

Test coverage includes:
- Zod schema validation & deep sanitization (preventing XSS / malicious scripts).
- Dynamic generation engine for various domain prompts (restaurant, portfolio, education, etc.).
- Conversational refinement & section preservation.
- Component rendering for all 15 supported section types (Navbar, Hero, Features, Services, Portfolio, Products, Pricing, Testimonials, Stats, Team, Gallery, FAQ, Contact, CTA, Footer).
- Component ErrorBoundary resilience.

Run code linting:

```bash
npm run lint
```

Build for production:

```bash
npm run build
```

---

## 🧩 Reusable Website Component Library

| Section Type | Key Capabilities |
|---|---|
| **Navbar** | Responsive logo, dynamic links, mobile drawer menu, CTA button |
| **Hero** | Split and centered layouts, badge pill, CTA buttons, background glow |
| **Features** | Icon cards with Lucide icon resolution, 2/3/4-column grids |
| **Services** | Service offerings, descriptions, action links |
| **Portfolio** | Project cards with category filters, tech tags, live links |
| **Products** | E-commerce catalog, price tags, ratings, interactive Add-to-Cart |
| **Pricing** | Monthly/annual billing toggle, popular plan highlight, feature checklist |
| **Testimonials**| Customer quotes, star ratings, reviewer avatars and roles |
| **Stats** | Metric counters, key achievements, border separators |
| **Team** | Member avatars, titles, bios, profile links |
| **Gallery** | Image grid with interactive lightbox zoom modal |
| **FAQ** | Interactive accordions with smooth expand/collapse |
| **Contact** | Interactive working form with validation and submit confirmation toast |
| **CTA** | High-conversion gradient banner with action buttons |
| **Footer** | Multi-column footer links, social icons, copyright notice |

---

## 📦 Exported Website Structure

When clicking **Export ZIP**, the generated archive contains an independently runnable project:

```text
├── package.json        # Dependencies (React, Vite, Tailwind, Lucide)
├── vite.config.ts      # Vite configuration with Tailwind CSS v4
├── tsconfig.json       # TypeScript configuration
├── index.html          # HTML entry with Google Fonts
├── website-spec.json   # Exported website specification data
├── README.md           # Instructions to install and run locally
└── src/
    ├── main.tsx        # React entry point
    ├── index.css       # Tailwind stylesheet
    └── App.tsx         # Standalone website application rendering all sections
```

To run the exported site:
```bash
unzip my-website.zip
cd my-website
npm install
npm run dev
```

---

## 🔒 Security & Safe Execution

- **Zero Arbitrary Code Execution:** The preview does not execute model-generated JavaScript or raw HTML strings. It strictly renders approved, typed React components mapped to a validated JSON schema.
- **Deep Sanitization:** All text strings and links undergo automatic sanitization stripping `<script>` tags, event handlers (`onload`, `onerror`), and `javascript:` URIs.
- **Client Key Isolation:** AI credentials entered in settings are stored locally in the browser and never leaked into exported ZIP files.
