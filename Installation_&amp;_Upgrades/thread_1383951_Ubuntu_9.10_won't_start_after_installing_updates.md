---
title: "Ubuntu 9.10 won't start after installing updates"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by aaron3 on 2010-01-17
I recently installed Kubuntu without issue, but after I tried installing the initial batch of updates that the package manager prompted me with, it would no longer start. I noticed that one of the updates was to the Linux kernel itself, actually added options to my Grub boot menu to start either the old or new kernel version. For either one, it would  display the Kubuntu splash and hang for a long time, then print out "unable to mount root file system." I booted from the CD and modified my /etc/fstab to mount my filesystems from devices in /dev directly (instead of using UUIDs), and changing the command Grub used to also use my boot partition (/dev/sda3) directly instead of a UUID. This allowed the old version of the kernel to start up and run (though with a lot of errors that weren't there before), but the new kernel appearted to start up, then filled my screen with an image that looked like a distorted TV test pattern, and wouldn't do anything else. (the distortion would shift around a bit whenever I moved the mouse or typed on the keyboard).

Has anyone else had this problem, and can it be fixed?
Also, as a general rule is it a good idea to even install those updates, or should I just wait until the next Ubuntu version is released and do my updating all at once?

thanks in advance; any help is appreciated.

---

### Post by lidex on 2010-01-17
This may be helpful:
[http://www.ubuntu.com/getubuntu/releasenotes/910]("http://www.ubuntu.com/getubuntu/releasenotes/910")
Scroll down to this line:
> GRUB menu.lst: install the maintainer's version vs. keep the local version

Are you using grub2?
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by aaron3 on 2010-01-19
I'm using grub2, so I have grub.cfg instead.

I'm not sure the problem is in grub, though, because Grub started without issue and showed the new kernel in the menu; the problems started after the kernel started booting.

In the case of the weird pattern on my screen, I noticed that one of the updates was for X; does the newer version maybe not support my graphics card (an ATI Mobility Radeon)?

---

### Post by lidex on 2010-01-19
Boot into your LiveCD and choose recovery option or from your grub screen if possible. You'll see a bunch of text and then end up with some repair options. Choose the xserver option and run that. then reboot.

---

