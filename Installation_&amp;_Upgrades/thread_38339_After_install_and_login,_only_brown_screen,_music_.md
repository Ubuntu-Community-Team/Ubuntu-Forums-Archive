---
title: "After install and login, only brown screen, music and cursor..."
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by ericdsr on 2005-05-31
And nothing else. No right-click context menus, task bar...nothing but the color of the good earth.  :?  I just did a major system upgrade and re-installed Hoary Hedgehog (new config in sig). The only hint I see is when I boot recovery mode and look at the X.log, the final line reads: Could not init font path element unix/:7100, removing from list. Any ideas are appreciated...

Eric

---

### Post by ericdsr on 2005-05-31
Found the answer. To resolve this issue, I just did an nvidia-glx install as outlined in the superb Ubuntu Starter Guide. Why this didn't make it at install, I dunno. Hope this helps somebody in the future...

---

