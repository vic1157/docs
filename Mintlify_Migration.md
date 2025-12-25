# RYB Documentation Migration Plan
## Migrate CLAUDE.md to Mintlify Documentation Site

---

## Overview

**Goal:** Transform the 735-line CLAUDE.md file into a comprehensive, well-organized Mintlify documentation site that serves both technical (developers) and non-technical (product/stakeholders) audiences.

**Current State:**
- Documentation repo at `/Users/vicraw/projects/docs/` with Mintlify sample content
- Source code at `/Users/vicraw/projects/guided-grow-app/` (React/TypeScript app)
- CLAUDE.md contains: project overview, tech stack, 7 major features, architecture, data structures, design patterns

**Constraints:**
- Keep existing Mintlify sample content as reference
- Mixed audience (developers + product/stakeholders)
- Moderate reorganization - improve UX with better navigation, diagrams, and Mintlify components

---

## Recommended Documentation Structure

### 4-Tab Navigation System

**Tab 1: Product** - For stakeholders, product team, and new developers
**Tab 2: Features** - Detailed feature documentation with screenshots and user flows
**Tab 3: Developer Guide** - Technical implementation details, patterns, and code examples
**Tab 4: Mintlify Reference** - Keep existing sample content for team reference

### Page Breakdown (31 New Pages)

#### Tab 1: Product (7 pages)
**Introduction:**
- `product/index.mdx` - Project overview, vision, and quick navigation
- `product/tech-stack.mdx` - Technology choices with rationale
- `product/roadmap.mdx` - Completed work + future enhancements
- `product/core-concepts.mdx` - Scrolls, Leo AI, and Denarii explained

**Getting Started:**
- `product/quickstart.mdx` - Local development setup
- `product/project-structure.mdx` - Folder organization
- `product/data-model.mdx` - Key TypeScript interfaces

#### Tab 2: Features (12 pages)
**User Journey:**
- `features/onboarding-overview.mdx` - Complete onboarding system
- `features/survey-system.mdx` - Spiritual assessment + personas
- `features/profile-setup.mdx` - Profile & reading goals onboarding
- `features/scroll-walkthrough.mdx` - 8-step tour + demo scroll

**Core Features:**
- `features/bible-reader.mdx` - Reading engine, translations, Activity Panel
- `features/our-daily-bread.mdx` - Daily journey (verse → scroll → quiz)
- `features/scripture-explorer.mdx` - Hub for scrolls, chats, quizzes
- `features/leo-ai.mdx` - AI chat interface

**Engagement:**
- `features/quiz-system.mdx` - Quiz creation, taking, results
- `features/scrolls.mdx` - Scroll concept and lifecycle
- `features/community.mdx` - Community preview
- `features/monetization.mdx` - Paywall and Denarii system

#### Tab 3: Developer Guide (12 pages)
**Architecture:**
- `dev/state-management.mdx` - localStorage patterns, custom events
- `dev/routing.mdx` - React Router setup, URL parameters
- `dev/styling.mdx` - Tailwind, shadcn/ui, theming
- `dev/animations.mdx` - Framer Motion patterns

**Implementation Patterns:**
- `dev/onboarding-pattern.mdx` - Reusable onboarding flow pattern
- `dev/mobile-optimization.mdx` - Viewport handling, keyboard management
- `dev/theme-system.mdx` - Light/dark mode implementation
- `dev/component-library.mdx` - Custom components catalog

**Code Examples:**
- `dev/examples/onboarding-progress.mdx` - Component walkthrough
- `dev/examples/activity-panel.mdx` - Drag gestures implementation
- `dev/examples/daily-bread.mdx` - Sequential unlock pattern

**Data & APIs:**
- `dev/data-persistence.mdx` - localStorage keys and patterns
- `dev/mock-data.mdx` - Current mock data structures
- `dev/future-backend.mdx` - Backend requirements

---

## Step-by-Step Implementation

### Phase 1: Setup & Structure (Day 1)

**1.1 Create Directory Structure**
```bash
mkdir -p product features dev/examples images
```

**1.2 Update `/Users/vicraw/projects/docs/docs.json`**
- Replace 2-tab navigation with 4-tab structure
- Update branding (name stays "RYB", adjust colors/links as needed)
- Add custom anchors (GitHub, Live App)
- Update navbar primary button to "Live App"
- Keep contextual options for code copying

**New navigation structure:**
```json
{
  "tabs": [
    {
      "tab": "Product",
      "groups": [
        { "group": "Introduction", "pages": [...] },
        { "group": "Getting Started", "pages": [...] }
      ]
    },
    {
      "tab": "Features",
      "groups": [
        { "group": "User Journey", "pages": [...] },
        { "group": "Core Features", "pages": [...] },
        { "group": "Engagement", "pages": [...] }
      ]
    },
    {
      "tab": "Developer Guide",
      "groups": [
        { "group": "Architecture", "pages": [...] },
        { "group": "Implementation Patterns", "pages": [...] },
        { "group": "Code Examples", "pages": [...] },
        { "group": "Data & APIs", "pages": [...] }
      ]
    },
    {
      "tab": "Mintlify Reference",
      "groups": [
        // Keep existing sample content
      ]
    }
  ]
}
```

**1.3 Create Placeholder MDX Files**
- Create all 31 MDX files with frontmatter (title, description, icon)
- Test navigation structure locally (`mintlify dev`)

### Phase 2: Product Tab Migration (Days 2-3)

**Priority Pages:**

**`product/index.mdx`** (Lines 1-5 from CLAUDE.md)
- Project description and overview
- CardGroup with quick links to key sections
- Status indicator (Prototype/Beta/Production)

**`product/core-concepts.mdx`** (Lines 626-648 from CLAUDE.md)
- Scrolls definition and lifecycle (with Steps component)
- Leo AI capabilities (with CardGroup)
- Denarii explanation and pricing (with table)
- Use Accordions for detailed definitions

**`product/tech-stack.mdx`** (Lines 7-16 from CLAUDE.md)
- Convert bullet list to CardGroup with icons
- Add "Why we chose X" explanations
- Link to dev architecture pages

**`product/roadmap.mdx`** (Lines 505-625 from CLAUDE.md)
- AccordionGroup for completed work (checkmarks)
- Warning components for known limitations
- Link to specific feature pages

**`product/project-structure.mdx`** (Lines 413-457 from CLAUDE.md)
- Interactive folder tree
- Descriptions for each major directory
- Links to component documentation

**`product/quickstart.mdx`**
- Step-by-step local setup
- Installation commands
- Troubleshooting section

**`product/data-model.mdx`** (Lines 219-265, 370-393, 485-503 from CLAUDE.md)
- Extract all TypeScript interfaces
- Use ResponseField components for properties
- Organize by domain (Scrolls, Quizzes, Chats, Bible content)

### Phase 3: Features Tab Migration (Days 4-6)

**User Journey Group:**

**`features/onboarding-overview.mdx`** (Lines 20-98 from CLAUDE.md)
- Summary of all onboarding flows
- Flowchart showing progression
- Links to detailed pages

**`features/survey-system.mdx`** (Lines 22-43)
- 10 questions breakdown
- 5 persona types with descriptions
- Note about calculation logic (not implemented)

**`features/profile-setup.mdx`** (Lines 45-57)
- Profile and reading goals flows
- Screenshots of onboarding modals
- localStorage persistence details

**`features/scroll-walkthrough.mdx`** (Lines 59-98)
- 8-step tour breakdown
- Interactive demo elements
- Link to demo scroll

**Core Features Group:**

**`features/bible-reader.mdx`** (Lines 100-133)
- Translation switcher, font controls, chapter navigation
- Activity Panel modes (inactive vs active)
- Extract code from `/Users/vicraw/projects/guided-grow-app/src/components/ActivityPanel.tsx`
- Sample chapters list

**`features/our-daily-bread.mdx`** (Lines 267-393)
- Sequential flow with Steps component
- Journey markers explained
- Daily reset logic
- Extract component code from `/Users/vicraw/projects/guided-grow-app/src/components/OurDailyBread.tsx`
- Screenshots of each state

**`features/scripture-explorer.mdx`** (Lines 161-217)
- Hub overview with navigation flow diagram
- 4 action buttons explained
- Tabbed view (Scrolls/Chats)
- Links to scrolls, chats, quizzes pages

**`features/leo-ai.mdx`** (Lines 171-179, 637-648)
- Chat interface walkthrough
- Mock response behavior
- Future capabilities
- Denarii requirement note

**Engagement Group:**

**`features/quiz-system.mdx`** (Lines 181-202)
- Quiz creation, taking, results flow
- Extract code from `/Users/vicraw/projects/guided-grow-app/src/pages/NewQuiz.tsx`
- Question component breakdown
- Results with color-coded feedback

**`features/scrolls.mdx`** (Lines 192-217, 626-636)
- Lifecycle diagram
- Detail view components
- Integration with quizzes
- Data structure with TypeScript interface

**`features/community.mdx`** (Lines 149-160)
- Preview implementation
- Coming Soon overlay
- Planned features list

**`features/monetization.mdx`** (Lines 134-148)
- Denarii explanation
- Pricing tiers (Monthly $5.99, Annual $49.99)
- Free vs Premium feature matrix
- "Free forever" messaging

### Phase 4: Developer Guide Migration (Days 7-9)

**Architecture Group:**

**`dev/state-management.mdx`** (Lines 459-478)
- localStorage patterns with code examples
- Custom event system
- Cross-component communication
- Event listener patterns

**`dev/routing.mdx`** (Lines 479-483)
- React Router setup
- URL parameter patterns (`?onboarding=true`)
- 31 routes documented

**`dev/styling.mdx`** (Lines 667-672)
- Tailwind configuration
- Shadcn/ui integration
- CSS variable system
- Semantic color tokens

**`dev/animations.mdx`** (Lines 673-682)
- Framer Motion patterns
- Drag gesture implementation (ActivityPanel)
- Spring animations
- Extract from `/Users/vicraw/projects/guided-grow-app/src/components/ActivityPanel.tsx`

**Implementation Patterns Group:**

**`dev/onboarding-pattern.mdx`** (Lines 649-659)
- Complete pattern breakdown with Steps component
- localStorage persistence
- Event dispatching
- Code examples from Profile.tsx, OnboardingProgress.tsx

**`dev/mobile-optimization.mdx`** (Lines 543-554, 692-699)
- Viewport meta tag settings
- Keyboard handling (Chat.tsx fixed layout)
- Safe area insets
- 16px input font size (iOS zoom prevention)

**`dev/theme-system.mdx`** (Lines 537-541, 683-691)
- ThemeProvider implementation
- useTheme hook
- CSS variable structure
- Extract from `/Users/vicraw/projects/guided-grow-app/src/hooks/use-theme.tsx`

**`dev/component-library.mdx`**
- Custom components catalog (8 components)
- Shadcn/ui components list (46 components)
- Usage examples and props

**Code Examples Group:**

**`dev/examples/onboarding-progress.mdx`**
- Full component walkthrough from `/Users/vicraw/projects/guided-grow-app/src/components/OnboardingProgress.tsx`
- Line-by-line explanation with annotations
- Event listener pattern

**`dev/examples/activity-panel.mdx`**
- Drag gesture breakdown from `/Users/vicraw/projects/guided-grow-app/src/components/ActivityPanel.tsx`
- State management (active/inactive modes)
- Panel positioning and z-index

**`dev/examples/daily-bread.mdx`**
- Sequential unlock pattern from `/Users/vicraw/projects/guided-grow-app/src/components/OurDailyBread.tsx`
- Daily reset logic
- State persistence with localStorage

**Data & APIs Group:**

**`dev/data-persistence.mdx`** (Lines 461-471)
- All localStorage keys documented
- Daily reset logic (date-based)
- Completion state patterns

**`dev/mock-data.mdx`**
- Current mock data structures
- Sample scrolls, chats, quizzes
- Where mock data lives in codebase

**`dev/future-backend.mdx`** (Lines 706-723)
- Planned API endpoints
- Authentication requirements
- Backend integration notes
- Bible API options

### Phase 5: Polish & Enhancement (Days 10-11)

**5.1 Add Visuals**
- Create flow diagrams (Mermaid or images)
- Screenshot key UI states from app
- Add animated GIFs for interactions (optional)
- Store in `/Users/vicraw/projects/docs/images/`

**5.2 Cross-linking**
- Add "Related Pages" CardGroup to each page bottom
- Ensure all internal links work
- Add breadcrumb context

**5.3 Code Refinement**
- Ensure all code snippets have proper syntax highlighting
- Add file names to code blocks
- Use CodeGroup for multiple related examples
- Include imports and type definitions

**5.4 Mintlify Components Usage**
- **Cards**: Feature overviews, navigation
- **Steps**: Sequential processes (onboarding, daily bread)
- **Accordions**: Detailed specs, collapsible content
- **Note/Tip/Warning**: Status indicators, best practices
- **CodeGroup**: Multiple code examples
- **ResponseField**: Interface properties
- **Tabs**: Alternative approaches

**5.5 Review & Test**
- Preview entire site locally (`mintlify dev`)
- Test all navigation paths
- Verify search functionality
- Check mobile responsiveness
- Validate all links

### Phase 6: Deployment (Day 12)

**6.1 Commit Changes**
```bash
git add .
git commit -m "Migrate CLAUDE.md to Mintlify documentation site

- Add 4-tab navigation (Product, Features, Developer Guide, Mintlify Reference)
- Create 31 new documentation pages
- Extract code examples from source code
- Add diagrams and screenshots
- Preserve existing Mintlify sample content"
```

**6.2 Deploy**
- Push to main branch
- Verify auto-deployment via Mintlify

**6.3 Iterate**
- Gather team feedback
- Add missing details
- Refine based on usage

---

## Critical Files

### Files to Modify
- `/Users/vicraw/projects/docs/docs.json` - Update navigation structure

### Files to Create (31 new MDX files)
**Product Tab (7):**
- `/Users/vicraw/projects/docs/product/index.mdx`
- `/Users/vicraw/projects/docs/product/tech-stack.mdx`
- `/Users/vicraw/projects/docs/product/roadmap.mdx`
- `/Users/vicraw/projects/docs/product/core-concepts.mdx`
- `/Users/vicraw/projects/docs/product/quickstart.mdx`
- `/Users/vicraw/projects/docs/product/project-structure.mdx`
- `/Users/vicraw/projects/docs/product/data-model.mdx`

**Features Tab (12):**
- `/Users/vicraw/projects/docs/features/onboarding-overview.mdx`
- `/Users/vicraw/projects/docs/features/survey-system.mdx`
- `/Users/vicraw/projects/docs/features/profile-setup.mdx`
- `/Users/vicraw/projects/docs/features/scroll-walkthrough.mdx`
- `/Users/vicraw/projects/docs/features/bible-reader.mdx`
- `/Users/vicraw/projects/docs/features/our-daily-bread.mdx`
- `/Users/vicraw/projects/docs/features/scripture-explorer.mdx`
- `/Users/vicraw/projects/docs/features/leo-ai.mdx`
- `/Users/vicraw/projects/docs/features/quiz-system.mdx`
- `/Users/vicraw/projects/docs/features/scrolls.mdx`
- `/Users/vicraw/projects/docs/features/community.mdx`
- `/Users/vicraw/projects/docs/features/monetization.mdx`

**Developer Guide Tab (12):**
- `/Users/vicraw/projects/docs/dev/state-management.mdx`
- `/Users/vicraw/projects/docs/dev/routing.mdx`
- `/Users/vicraw/projects/docs/dev/styling.mdx`
- `/Users/vicraw/projects/docs/dev/animations.mdx`
- `/Users/vicraw/projects/docs/dev/onboarding-pattern.mdx`
- `/Users/vicraw/projects/docs/dev/mobile-optimization.mdx`
- `/Users/vicraw/projects/docs/dev/theme-system.mdx`
- `/Users/vicraw/projects/docs/dev/component-library.mdx`
- `/Users/vicraw/projects/docs/dev/examples/onboarding-progress.mdx`
- `/Users/vicraw/projects/docs/dev/examples/activity-panel.mdx`
- `/Users/vicraw/projects/docs/dev/examples/daily-bread.mdx`
- `/Users/vicraw/projects/docs/dev/data-persistence.mdx`
- `/Users/vicraw/projects/docs/dev/mock-data.mdx`
- `/Users/vicraw/projects/docs/dev/future-backend.mdx`

### Source Files to Extract From
- `/Users/vicraw/projects/docs/CLAUDE.md` - Primary content source
- `/Users/vicraw/projects/guided-grow-app/src/components/OurDailyBread.tsx` - Daily Bread component
- `/Users/vicraw/projects/guided-grow-app/src/components/ActivityPanel.tsx` - Drag gestures
- `/Users/vicraw/projects/guided-grow-app/src/components/OnboardingProgress.tsx` - Onboarding pattern
- `/Users/vicraw/projects/guided-grow-app/src/hooks/use-theme.tsx` - Theme system
- `/Users/vicraw/projects/guided-grow-app/src/pages/NewQuiz.tsx` - Quiz system
- `/Users/vicraw/projects/guided-grow-app/src/pages/Chat.tsx` - Leo AI chat

---

## Key Principles

1. **Audience Segmentation**: Product tab for non-technical, Developer Guide for technical
2. **Progressive Disclosure**: Use Accordions to hide complexity
3. **Scannability**: CardGroups, Steps, and clear headings
4. **Code Examples**: Extract from real source code, include imports
5. **Status Indicators**: Note/Warning components for implementation status
6. **Cross-linking**: Related Pages sections at bottom of each page
7. **Search Optimization**: Descriptive titles, rich descriptions, keywords in frontmatter

---

## Estimated Timeline

- **Days 1-3**: Setup + Product tab (7 pages)
- **Days 4-6**: Features tab (12 pages)
- **Days 7-9**: Developer Guide tab (12 pages)
- **Days 10-11**: Polish, visuals, cross-linking
- **Day 12**: Deploy and iterate

**Total**: ~12 days for comprehensive migration with polish
