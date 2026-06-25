# Classroom Live

Real-time polling and word cloud tool built for classroom use. No subscriptions, no monthly limits. Built on Supabase and deployed on Vercel.

---

## What This Is

Three HTML files that work together to give you live student input during lessons. Students respond on their phones. Results appear animated on your display in real time. Embeds directly into Slides.com via iframe.

---

## The Three Pages

| File | Who Uses It | What It Does |
|------|-------------|--------------|
| `teacher.html` | You, on your computer | Launch sessions, pick mode, see response count, end sessions |
| `student.html` | Students, on their phones | Submit a vote or a word, one response per session |
| `display.html` | Your Slides.com iframe | Shows live animated results as students respond |

---

## Four Session Modes

- **A B C D** — Multiple choice poll with your own answer text
- **Yes / No** — Binary quick vote
- **1 – 5** — Scale rating
- **Word Cloud** — Students type a word, cloud grows and scales live

---

## How To Use It In Class

1. Open `teacher.html` on your computer before class
2. Type your question, pick a mode, hit **Launch Session**
3. Tell students to go to your student URL on their phones
4. Open `display.html` in your Slides.com iframe — results appear live
5. Hit **End Session** when done

---

## Your URLs

- Teacher: `https://project-ua4hr.vercel.app/teacher.html`
- Student: `https://project-ua4hr.vercel.app/student.html`
- Display: `https://project-ua4hr.vercel.app/display.html`

---

## How To Update The App

1. Go to this GitHub repo
2. Click the file you want to edit
3. Click the pencil icon to edit
4. Make your changes and click **Commit Changes**
5. Vercel redeploys automatically within 30 seconds
6. Your live URL stays the same

---

## Backend

**Supabase project:** `weston-classroom`
**Project URL:** `https://yxppaxroxgndbzgsmfqz.supabase.co`

Two tables power everything:

- `sessions` — stores each question, mode, and active state
- `responses` — stores every student response linked to a session

Real-time updates use Supabase's built-in Postgres change subscriptions. No websocket server needed.

---

## If Something Breaks

**Students see "Waiting for session" but you launched one**
Check that the session inserted correctly in your Supabase dashboard under Table Editor, then Sessions. If the table is empty the SQL may not have run correctly.

**Display page shows no results**
Make sure you are looking at `display.html` not `teacher.html`. Also confirm the session shows `active: true` in Supabase.

**Vercel shows a 404 at the root URL**
Normal. Go directly to one of the three page URLs above. There is no homepage by design.

---

## Built With

- [Supabase](https://supabase.com) — real-time database, free tier
- [Vercel](https://vercel.com) — hosting, free tier
- [DM Sans](https://fonts.google.com/specimen/DM+Sans) — Google Fonts
- Vanilla HTML, CSS, and JavaScript — no frameworks, no build step
