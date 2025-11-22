Knowledge Base: Managing the Career Simulator Content
Document ID: KB-CS-001Role: Administrator / Content ManagerSystem: Career Simulator v2.5

1. Overview
The "Career Simulator" is a high-performance web app. Instead of a database, it uses a Local Data Store inside the code. This guide explains how to update text, images, and links by editing the RESUME_DATA object in App.jsx.Key Rule: Always update both the en (English) and fr (French) sections to keep the site consistent.

2. Managing Projects (The Portfolio)
Projects now support detailed descriptions, media galleries, and status indicators.

2.1 Adding a New ProjectFind the projects array in RESUME_DATA. Add a new object:

{
    id: "p_new",
    title: "New Project Title",
    role: "Your Role",
    status: "completed", // Options: 'completed', 'in-progress', 'on-pause'
    desc: "Short summary for the main card.",
    fullDescription: "Long, detailed description. Use \n\n for new paragraphs.",
    tech: ["Tool A", "Tool B"],
    icon: "Monitor", // Options: Monitor, Server, Globe, Code
    media: [
        { type: "image", url: "[https://image-link.com](https://image-link.com)", caption: "Dashboard View" }
    ],
    codeSnippet: "console.log('Optional code snippet here')"
},

2.2 Traffic Light Status

The status field controls the colored dot on the project card:"completed" -> Green (Visible on Main Page)"in-progress" -> Yellow (Hidden from Main Page, visible in Hub)"on-pause" -> Red (Hidden from Main Page, visible in Hub)3. Managing Assets (Images & PDFs)3.1 Uploading Files to GitHubTo make your profile picture or resume available for download, you must upload the files to your GitHub repository.Go to your GitHub repository page (e.g., github.com/yourusername/career-simulator).Click Add file > Upload files.Drag and drop your files:Profile Picture: e.g., profile.jpgResume (English): e.g., Resume_EN.pdfCV (French): e.g., CV_FR.pdfClick Commit changes.3.2 Linking Assets in CodeOnce uploaded, you tell the app which file to use.Profile Picture:Find the profilePic line in RESUME_DATA and enter the exact filename you uploaded.profilePic: "profile.jpg",
CV & Resume Downloads:Find the downloads block and enter the filenames.downloads: {
    resume: "Resume_EN.pdf",
    cv: "CV_FR.pdf"
},
4. Updating Links & Socials4.1 Social Media & EmailTo change the main contact buttons in the footer:Find the social block:social: {
    linkedin: "[https://linkedin.com/in/yourprofile](https://linkedin.com/in/yourprofile)",
    email: "your.email@example.com"
},
4.2 Blog & Hobbies LinksYou can add links to external articles (Medium, LinkedIn Pulse) or social profiles (SoundCloud, Instagram).For Blogs:Add a link property to the blog item.{
  title: "Optimizing SCCM...",
  date: "Oct 12, 2023",
  read: "5 min read",
  link: "[https://medium.com/your-article-link](https://medium.com/your-article-link)" // Add this!
},
For Hobbies:Add a link property to the hobby item.{
  name: "Audio Engineering",
  icon: "Music",
  desc: "Mixing tracks...",
  link: "[https://soundcloud.com/yourprofile](https://soundcloud.com/yourprofile)" // Add this!
},
If you want the default link to be LinkedIn, just paste your LinkedIn URL here.5. Safety Checklist[ ] Commas: Every line inside an object {...} must end with a comma ,.[ ] Quotes: All text must be wrapped in " ".[ ] Filenames: Ensure filenames in the code match the uploaded files exactly (case-sensitive!). Profile.jpg is different from profile.jpg.