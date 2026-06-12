---
title: "Kernel 2.6.27-2"
date: 2008-08-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plun on 2008-08-29
Out...:)

It seems to be only a few changes.

>  
linux (2.6.27-2.3) intrepid; urgency=low
 .
   [ Ben Collins ]
 .
   * build/retag: Make script save .orig of tags for later use
   * ubuntu/lirc: Fix device_create call
   * build/firmware: Put in-kernel firmware into version specific subdir
     - LP: #262115
   * Rebase on linux-2.6 git.
   * ABI bump
 .
   [ Herton Ronaldo Krzesinski ]
 .
   * SAUCE: (no-up) Apparmor warning fixes
 .
   [ John Johansen ]
 .
   * SAUCE: (no-up) Proper AppArmor ptrace updates for newer lsm API
 .
   [ Mackenzie Morgan ]
 .
   * SAUCE: Add quirk for ASUS Z37E to make sound audible after resume
     - LP: #25896


[https://lists.ubuntu.com/archives/intrepid-changes/2008-August/006048.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-August/006048.html)




Lost my /home a couple of times during reboots....

---

### Post by ViRMiN on 2008-08-29
Yeah, my /home is a symlink to a /mnt directory, which the actual disk swaps from /dev/hda5 to /dev/sda5 to /dev/sdc5!  Should really mount it via UUID but... cba! :)

Not noticed any changes tbh... everything already works for me... still a +0.0.0-1 change is progress! :)

---

### Post by ViRMiN on 2008-08-29
For some bizarre reason, my /boot/grub/menu.lst doesn't update automatically and I usually edit it manually.  I ran update-grub earlier, which has put the splash back up and see blankness up until the Gnome login screen.  Previously, I had that option and "quiet" removed as I had problems with dmraid starting and being dumped at a busybox prompt, but, that got fixed this week.

---

### Post by dinxter on 2008-08-29
causes an early boot hard lockup here on amd64 compared to 2.6.26-1 if anyone has the same problem

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262742](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262742)

---

### Post by ViRMiN on 2008-08-29
> **dinxter said:**
> causes an early boot hard lockup here on amd64 compared to 2.6.26-1 if anyone has the same problem

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262742](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262742)

Works fine for me, I'm also on AMD64 (check my sig for specs)

---

### Post by gjoellee on 2008-08-29
Works great for me! After I updated the boot time was reduced so much I could notice it:)
AMD Athelon 3000+ 2.17 GHz
512mb RAM

> ubuntu@ubuntu-desktop:~$ uname -r
2.6.27-2-generic


---

### Post by Nullack on 2008-08-29
Didnt work for on first boot. GDM failed to load and was aborted to a command prompt. Then I edited out the usplash in the menu.lst, rebooted, it all worked.

---

### Post by vikrant82 on 2008-08-29
Sadly, virtualbox kernel module fails to compile on this one. Any workarounds to run virtualbox on this kernel are welcome.

---

### Post by DougieFresh4U on 2008-08-29
My old Intel box has not let me down. I have done dist-upgrades for the last 2 years and so far it handles it quite well.
Just wish i would get a video card instead of the on board crap I'm stuck with.
Excellent work devs  :)

---

### Post by vishalrao on 2008-08-30
i need to specify the "nolapic" option (amd64) to be able to boot on my HP tablet tx1302au.

the wl driver doesnt seem to work for me, but blacklisting it and installing the b43 driver and firmware works very well... jockey crashed during installation of b43 which i think is why i needed to manually run fwcutter's "installfirmware".sh script.

now "normal usage" (web browsing, opening files in OOo etc) works well but how do i monitor the "kernel" for issues? my CPU temp seems ok (from actual touching the exhaust location)...

---

### Post by Sef on 2008-09-01
> Works fine for me, I'm also on AMD64 (check my sig for specs)

Just installed Ibex and 2.6.2-7 has worked fine for me.

---

### Post by plun on 2008-09-01
RC5 is out "upstream"....

> Date	Thu, 28 Aug 2008 16:26:45 -0700 (PDT)
From	Linus Torvalds <>
Subject	Linux 2.6.27-rc5

Another week (my weeks do seem to be eight days, don't they? Very odd), 
another -rc.

The dirstat pretty much says it all:

  43.0% arch/arm/configs/
  43.9% arch/arm/
  25.5% arch/powerpc/configs/
  26.8% arch/powerpc/
  73.9% arch/
   4.4% drivers/usb/musb/
   5.4% drivers/usb/
   4.0% drivers/watchdog/
  16.0% drivers/
   3.5% fs/

yeah, the bulk of it is all config updates, and with arm and powerpc 
leading the pack.

But seriously, while the config updates amount to about three quarters of 
the diff, and if you don't use a rename-aware diff the blackfin include 
file movement pretty much accounts for the rest, hidden behind all those 
trivial (but bulky) changes are a lot of small changes that hopefully fix 
a number of regressions.

The most exciting (well, for me personally - my life is apparently too 
boring for words) was how we had some stack overflows that totally 
corrupted some basic thread data structures. That's exciting because we 
haven't had those in a long time.  The cause turned out to be a somewhat 
overly optimistic increase in the maximum NR_CPUS value, but it also 
caused some introspection about our stack usage in general. Including 
things like a patch to gcc to fix insane stack usage for vararg functions 
on x86-64.

But that one would only hit anybody who was a bit too adventurous and 
selected the big 4096 CPU configuration. The rest of the regressions fixed  are a bit more pedestrian.



[http://lkml.org/lkml/2008/8/28/371](http://lkml.org/lkml/2008/8/28/371)

---

### Post by FishRCynic on 2008-09-01
re: virtualbox

try here

[http://ubuntuforums.org/showthread.php?t=902105](http://ubuntuforums.org/showthread.php?t=902105)

or here

[http://forums.virtualbox.org/viewtopic.php?t=8997](http://forums.virtualbox.org/viewtopic.php?t=8997)

linux generic i686 
worked for me

---

### Post by Nullack on 2008-09-01
Yeah I saw that some days ago Plun. Mate I figured due to the weekend it'll take a few days for the kernel team to get it into our build.

---

