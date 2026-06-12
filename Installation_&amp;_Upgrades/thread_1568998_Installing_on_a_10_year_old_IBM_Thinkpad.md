---
title: "Installing on a 10 year old IBM Thinkpad"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by cthulhu_54 on 2010-09-06
Hi!
I'm trying to install Linux on my 10 year old IBM Thinkpad 600E, 32 Mb RAM, 400 MHz. I replaced the wrecked 10 GB HD with a known-to-be-working 40 GB HD, and popped in the Arch install CD, and this is how far I got:
(The CD works on other computers)

[IMG]http://img444.imageshack.us/img444/4083/dsc5933.jpg[/IMG]

Now, I don't have a clue as to what the problem could be? Is it telling me it can't find the Hard Drive? What gives?

---

### Post by mörgæs on 2010-09-06
With 32 MB you will not have a chance of running Ubuntu or Arch, sorry.

---

### Post by cthulhu_54 on 2010-09-06
Yeah, Ubuntu is out, but I'm pretty sure I can run Arch Linux. I actually managed to start (from yet another hard drive) Debian stable (Lenny), with full Xorg (with Fluxbox) and Emacs22 running at 28 Mb Ram usage. Not that bad in my opinion.

Then I tried booting from the working 40 GB drive, where I also have Fluxbox, but the load of Wicd, gnome power manager, etc made the boot time 18 minutes, rather than 2-5 minutes. Once it was done it had Swaped 40 Mb.

---

### Post by K.Mandla on 2010-09-08
Arch will run on 32Mb; recent versions of Ubuntu will not. If you're willing to skip back even as far as 6.06, you can use Ubuntu on a machine with those specs. 

The early Thinkpads had/have a small inconsistency when booting from the CD. Try downloading an earlier ISO and installing from that. I used to have a Thinkpad A21E that likewise couldn't boot from some Arch ISOs, but older versions worked fine.

And it will update itself without a hitch. Or it should. ;)

---

### Post by cthulhu_54 on 2010-09-08
Thanks a lot!
I'll try it out. (If I can find an older iso, or perhaps a floppy image)

---

### Post by oldos2er on 2010-09-08
According to [http://wiki.archlinux.org/index.php/Beginners_Guide#Step_2:_Boot_Arch_Linux_Installer](http://wiki.archlinux.org/index.php/Beginners_Guide#Step_2:_Boot_Arch_Linux_Installer) minimum RAM for a basic install is 128MB.

---

### Post by tgalati4 on 2010-09-08
Yea, you can cheat a little.  If you put a 128 or 256 MB swap partition, you can get away with 128 MB of RAM and boot the Live CD and even install.  It will run slow.  If you want something to muck with, try slitaz.

[http://slitaz.org](http://slitaz.org)

---

### Post by K.Mandla on 2010-09-08
> **oldos2er said:**
> According to [http://wiki.archlinux.org/index.php/Beginners_Guide#Step_2:_Boot_Arch_Linux_Installer](http://wiki.archlinux.org/index.php/Beginners_Guide#Step_2:_Boot_Arch_Linux_Installer) minimum RAM for a basic install is 128MB.
This is true, and yet ...

[http://kmandla.wordpress.com/2010/05/28/fbterm-birth-of-the-cool-for-the-console/](http://kmandla.wordpress.com/2010/05/28/fbterm-birth-of-the-cool-for-the-console/)

You can get it installed with much less than what is recommended, and come up with some fantastic setups. ;)

---

### Post by oldos2er on 2010-09-08
Thanks for the info.

---

