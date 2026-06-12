---
title: "[SOLVED] Installing GRUB on a writable CD"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by Om1977 on 2007-08-13
Hi,

I have a p3 laptop with no primary/internal HDD, I was trying to install Ubuntu 7.04 on an external HDD, but didn't work so used someones computer to install Ubuntu on the external HDD.

Now I have the system installed but no GRUB, the only other option is to install GRUB on a floopy or Writable CD, I can then use my CD drive to boot from.

I do not know how to go about writing or installing the GRUB on a CD .. please help.

OM

---

### Post by logos34 on 2007-08-13
Here you go:
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html)

Just make a small correction: stage2_eltorito is located in

> /lib/grub/i386-pc/stage2_eltorito


> I have a p3 laptop with no primary/internal HDD, I was trying to install Ubuntu 7.04 on an external HDD, but didn't work so used someones computer to install Ubuntu on the external HDD.

Good luck.  Because you may have trouble booting/running ubuntu on your machine unless it's similar to the one you used for install.

---

### Post by Om1977 on 2007-08-13
Hi,

Appreciate your help there.

But is there a possibility then to some how install 7.04 on the external hdd without a primary HDD?

Please advise

OM

---

### Post by confused57 on 2007-08-13
I would suggest you burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It's a very small download(5-7 Mb) & may be able to boot your external hd.

---

### Post by logos34 on 2007-08-13
> **Om1977 said:**
> Hi,

Appreciate your help there.

But is there a possibility then to some how install 7.04 on the external hdd without a primary HDD?

Please advise

OM

I'm not sure to tell you the truth--never encounterd a similar situation. But in theory it should be possible **IF the laptop bios can boot from usb devices**.  This is an older model notebook so that may have been your problem the first time you tried the install (I should have caught that earlier).  If it can boot from usb, you might also try reinstalling Grub to the mbr of that drive so you don't have to use a cd (any number of things could have caused grub-install to fail)

edit: and by all means get supergrub as confused57 just suggested--it's a great little tool.

---

### Post by Om1977 on 2007-08-13
Thank you Confused and Logos .. will try that out .. really appreciate your help :)

---

