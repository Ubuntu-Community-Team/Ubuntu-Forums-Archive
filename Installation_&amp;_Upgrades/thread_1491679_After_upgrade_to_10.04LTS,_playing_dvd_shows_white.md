---
title: "After upgrade to 10.04LTS, playing dvd shows white screen"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by doublewitt on 2010-05-23
After upgrading to **10.04LTS**, I have this issue with ALL video players. Once the dvd begins to play, all I see is a white screen - no image. However, the sounds plays fine. What can I do to correct this?

Aside from this one issue, everything went fine in the upgrade process and I'm very happy with this new version. I just need to get this problem fixed, and so i would appreciate any help...

thanks!

---

### Post by doublewitt on 2010-05-29
any hope...?

---

### Post by doublewitt on 2010-06-02
anyone...?

---

### Post by iiiears on 2010-06-02
Hi,

   Add some system and video player info so others can help. That is why we are here.

---

### Post by doublewitt on 2010-06-02
Thanks.
This issue occurs with ALL video players. What kind of system info do you need?

---

### Post by wojox on 2010-06-02
> **doublewitt said:**
> Thanks.
This issue occurs with ALL video players. What kind of system info do you need?

Try this and see if it helps [http://wojox.homelinux.org/?p=12](http://wojox.homelinux.org/?p=12)

---

### Post by doublewitt on 2010-06-02
Thanks for the **link**. I did everything that was listed and that didn't solve the problem... still a white screen...

---

### Post by doublewitt on 2010-06-06
**I still need to fix that "[COLOR="Blue"]white screen[/COLOR]" issue...**
Can someone else offer suggestions on how to fix this problem? Any advice would be appreciated...

Ofcourse, Ubuntu 10.04LTS
+ AMD Phenom Quad Core Processor
4G Ram - Nvidea Card - GeForce 9800GT

---

### Post by doublewitt on 2010-06-12
suggestions...?!

---

### Post by doublewitt on 2010-06-15
What's happened...??!!!
Usually, the response is much better...
Nobody knows what to do...?

---

### Post by kots on 2010-06-17
Hi, I got a W510 thinkpad and installed 10.04, had exacty the same issue up until a few minutes ago...
This was a partial solution for me:
[http://ubuntuforums.org/showthread.php?t=476419](http://ubuntuforums.org/showthread.php?t=476419) (see #3)

Fixed playback (moview player) and cheese this way, not skype or VLC though... must be on the right track however. 

Will look into it further and if I get something i will let you know...

---

### Post by kots on 2010-06-17
...following the same reasoning as above, vlc will work if you go to tools->preferences->video->output and choose something like 'X11 video output' or OpenGL etc...

there must be a better solution to this...

---

### Post by doublewitt on 2010-06-17
Wow - ***thanks*** - that fixed my problem!
I did exactly what was said here:
[http://ubuntuforums.org/showthread.php?t=476419](http://ubuntuforums.org/showthread.php?t=476419) (see #3)
This corrected the problem for all my movie players...
:D

---

### Post by kots on 2010-06-18
Glad it did, note however that this solution involves the CPU doing all the work.

---

