---
title: "Desktop takes time to show up after entering password on login screen-2478238"
date: 2024-10-16
forum: Installation &amp; Upgrades
---

### Post by anspectrum on 2024-10-16
I have created this thread because original thread can no longer be edited. Original thread is at [https://ubuntuforums.org/showthread.php?t=2478238](https://ubuntuforums.org/showthread.php?t=2478238)

Continuing from original thread...

I upgraded Ubuntu 22.04 to 24.04 in Sept 2024 however that delayed appearance of Desktop was still there. Today I was reading a [blog]("https://utcc.utoronto.ca/~cks/space/blog/linux/Fedora40LoginStallWhy") and came across this utility ```
extrace 
``` I thought about trying it. So I used ```
extrace -ltu -o Desktop/trace
``` command to start the trace while trying to login using second user. It took usual ~2+ mins. But this time I was able to catch ```
41751- /bin/xbrlapi exited status=4 time=133.389s
``` in the output file. A quick review shows that this is related to accessibility related features. Details can be found [here]("https://packages.debian.org/unstable/xbrlapi"). I uninstalled it and viola, login time snapped back to 2-3 sec. I don't know how it was installed in the first place or what caused it to misbehave after I upgraded to 22.04.

This issue bugged me for over two years. I tried many times to diagnose including taking help from ChatGPT for synthesizing logs however nothing worked. Hopefully this information can be helpful for others in some way.

---

