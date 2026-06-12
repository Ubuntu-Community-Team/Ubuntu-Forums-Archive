---
title: "Ubuntu install freezes at 90%"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Haluci on 2007-11-16
I just recently tried to install Ubuntu on an empty partition.  When I started the install, I told the installer to install the bootloader onto the ext3 partition that Ubuntu was going to create.  The install went just fine until it reached 90% (this being the part where it "detects hardware"), where it completely froze.  So, I turned off the computer completely, this being my only option, and turned the computer back on.  Not only did Ubuntu not run (which I expected), my BIOS said that there was no bootable media on my hard disk (which I did not expect).  Guessing that Ubuntu somehow nuked my MBR, I repaired my bootloader with a my Vista DVD and got Vista (but not Ubuntu) to run.

What did I do wrong here?  Is there anything different I need to try to get Ubuntu to install?

System Specs:
Dell Inspiron E1405
Intel Core 2 Duo Processor @ 2.00GHz 2.00GHz
2GB of RAM
...and a bunch of other stuff like my keyboard which I can provide info on if it will help.

---

### Post by Pumalite on 2007-11-16
Graphics? Looks like a bad burn or we'll have to identify what is your hardware problem.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Burn a new CD anyway, but install with Alternate CD. Burn at 4x.
Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

---

### Post by Haluci on 2007-11-16
Video Card :	Mobile Intel(R) 945GM Express Chipset Family

I'll try this again tomorrow with your suggestions and post here again.

---

### Post by Disrupted on 2007-11-17
Hi all,

Personally, I don't think this issue is because of a bad CD burn. I had to boot the Ubuntu CD with the extra boot parameter hpet=disabled. In all fairness, I also have to boot other linux distros (systemrescuecd) with the same parameter otherwise both Ubuntu and systemrescuecd will freeze with the following problem:

PCI: Cannot allocate resource region 1 of device 0000:00:14.0

Now, luckily, online I was able to find that hpet=disabled did allow pretty much every linux LiveCD to boot without problem.

BUT... now the problem is that when I try to do an install from the desktop icon, my system also freezes at the 90% mark when the LiveCD installer is trying to detect hardware devices.

The installer that I launch from the Ubuntu desktop icon doesn't know that I needed to boot with the extra hpet=disabled boot parameter to skip that specific PCI hardware detection routine.

Is there a way to specify hpet-disabled for the desktop installer? If I could do that, I'm pretty sure that the freeze at the 90% would not happen.

Thanks in advance,
~Brad / Disrupted

---

### Post by Haluci on 2007-11-18
That's interesting.  Is it possible to specify that in the alternate CD?

---

### Post by Pumalite on 2007-11-18
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

---

### Post by Haluci on 2007-11-18
never mind.  Once I finally got the alternate iso to not fail the md5 hash (I blame bittorrent) and not fail the CD integrity check (I blame my cd burner), the install worked flawlessly.  Thanks Pumalite.

---

### Post by Pumalite on 2007-11-18
You are welcome. Good luck.

---

