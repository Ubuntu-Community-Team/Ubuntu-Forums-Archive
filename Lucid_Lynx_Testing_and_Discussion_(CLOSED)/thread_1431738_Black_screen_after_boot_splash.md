---
title: "Black screen after boot splash"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Nyoro on 2010-03-17
I am completely unable to access my installation, as my screen turns black and goes into powersave mode after X launches. Also, I am unable to access any of the text terminals on alt-ctrl-f1/f2/f3/f4. My screen briefly wakes up from powersave when I switch back and forth between the text terminals and X on alt-f7, however it goes directly back to powersave mode, and X is not visible at any time.

I tried booting into recovery mode, in order to inspect the Xorg log. It apparently loads the video driver and recognizes my display. No apparent errors (EE or WW).

The problem is persistent, in fact I haven't been able to see the lucid desktop once since installation. I am thinking that the problem could lie in using the open source ati driver which does not explicitly support the 5770. However, "it was working on Karmic".

I have looked through the lucid bugs and didn't find anything pertinent. I'd like to submit a bug report, but I think I need a slightly better understanding of the problem to provide a useful bug report.

On a side note, I had a lot of trouble getting the live CD to boot, finally managed by disabling my floppy drive in bios. Probably not related.

System ran 9.10 and Windows fine.

System info
-----------
Alpha 3 daily (from 16th of March).
ATI Radeon 5770
Dell u2410 monitor, using the displayport connector.

I'd be happy if someone could point me in the right direction to start troubleshooting this, or if someone would share similar experiences, that could lead to a better understanding of the problem.

For instance, could I force Xorg-server to use another driver? Would the "VESA" driver be a good failsafe to test against?

---

### Post by blakamin on 2010-03-17
Have you tried disabling plymouth?
edit: I've heard that ATI drivers aren't supported at this stage. (not sure if this includes the open source ones)

---

### Post by monraaf on 2010-03-17
Support in the open source radeon driver for Evergreen (HD5xxx) is rather new, so not everything is working correctly yet. You may want to try connecting your monitor through DVI or HDMI. If that's not an option then the VESA driver should "work". It's what you were probably using in Karmic when not using fglrx.

---

### Post by Nyoro on 2010-03-17
Thanks for the leads. 

I haven't tried disabling plymouth, as I (wrongfully?) thought that the problem was related to X rather than to the booting process.

I think I was actually running the fglxr driver on Karmic, at least I remember seeing a ATI logo with the text "unsupported hardware" overlaid on the bottom right of the screen.

I think I am going to try out Moonrafs suggestion, thanks :-D

Is this something that should be filed as a bug against lucid?

---

### Post by Nyoro on 2010-03-17
I was able to force X to use the VESA driver and get X up and running that way. It's not pretty but its a step in the right direction, so thanks for your help on that. I guess my next step will be to try to install the proprietary driver, or perhaps check up on the open source driver.

Edit:

After seeing this [http://www.botchco.com/agd5f/?p=48](http://www.botchco.com/agd5f/?p=48), I will probably be temporarily exchanging the display port cable with a HDMI or DVI, and try using the open source driver.

---

### Post by ozonehole on 2010-03-17
May I just ask, "How do you force X to use the VESA driver?" I want to do this too, and so far I haven't found the trick. Yes, I do know about file xorg.conf - the trouble is, I'm running Lucid Alpha3, and there is no xorg.conf file! They must have changed the way to do this configuration, but I'm not seeing it.

===================================================

OK, found the answer to my question. Rather than delete this post, I'll link the solution here, in case others need to know:

Where did xorg.conf go?
[http://ubuntuforums.org/showthread.php?t=1428788](http://ubuntuforums.org/showthread.php?t=1428788)

---

### Post by Nyoro on 2010-03-18
What I did was to run Xorg -configure. This generates /root/Xorg.conf.new. I then edit this file and move it to /etc/X11/xorg.conf.

---

