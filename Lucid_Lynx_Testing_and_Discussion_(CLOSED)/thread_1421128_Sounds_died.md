---
title: "Sounds died"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kHERBy on 2010-03-03
To start I did update ubuntu to the dev release of 10.4 Lucid. Sound worked perfectly for the first few days, No issues. 

1. Updated to Lucid
2. Disabled postfix daemon(don't use mail server?)
3. Installed Enemy Territory
4. Installed liboss-all
5. RAN echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
6. Rebooted
7. No Sound.

Now I only installed liboss to try to get sound to work with et, however I found a different work around to allow it to work with pulse audio. Which worked fine... until I rebooted and came back to having no sound. Anyone care to help me troubleshoot this?

---

### Post by cariboo on 2010-03-04
A bump for the move

---

