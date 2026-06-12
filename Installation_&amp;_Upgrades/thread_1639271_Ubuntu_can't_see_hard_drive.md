---
title: "Ubuntu can't see hard drive"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by kurtcarter on 2010-12-06
Hi there,

I'm a linux newbie hoping to replace Vista on one of my desktop machines. So far the process has been frustrating as I find that Ubuntu doesn't run out of the box on any of my hardware which is fairly standard.

I tried running live CD and also installing it with wubi but I keep running into the same error every time:

"init ramfs  Unable to find a medium containing a live file system

/dev/sda3 does not exist."

Any idea how to fix this? I've looked at other posts but they all require me to run a terminal window once booted up. The problem is it never gets that far.

I do have it running via Virtualbox but I want to actually install it. Will doing a fresh install and using gparted to partition the drive and then install Linux on that solve the problem?

Kurt

---

### Post by CharlesA on 2010-12-06
Does that error occur when you boot off a livecd?

---

### Post by sikander3786 on 2010-12-06
Welcome to the forums :-)

I would first suggest to check the integrity of downloaded image and make sure that is not corrupt.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, burn a new CD at the lowest possible speed (4x recommended).

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Or if your Bios supports, booting from a USB drive is another option.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Let us know about your progress :)

---

