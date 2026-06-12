---
title: "screen resolution 1400 x 1050 pixels"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by JANNL on 2007-06-02
Hi People,

New to Ubuntu I installed 7.04 as a dual boot on my Windows XP Pro machine. I use a Samsung SyncMaster 203 B (20 inch) monitor and try to get the right alignment and resolution adjustments. So far I edited xserver-xorg without getting the desired effect. FYI : My video card is Intel(R) 82845 G/GL/GE/PE/GV sitting in a Dell GX260 machine. I used i820 setting (under xorg) but my Ubuntu start-up screen out aligns to the right or to the left (depending on the xorg setting I gave) but I don't get it fully aligned around the monitor edges.

Can someone out there give me some helpful hints and or suggetions ?  Very much appreciated.:)

Regards,
Jan

---

### Post by linuxbz on 2007-06-02
I am running 7.04 on a Dell Latitude D520 laptop. I could not get the native 1400x1050 resolution until I replaced the xserver-xorg-video-i810 package with xserver-xorg-video-intel. If you don't get any more definitive answer, you might try that. After backing up your xorg.conf, of course.

---

### Post by JANNL on 2007-06-03
I am following the steps described in the following link: 

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html) 

At that point where to make a choice from which video driver to apply I don't find the one 
you mention i.e. ~ video-intel 

o Can you pls. tell me where to find this specific item ?

Thanks for your response,
Jan

---

