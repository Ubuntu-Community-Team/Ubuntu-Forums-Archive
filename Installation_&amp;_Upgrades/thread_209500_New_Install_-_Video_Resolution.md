---
title: "New Install - Video Resolution?"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by jsimmons on 2006-07-05
There are only three resolutions available on a fresh install?  I have a nVidia 7900GTX connected to a 19-inch LCD, and that's all I got (currently set to  1024x768).  All of the resolutions available through the settings are lower than my monitor's native resolution (1280x1024).  Do I *have* to install nVidia's accelerated drivers to get my desired resolution?

---

### Post by ariek on 2006-07-05
Try:
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
``` 
Then restart X with Ctrl-Alt-Backspace

Good luck

---

