---
title: "cannot install ubuntu whatsoever"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by P8ntBal1551 on 2008-01-27
i had ubuntu on my old laptop and it was working fine
now im trying to install it on my new desktop and nothing
i try to book up into the live disk and my moniter has the "out of range" error
then i try to book up in safe graphics mode and it comes up with a blinking _
if you guys think it may have something to do with my hardware : 
biostar t force 570
gigabyte 8800gt
2 gigs on 2 sticks of ocz reaper
dvd sata deive
20.1" moniter widescreen resolution at 1680 x 1050

please i really want ubuntu on my comp

---

### Post by Pumalite on 2008-01-27
Install with the Alternate CD and then follow this thread:
[http://ubuntuforums.org/showthread.php?t=679266](http://ubuntuforums.org/showthread.php?t=679266)

---

### Post by P8ntBal1551 on 2008-01-27
whats the link to tell me how to install in text mode?

---

### Post by Pumalite on 2008-01-27
[https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6](https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by P8ntBal1551 on 2008-01-28
ok well i got it installed but now whenever i try to install it in either safe mode or regular it goes into the check desk, and it does that everytim i restart it, and if i leave it it says its going to restart but eventually doesnt, it just stays black
also if i try to boot to windows from grub i cant, it just says no signal detected

---

### Post by Pumalite on 2008-01-28
Check your drive with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by P8ntBal1551 on 2008-01-28
ok well i tried to install my nvidia driver and it worked until i restarted it and now it seems as thought my compiz isnt working anymore because i tryed to find the gui settings manager for compiz it fried out on me and now i cant get the "visual effects" tab over "none" in  the appearance preferances and my nvidia driver isnt working anymore, at all

---

### Post by overdrank on 2008-01-28
> **P8ntBal1551 said:**
> ok well i tried to install my nvidia driver and it worked until i restarted it and now it seems as thought my compiz isnt working anymore because i tryed to find the gui settings manager for compiz it fried out on me and now i cant get the "visual effects" tab over "none" in  the appearance preferances and my nvidia driver isnt working anymore, at all

HI and how did you install the drivers, Restricted drivers? What is the model of the graphics card?

---

### Post by P8ntBal1551 on 2008-01-28
there was a forum telling me how to install the nvidia driver and its a 8800 gt

---

### Post by overdrank on 2008-01-29
> **P8ntBal1551 said:**
> there was a forum telling me how to install the nvidia driver and its a 8800 gt

Ok it may be a simple as reconfiguring your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` command in the terminal

---

### Post by P8ntBal1551 on 2008-01-29
ya, no it really didnt work
and just in case i switched between *** the X11 backups
nvidia still isnt my default card driver and compiz is still not working

---

### Post by P8ntBal1551 on 2008-01-29
help...?

---

### Post by overdrank on 2008-01-29
> **P8ntBal1551 said:**
> help...?

HI and maybe Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by DDuong on 2008-01-29
The Envy script that OverDrank posted helped me a lot.  Give that a try.

---

### Post by P8ntBal1551 on 2008-02-18
ok so first the live cd didnt like my widescreen moniter, no problem, i use the alternate install disk
success, i can at least see the gui, i try to set my resolution using the restricted driver manager
no success, it wont stick, i try to change it before the gui loads and after, neither time works
so i download envy and it installs the nvidia driver, and i try to boot up, my moniter says its out of range
i go look in the xorg.conf, it says the moniter is 1680x1680, its spoused to be 1680x1050, so i change it to that, i try agian, nothing, so i come here
also compiz wont load whatsoever, when i turn on the special graphics options, it gives me an error (im sorry i cant remember) and reverts back to the none

---

### Post by P8ntBal1551 on 2008-02-18
please help?

---

### Post by P8ntBal1551 on 2008-02-18
ok so first the live cd didnt like my widescreen moniter, no problem, i use the alternate install disk
success, i can at least see the gui, i try to set my resolution using the restricted driver manager
no success, it wont stick, i try to change it before the gui loads and after, neither time works
so i download envy and it installs the nvidia driver, and i try to boot up, my moniter says its out of range
i go look in the xorg.conf, it says the moniter is 1680x1680, its spoused to be 1680x1050, so i change it to that, i try agian, nothing, so i come here
also compiz wont load whatsoever, when i turn on the special graphics options, it gives me an error (im sorry i cant remember) and reverts back to the none

---

### Post by P8ntBal1551 on 2008-02-18
nothing helped

---

### Post by P8ntBal1551 on 2008-02-18
ok i can install ubuntu
but i cant get the screen resolution to stick on the restricted drivers manager
then i try to install the nvidia driver through envy and the screen reslution goes to big for my screen

---

### Post by P8ntBal1551 on 2008-02-18
help please?...

---

### Post by P8ntBal1551 on 2008-02-19
ok then ill havta stick to xp

---

