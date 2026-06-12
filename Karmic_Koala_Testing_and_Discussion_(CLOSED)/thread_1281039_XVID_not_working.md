---
title: "XVID not working"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by canabal on 2009-10-02
Hey all, I just upgraded to the beta from my jaunty install and I cannot seem to play XVID files.  In vlc I get the error: 

No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.


I have not removed any packages, and I have tried removing and re-install gstreamer, but still nothing.   Any ideas?

---

### Post by BAMF1501 on 2009-10-02
i do aslo have same issue hope it gets fixed soon:confused:

---

### Post by blakamin on 2009-10-02
have you made sure libavcodec is installed?

---

### Post by BAMF1501 on 2009-10-02
i jsut reinstalled libavcodec and works fine now thanks

---

### Post by canabal on 2009-10-02
tried re-installing and still nothing, although I did not find a plain libavcodec, only libavcodec-extra-52 & libavcodec-unstripped-52 so I did them.

Any idea why i am missing libavcodec?

---

### Post by BAMF1501 on 2009-10-02
do you have xvid cap installed cause i notice when i install vlc mediaplayer xvid cap dissapears and i have to reinstall it and when i do that vlc dissapears ??

---

### Post by canabal on 2009-10-02
Just tried install xvidcap, didnt uninstall vlc, but did not fix the problem either.

---

### Post by canabal on 2009-10-03
When I try other vids, it seems they do not work either and I get a different error message (for a different decoder).

No suitable decoder module:
VLC does not support the audio or video format "avc1". Unfortunately there is no way for you to fix this.


This would probably all be resolved if I did a clean install, but i should not have to as a lot of people will likely try upgrading.  Anyone have any other ideas of packages to try to reinstall?

---

### Post by BAMF1501 on 2009-10-03
Yes mine still currently is not working either :(

---

### Post by Longinus00 on 2009-10-03
[http://ubuntuforums.org/showthread.php?t=1281569](http://ubuntuforums.org/showthread.php?t=1281569)

---

### Post by canabal on 2009-10-03
> **Longinus00 said:**
> [http://ubuntuforums.org/showthread.php?t=1281569](http://ubuntuforums.org/showthread.php?t=1281569)

Thanks for that link, it worked.

For those that are curious, it says to reinstall the ubuntu-restricted-extras (if you are too lazy to open the link).

---

