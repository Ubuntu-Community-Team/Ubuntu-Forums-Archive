---
title: "Can not install 6.06 in a 250 GB hard disk"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by petoro on 2006-07-15
I've bought a 250 GB hard disk for my 800 Mhz computer.

The BIOS don't recognize the size of this hard disk but Windows XP installs without problems.

I have reserved a 60 GB partition for Ubuntu 6.06.

Ubuntu seems to install well in such partition but, when I boot the computer after the installation I always get a **grub error**  (error 17 if I remember well).

I always have to boot with the XP restore console and make a **fixmbr** to recover Windows.

Is there any way to install Ubuntu in such a partition? a way to make **GRUB** work?


Thanks in advance

---

### Post by firezip on 2006-07-15
Yea I get the same problem...any help?

---

### Post by confused57 on 2006-07-16
Do you have an LBA option in bios?

---

### Post by firezip on 2006-07-16
No I only have "Auto" or "Off". My computer is a Dell Precision 340 with bios A06. Here is my fdisk report

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   307194929   153597433+   7  HPFS/NTFS
/dev/hda2       307194930   308243506      524288+  82  Linux swap / Solaris
/dev/hda3       308255220   488392064    90068422+  83  Linux
ubuntu@ubuntu:~$ sudo grub-install /dev/hda3
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$


```

Any way to fix this?

---

### Post by confused57 on 2006-07-16
I can't find the thread describing how to do it(it's relatively old), but seems the only solution is to create a /boot partition right after the WindowsXP.  Googled and found this:

[http://www.enterprisedt.com/publications/dual_boot.html](http://www.enterprisedt.com/publications/dual_boot.html)

this may give you some idea of how to search further for a solution, I've never done this...but I remember reading about it...maybe use search words  "linux bios large hard drives" or something to that effect.  Sorry I can't help.

Great idea ferebee, that might  be all that's needed.

---

### Post by ferebee on 2006-07-16
Have you checked with Dell to see if there are any updates for your bios that would allow it to recognize your drive? This might not be the problem, but it might be worth checking.

This Gentoo page has a nice list of grub errors and what they mean:[URL="http://www.gentoo.org/doc/en/grub-error-guide.xml"]
http://www.gentoo.org/doc/en/grub-error-guide.xml[/URL]

---

### Post by petoro on 2006-07-16
I have found a solution.

I have an ASUS CUV4X-C motherboard.

With the last stable BIOS release of this motherboard (from 2001) I can not install Ubuntu. The LBA mode of this BIOS only detects 8 GB and this breaks GRUB.

There is a more modern experimental version of the BIOS (from 2002). ASUS says that it is a beta.

I have installed it and everything works perfectly.  The BIOS detects the full 250 GB of the hard disk and Windows, Ubuntu and GRUB install without a problem.

This beta BIOS also mends some additional minor glitches I had.


Good luck,


Petoro

---

