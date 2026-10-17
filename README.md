# Pawel & Kinga Tasks

A Google Tasks board and day planner for two Google accounts. It's one HTML file with no server, and it works in any browser on Mac, PC, iPhone and Android.

- **Board**: one column per person. Drag to reorder or to hand a task to the other person. Tick to complete; tap a task to edit it.
- **Day**: drag tasks (or tap a task, then tap an hour) into half-hour slots. Meetings from Google Calendar show as busy time.
- Every change goes straight to Google Tasks, so the Google Tasks app on your phone shows the same thing.

## Put it online (GitHub Pages)

1. Upload `index.html`, `manifest.webmanifest`, `icon-192.png`, `icon-512.png` and `apple-touch-icon.png` to a **public** repository, for example `task-hub`.
2. In the repository, go to **Settings → Pages**, set **Source** to *Deploy from a branch*, pick **main** and **/ (root)**, then click **Save**.
3. After a minute the app is live at `https://YOUR-NAME.github.io/task-hub/`.

## Connect Google (once)

1. In [Google Cloud Console](https://console.cloud.google.com/projectcreate), create a project. It's free.
2. Enable the [Google Tasks API](https://console.cloud.google.com/apis/library/tasks.googleapis.com) and the [Google Calendar API](https://console.cloud.google.com/apis/library/calendar-json.googleapis.com).
3. In [Google Auth Platform](https://console.cloud.google.com/auth/overview), click **Get started** and choose audience **External**. Under **Audience → Test users**, add both Google accounts.
4. Under **Clients → Create client**, choose **Web application**, then add:
   - **Authorized JavaScript origins**: `https://YOUR-NAME.github.io`
   - **Authorized redirect URIs**: `https://YOUR-NAME.github.io/task-hub/`

   Copy the Client ID.
5. Put the Client ID in the `clientId: ''` line near the top of the script in `index.html`, so no device has to ask for it. You can paste it in ⚙ Settings instead, but then every device asks once.
6. Open the app and click **Connect** in each person's column.

Settings in the app shows the exact origin and redirect address to copy.

## Install on a phone

- **iPhone**: open the address in Safari, tap **Share → Add to Home Screen**. The Home Screen app keeps its own Google sign-in, so connect both accounts once inside it.
- **Android**: open the address in Chrome, tap **⋮ → Add to Home screen** (or **Install app**).

## Good to know

- Google's API can't store a task's time of day, only the date. When you place a task at an hour, the app adds a line like `⏰ 14:30` to the task's notes, which you'll also see on your phone.
- A Google sign-in lasts an hour. When you open the app, it refreshes expired sign-ins by itself with a quick hop through Google. If Google needs you to sign in again, the person's button turns amber.
- The email addresses are deliberately not in the code, because a public site shows its code to anyone. Each column remembers its Google account on each device after the first Connect.
