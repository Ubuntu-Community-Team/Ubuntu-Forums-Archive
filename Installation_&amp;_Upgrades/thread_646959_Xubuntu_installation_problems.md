---
title: "Xubuntu installation problems"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by Nanday on 2007-12-21
Hello. This is my first post here, although I'm a Ubuntu user now for little more than a year.

I'm trying to install Xubuntu on my girlfriend's quite old PC (a PIII at 800mhz with 300 or so mb of RAM). I downloaded my CD image, burnt it, and tried to boot from it. But I doesn't. :(

Since it is a LiveCD, y boot from it, select the "Install or Run", and I get the splash screen, with that nice Xubuntu logo and the progress bar going back an forward for a while. After that, it switches again to text-mode only, and get some error, like this:
Udevd-event[2114]Run_program_ '/sbin/modprobe' abnormal exit'

Then, it looks like a command line shell, with (initramfs) as the prompt. I'm really puzzled, since I tried the CD in my PC and it worked like a charm, booting into Xubuntu desktop flawless.

Any help here? Thanks.

---

### Post by Pumalite on 2007-12-21
With that RAM, try the Xubuntu Alternate CD. You can boot a Live CD making a 500 MB /swap partition ahead of time.

---

### Post by Nanday on 2007-12-22
Ok, I'm downloading it right now... I'll give it a try as soon as I burn the image. Thanks a lot. :)

P.S.: What's the difference between the standard LiveCD and the alternate?

---

### Post by Pumalite on 2007-12-22
Alternate is text based, but has more control and is easier to install

---

### Post by Nanday on 2007-12-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/178615](https://bugs.launchpad.net/ubuntu/+bug/178615) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello again. I tried too the Kubuntu Live CD, and got the exact error. I'm a bit confused, since Fedora, OpenSUSE and Mandriva LiveCDs worked flawlessly.

I've got the alternate CD just burned, I'll give a try soon.

---

### Post by Pumalite on 2007-12-25
Good Luck.
You should consider this too, since it uses less memory:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Nanday on 2007-12-30
Hello again. I tried yesterday to install Xubuntu from the alternate CD. It didn't work either. It started, slow, but problem-free, until the hardware check. When the progress bar reached 75% (or so), it just freezed there, while detecting Floppy Drives. 

I don't think it is a problem of memory. I tried the LiveCD and the alternate CD on a Pentium II with as little memory as 128Mb and it worked, sluggish, but without significant trouble. 

It's really frustrating... I tried a handful of other distros, and although not every one detected all the hardware (mainly the cablemodem and the sound card), they could show the desktop, and run some problems while on LiveCD mode (even surfing the net or playing music).

Any other idea? I'm considering Fedora instead of Ubuntu... :(

---

### Post by Pumalite on 2007-12-30
It's probably the chipset in your motherboard or integrated graphics. Why don't you make a 500 MB /swap partition and then try Feisty Live CD.

---

