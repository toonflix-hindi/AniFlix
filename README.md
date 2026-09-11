# ToonFlix Hindi Dub

Professional dark anime streaming frontend for GitHub Pages + Firebase Realtime Database.

## Files
- `index.html` — home/library and anime cards
- `anime.html` — anime details, episode list and player
- `admin.html` — Firebase-authenticated admin panel
- `config.js` — Firebase project settings
- `style.css` — responsive dark UI
- `script.js`, `anime.js`, `admin.js` — application logic

## Firebase setup
1. In Firebase Console, enable **Authentication → Sign-in method → Email/Password**.
2. Create your admin user in Authentication.
3. Open **Project settings → General → Your apps → Web app** and copy the Web API Key.
4. Put the key in `config.js`:
   `FIREBASE_API_KEY: "AIza..."`

The database URL is already configured:
`https://toonflix-wed-default-rtdb.firebaseio.com`

## Recommended Realtime Database rules
Use authenticated users for writes. Public visitors can read the anime catalog:

{
  "rules": {
    "anime": {
      ".read": true,
      ".write": "auth != null"
    }
  }
}

For stronger security, restrict writes to an admin UID instead of every authenticated user.

## GitHub Pages
Upload all files to the repository root and enable GitHub Pages from the repository's Pages settings.

## Episode links
Each episode accepts either:
- a direct browser-playable video URL (`.mp4`, `.webm`, `.m3u8`) and choose `video`, or
- a third-party embed/player URL and choose `embed`.

Only add media you have permission to distribute/stream.
