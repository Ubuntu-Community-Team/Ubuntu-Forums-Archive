---
title: "ALSA disappears after trying to fix headphone issue"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by unicornz on 2011-11-18
After upgrading to 11.10 today, I found that my laptop speakers no longer automuted when I plugged in my headphones. I had this issue in Narwhal, but was able to find a workaround.

I tried [this]("http://ubuntuforums.org/showpost.php?p=9298037&postcount=6") and now I can't even open alsamixer. When I type sudo alsamixer into the terminal I get this error message:

cannot open mixer: no such file or directory

I'm getting no sound whatsoever now, and in "Sound" preferences the soundcard isn't showing up. I'm seeing a "Dummy Output" instead.

Help??

---

### Post by mikewhatever on 2011-11-19
Have you really downgraded to Alsa 1.0.23? Oneiric has a newer Alsa 1.0.24.1, which should have better audio hardware support.

PS: Alsamixer shold not be run with sudo.

---

### Post by unicornz on 2011-11-19
> **mikewhatever said:**
> Have you really downgraded to Alsa 1.0.23? Oneiric has a newer Alsa 1.0.24.1, which should have better audio hardware support.

PS: Alsamixer shold not be run with sudo.

                            Yeah, I didn't check carefully to see that the fix from the link was using the correct version of alsa... :( Stupid. At this point I think I should uninstall and reinstall. Even if I do, I'm annoyed that I'm going to have to find a new headphone jack workaround.

I've used the terminal to open alsamixer for a year now... works every time. Sudo or no sudo.

---

