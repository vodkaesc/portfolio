# Portfolio Customization Guide

This is a **forked codebase** from Takuya Matsuyama's portfolio. This guide explains how to customize every aspect of the portfolio to make it your own.

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Technologies & Stack](#technologies--stack)
3. [Folder Structure](#folder-structure)
4. [Customization Guide](#customization-guide)
   - [Personal Information](#1-personal-information)
   - [Images & Media](#2-images--media)
   - [Social Links](#3-social-links)
   - [Work/Projects](#4-workprojects-section)
   - [Wallpapers](#5-wallpapers-section)
   - [Posts/Content](#6-postscontent-links)
   - [Colors & Theme](#7-colors--theme)
   - [Navigation](#8-navigation)
   - [Meta Tags & SEO](#9-meta-tags--seo)
5. [Adding New Pages](#adding-new-pages)
6. [Running & Deploying](#running--deploying)

---

## Project Overview

This is a **Next.js portfolio website** built with:
- **Framework:** Next.js 13
- **UI Library:** Chakra UI
- **Styling:** Emotion (CSS-in-JS)
- **Animations:** Framer Motion
- **3D Graphics:** Three.js (for the voxel dog animation)
- **Deployment:** Vercel ready

The portfolio includes:
- Homepage with bio and introduction
- Works/Projects showcase
- Wallpapers gallery
- Links to popular posts
- Dark/Light theme toggle
- Responsive design
- 3D animated dog character

---

## Technologies & Stack

```json
{
  "frontend": "Next.js 13, React 18",
  "ui_framework": "Chakra UI v2.8",
  "styling": "Emotion, styled-components",
  "animations": "Framer Motion",
  "3d_graphics": "Three.js",
  "icons": "React Icons, Chakra Icons",
  "analytics": "Vercel Analytics",
  "deployment": "Vercel"
}
```

---

## Folder Structure

```
portfolio/
├── components/              # Reusable React components
│   ├── layouts/            # Page layout wrappers
│   │   ├── main.js         # Main layout with navbar/footer
│   │   └── article.js      # Article/work page layout
│   ├── bio.js              # Bio section styles
│   ├── navbar.js           # Navigation bar
│   ├── footer.js           # Footer
│   ├── logo.js             # Logo component
│   ├── grid-item.js        # Grid item components
│   ├── icons/              # Custom icons
│   └── ...other components
│
├── pages/                   # Next.js pages (become routes)
│   ├── _app.js             # App wrapper
│   ├── _document.js        # HTML document template
│   ├── index.js            # Homepage
│   ├── works.js            # Works overview
│   ├── works/              # Individual work pages
│   │   ├── inkdrop.js
│   │   ├── walknote.js
│   │   ├── fourpainters.js
│   │   └── ...more works
│   ├── wallpapers/         # Wallpaper pages
│   │   ├── index.js
│   │   ├── machiya.js
│   │   └── cherry-blossoms.js
│   └── posts.js            # Posts/content links
│
├── public/                  # Static files (images, favicon)
│   └── images/
│       ├── takuya.jpg      # Profile picture
│       ├── works/          # Work thumbnail images
│       ├── wallpapers/     # Wallpaper gallery images
│       ├── contents/       # Post thumbnail images
│       └── links/          # Social link icons
│
├── lib/
│   ├── theme.js            # Chakra UI theme configuration
│   └── model.js            # 3D model related code
│
├── package.json            # Dependencies
├── next.config.js          # Next.js configuration
├── prettier.config.js      # Code formatting rules
└── vercel.json             # Vercel deployment config
```

---

## Customization Guide

### 1. **Personal Information**

#### Main Name & Title
**File:** [pages/index.js](pages/index.js)

```javascript
// Line 36-37: Change your name and title
<Heading as="h2" variant="page-title">
  Takuya Matsuyama  // ← CHANGE THIS
</Heading>
<p>Digital Craftsman ( Artist / Developer / Designer )</p> // ← CHANGE THIS
```

#### Bio Section
**File:** [pages/index.js](pages/index.js#L48-L70)

```javascript
// Lines 48-70: Replace the entire Paragraph with your bio
<Paragraph>
  Takuya is a freelance and a full-stack developer based in Osaka...
  // ← CHANGE THIS ENTIRE SECTION
</Paragraph>
```

#### Logo/Brand Name
**File:** [components/logo.js](components/logo.js)

```javascript
// Line 28: Change the brand name in the logo
<Text color={useColorModeValue('gray.800', 'whiteAlpha.900')} >
  Takuya Matsuyama  // ← CHANGE THIS
</Text>
```

#### Footer Copyright
**File:** [components/footer.js](components/footer.js)

```javascript
// Line 6: Change the copyright name
&copy; {new Date().getFullYear()} Takuya Matsuyama. All Rights Reserved.
// ← CHANGE "Takuya Matsuyama"
```

---

### 2. **Images & Media**

#### Profile Picture
**File:** [pages/index.js](pages/index.js#L51-L65)

```javascript
// Line 59-61: Replace profile image
<Image
  src="/images/takuya.jpg"  // ← REPLACE WITH YOUR IMAGE
  alt="Profile image"
  width="100"
  height="100"
/>
```

**Steps:**
1. Replace `/public/images/takuya.jpg` with your profile picture
2. Update image dimensions (width/height) if needed
3. Use JPG, PNG, or WebP format

#### Work Thumbnails
**File:** [pages/works.js](pages/works.js#L5-L15)

```javascript
// Lines 5-15: Import thumbnail images for each work
import thumbInkdrop from '../public/images/works/inkdrop_eyecatch.png'
import thumbWalknote from '../public/images/works/walknote_eyecatch.png'
// ← REPLACE THESE WITH YOUR WORK IMAGES

// Then reference them in the WorkGridItem:
<WorkGridItem id="inkdrop" title="Inkdrop" thumbnail={thumbInkdrop}>
  Your work description here
</WorkGridItem>
```

**Steps:**
1. Add your work images to `/public/images/works/`
2. Update import statements at the top of the file
3. Use consistent naming like `work-name_eyecatch.png`
4. Recommended size: 200x200px or larger

#### Wallpaper Images
**File:** [pages/wallpapers/index.js](pages/wallpapers/index.js#L7-L8)

```javascript
// Lines 7-8: Import wallpaper thumbnails
import thumbCherryBlossoms from '../../public/images/wallpapers/cherry-blossoms/ls-13.jpg'
import thumbMachiya from '../../public/images/wallpapers/machiya/ls-03.jpg'
// ← REPLACE WITH YOUR WALLPAPER IMAGES
```

#### Post/Content Thumbnails
**File:** [pages/posts.js](pages/posts.js#L5-L12)

```javascript
// Lines 5-12: Import thumbnail images
import thumbPortfolio from '../public/images/contents/youtube-how-to-build-portfolio.jpg'
// ← REPLACE WITH YOUR POST IMAGES
```

---

### 3. **Social Links**

#### Add Social Media Icons
**File:** [pages/index.js](pages/index.js)

Find the social links section (usually near the bottom) and add your links:

```javascript
// Around line 140-160: Social links
<Link href="https://twitter.com/YOUR_HANDLE" target="_blank">
  <IoLogoTwitter />
</Link>
<Link href="https://github.com/YOUR_USERNAME" target="_blank">
  <IoLogoGithub />
</Link>
<Link href="https://instagram.com/YOUR_HANDLE" target="_blank">
  <IoLogoInstagram />
</Link>
```

**Available icons from React Icons:**
- `IoLogoTwitter`
- `IoLogoGithub`
- `IoLogoInstagram`
- `IoLogoYoutube`
- `IoLogoLinkedin`
- And many more ([react-icons.github.io/react-icons](https://react-icons.github.io/react-icons))

---

### 4. **Work/Projects Section**

#### Adding a New Work/Project

**Step 1:** Create a new file for your work
**File:** [pages/works/your-project.js](pages/works/)

```javascript
import {
  Container,
  Badge,
  Link,
  List,
  ListItem,
  AspectRatio
} from '@chakra-ui/react'
import { ExternalLinkIcon } from '@chakra-ui/icons'
import { Title, WorkImage, Meta } from '../../components/work'
import P from '../../components/paragraph'
import Layout from '../../components/layouts/article'

const Work = () => (
  <Layout title="Your Project Name">
    <Container>
      <Title>
        Your Project Name <Badge>2023-</Badge>
      </Title>
      <P>
        Brief description of your project. What does it do? Make it compelling!
      </P>
      <List ml={4} my={4}>
        <ListItem>
          <Meta>Website</Meta>
          <Link href="https://yourproject.com/">
            https://yourproject.com/ <ExternalLinkIcon mx="2px" />
          </Link>
        </ListItem>
        <ListItem>
          <Meta>Platform</Meta>
          <span>Web/Mobile/Desktop</span>
        </ListItem>
        <ListItem>
          <Meta>Stack</Meta>
          <span>Your tech stack</span>
        </ListItem>
      </List>

      <WorkImage src="/images/works/your-project_01.png" alt="Project" />
      <WorkImage src="/images/works/your-project_02.png" alt="Project" />
    </Container>
  </Layout>
)

export default Work
export { getServerSideProps } from '../../components/chakra'
```

**Step 2:** Add to works overview
**File:** [pages/works.js](pages/works.js)

```javascript
// Add import at top
import thumbYourProject from '../public/images/works/your-project_eyecatch.png'

// Add to grid
<WorkGridItem 
  id="your-project" 
  title="Your Project Name" 
  thumbnail={thumbYourProject}
>
  One line description of your project
</WorkGridItem>
```

**Step 3:** Add images
1. Place thumbnail at `/public/images/works/your-project_eyecatch.png`
2. Place detailed images at `/public/images/works/your-project_01.png`, etc.

---

### 5. **Wallpapers Section**

#### Adding Wallpaper Packs

**File:** [pages/wallpapers/index.js](pages/wallpapers/index.js)

```javascript
// Import your wallpaper thumbnail
import thumbMyWallpaper from '../../public/images/wallpapers/my-collection/ls-01.jpg'

// Add to grid
<WorkGridItem
  category="wallpapers"
  id="my-collection"
  title="My Collection Name"
  thumbnail={thumbMyWallpaper}
>
  Description of your wallpaper collection
</WorkGridItem>
```

**Create detailed wallpaper page:**
**File:** [pages/wallpapers/my-collection.js](pages/wallpapers/)

```javascript
import {
  Container,
  Badge,
  Link,
  List,
  ListItem
} from '@chakra-ui/react'
import { Title, WorkImage, Meta } from '../../components/work'
import P from '../../components/paragraph'
import Layout from '../../components/layouts/article'

const Wallpaper = () => (
  <Layout title="My Collection">
    <Container>
      <Title>
        My Collection <Badge>2024</Badge>
      </Title>
      <P>Description of your wallpaper collection</P>
      <WorkImage src="/images/wallpapers/my-collection/ls-01.jpg" alt="Wallpaper" />
      <WorkImage src="/images/wallpapers/my-collection/ls-02.jpg" alt="Wallpaper" />
    </Container>
  </Layout>
)

export default Wallpaper
export { getServerSideProps } from '../../components/chakra'
```

---

### 6. **Posts/Content Links**

#### Adding Links to Your Content

**File:** [pages/posts.js](pages/posts.js)

```javascript
// Add import for thumbnail
import thumbYourPost from '../public/images/contents/your-post-thumbnail.jpg'

// Add to grid
<GridItem
  title="Your Post Title"
  thumbnail={thumbYourPost}
  href="https://link-to-your-post.com"
/>
```

**Steps:**
1. Import your thumbnail image
2. Create a `GridItem` component with:
   - `title`: The post title
   - `thumbnail`: The image file
   - `href`: Link to your post (external URL)

---

### 7. **Colors & Theme**

#### Change Color Scheme
**File:** [lib/theme.js](lib/theme.js)

```javascript
// Line 5: Main background color
body: {
  bg: mode('#f0e7db', '#202023')(props)
  //     light   dark  ← Change these colors
}

// Line 19: Link color
baseStyle: props => ({
  color: mode('#3d7aed', '#ff63c3')(props),
  //     light     dark   ← Change these colors
})

// Line 27-28: Add custom colors
const colors = {
  grassTeal: '#88ccca'  // ← Change accent color
}
```

**Color Mode Function Explanation:**
- `mode(lightColor, darkColor)` = provides different colors for light and dark themes
- First color = Light theme
- Second color = Dark theme

#### Change Font
**File:** [lib/theme.js](lib/theme.js#L25-L27)

```javascript
const fonts = {
  heading: "'M PLUS Rounded 1c'"  // ← Change heading font
}
```

To use a different font:
1. Add font import to [components/fonts.js](components/fonts.js)
2. Update the font name in theme.js

#### Change Section Title Style
**File:** [lib/theme.js](lib/theme.js#L11-L20)

```javascript
'section-title': {
  textDecoration: 'underline',
  fontSize: 20,
  textUnderlineOffset: 6,
  textDecorationColor: '#525252',  // ← Change underline color
  textDecorationThickness: 4,
  marginTop: 3,
  marginBottom: 4
}
```

---

### 8. **Navigation**

#### Add/Remove Navigation Links
**File:** [components/navbar.js](components/navbar.js#L70-L80)

```javascript
// Around line 70-80: Navigation links
<LinkItem href="/works" path={path}>
  Works  // ← Navigation label
</LinkItem>
<LinkItem href="/posts" path={path}>
  Posts
</LinkItem>
// Add new links here:
<LinkItem href="/your-page" path={path}>
  Your Page Name
</LinkItem>
```

---

### 9. **Meta Tags & SEO**

#### Update Meta Information
**File:** [components/layouts/main.js](components/layouts/main.js#L12-L32)

```javascript
<Head>
  <meta name="description" content="Takuya's homepage" />
  // ↑ Change this
  
  <meta name="author" content="Takuya Matsuyama" />
  // ↑ Change this
  
  <meta name="twitter:title" content="Takuya Matsuyama" />
  // ↑ Change this
  
  <meta name="twitter:site" content="@craftzdog" />
  // ↑ Change to your Twitter handle
  
  <meta name="twitter:creator" content="@craftzdog" />
  // ↑ Change to your Twitter handle
  
  <title>Takuya Matsuyama - Homepage</title>
  // ↑ Change this
</Head>
```

#### Update Social Card Image
The social card image (shown when sharing on Twitter/Facebook):

1. Replace `/public/images/card.png` with your custom card
2. This appears in the meta tags:
```javascript
<meta name="twitter:image" content="https://www.yoursite.com/card.png" />
<meta property="og:image" content="https://www.yoursite.com/card.png" />
```

---

## Adding New Pages

### Create a Simple Page

**File:** [pages/my-page.js](pages/)

```javascript
import { Container, Heading, Text } from '@chakra-ui/react'
import Layout from '../components/layouts/article'

const MyPage = () => (
  <Layout title="My Page">
    <Container>
      <Heading as="h2" variant="page-title">
        My Page Title
      </Heading>
      <Text>
        Your page content goes here
      </Text>
    </Container>
  </Layout>
)

export default MyPage
export { getServerSideProps } from '../components/chakra'
```

This will automatically become a route at `/my-page`

---

## Running & Deploying

### Local Development

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Open http://localhost:3000 in your browser
```

### Build for Production

```bash
# Build the project
npm run build

# Start production server
npm start
```

### Code Formatting

```bash
# Format code with Prettier
npm run prettier
```

### Deploy to Vercel

This project is configured for Vercel deployment:

1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Click "New Project" and import your repository
4. Click "Deploy"

That's it! Your site will be live.

---

## Quick Reference: Files to Customize

| What to Change | File | Lines |
|---|---|---|
| Your name | [pages/index.js](pages/index.js) | 36-37 |
| Your bio | [pages/index.js](pages/index.js) | 48-70 |
| Profile picture | [pages/index.js](pages/index.js) | 59 |
| Social links | [pages/index.js](pages/index.js) | 140-160 |
| Works overview | [pages/works.js](pages/works.js) | - |
| Colors/Theme | [lib/theme.js](lib/theme.js) | - |
| Navigation menu | [components/navbar.js](components/navbar.js) | 70-80 |
| Footer copyright | [components/footer.js](components/footer.js) | 6 |
| Meta tags/SEO | [components/layouts/main.js](components/layouts/main.js) | 12-32 |
| Logo text | [components/logo.js](components/logo.js) | 28 |

---

## Tips & Best Practices

1. **Image Optimization**
   - Use optimized images (WebP when possible)
   - Compress images before uploading
   - Recommended sizes: 
     - Profile: 100x100px
     - Work thumbnails: 400x300px
     - Banner: 1200x630px

2. **Content Updates**
   - Keep descriptions concise and compelling
   - Use keywords for SEO
   - Add dates to your works (e.g., "2023-")

3. **Performance**
   - Next.js automatically optimizes images
   - Use lazy loading for images
   - Minimize external library imports

4. **Testing**
   - Test dark/light mode toggle
   - Check mobile responsiveness
   - Test all links work correctly

5. **Git Workflow**
   - Commit changes regularly
   - Use meaningful commit messages
   - Keep your fork updated

---

## Troubleshooting

**Images not showing?**
- Check image paths start with `/images/`
- Ensure files are in `/public/images/` folder
- Verify image format is supported (JPG, PNG, WebP)

**Build fails?**
- Run `npm install` to ensure all dependencies are installed
- Check for syntax errors in modified files
- Clear `.next` folder: `rm -rf .next` and rebuild

**Styling not working?**
- Check Chakra UI components are properly imported
- Verify theme colors use valid hex codes
- Check for typos in component props

---

## Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Chakra UI Documentation](https://chakra-ui.com/docs)
- [React Icons](https://react-icons.github.io/react-icons)
- [Framer Motion](https://www.framer.com/motion)

---

**Last Updated:** February 17, 2026

Happy customizing! 🚀
