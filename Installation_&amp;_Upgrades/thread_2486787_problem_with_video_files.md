---
title: "problem with video files"
date: 2023-05-10
forum: Installation &amp; Upgrades
---

### Post by hmiersch on 2023-05-10
hi. 
i recently installed 23.04, and now i have a problem: i can no longer play my video files that worked normally under 20.04. when i try to play such a file using videos, all i get is a blank video window and the following error message:   

unable to play the file. Gstreamer element vaapipostproc is required to play the file, but is not installed.  

i tried to install it with sudo apt-get install vaapipostproc but it told me it couldn't find the package or something similar. IOW, no luck. so what can i do?

---

### Post by SeijiSensei on 2023-05-10
I use mpv with smplayer as the front end. Plays everything.

```
sudo apt install mpv smplayer
```

---

### Post by monkeybrain20122 on 2023-05-12
Try deleting the gstreamer cache

  ```
rm -r ~/.cache/gstreamer-1.0
```

or simply navigate there (press ctrl+h to show hidden files) and delete it.


+1 for mpv. It uses ffmpeg instead of gstreamer and works much better than totem/Video, which is garbage.

---

### Post by TheFu on 2023-05-12
I've been frustrated by Gstreamer for decades and try to avoid anything that needs it. It isn't hard.  

**mpv** or **vlc** don't use it.  mpv has a few different GUI front-ends, if you prefer them.  Anyway, if you make mpv your default video playing application and learn just a few of the keyboard commands, it is really efficient and plays anything (well, anything you should want to see).

If you still want to get gstreamer working, [https://gstreamer.freedesktop.org/documentation/frequently-asked-questions/troubleshooting.html](https://gstreamer.freedesktop.org/documentation/frequently-asked-questions/troubleshooting.html) might be helpful.  

But you have 3 very experienced users suggesting to use a different application. Your choice.

---

