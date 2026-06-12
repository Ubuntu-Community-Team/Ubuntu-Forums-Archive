---
title: "Grub, WindowsXP, &quot;/boot/grub/stage1 not read correctly&quot;"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by firepol on 2007-03-12
Hi,

I had a windows XP Home (frist partition, primary) and 10 GB unpartitioned space (I left it on purpose) and I decided to install ubuntu on my laptop.

At the installation I didn't notice that it recognized my windows partition as recognized as /dev/hda2... no problem, ubuntu was installed correctly but just /media/hda2 had nothing to browse.

my partition table now is as follows:

/dev/hda1 = Windows (NTFS), 30 GB * boot flag
/dev/hda2 = Ubuntu (ext3 partition), 8.6 GB
/dev/hda3 = Swap, 1.4 GB

Note: as you an see I'm not using a separate partition for /boot. But this shouldn't be a problem as I've already used this configuration elsewhere without problems.

I tried to boot "Microsoft Windows XP Home" (added by the ubuntu installer in my grub menu list) and it didn't work: it complained that the file hal.dll was not found in \windows\system32... but the file was there. So, after trying several boot cds and recovery systems and using the windows console to rewrite the MBR by running fixmbr I got my windows working again. And I have to say, it was a PITA. i don't know how it got fixed but at the end it booted.

But now I no more have a grub menu. Ok... this happened several times in other situations (I have several linux boxes) and my solution to solve this was always to boot my pc with SystemRescueCd (you can download and try it at [http://www.sysresccd.org)](http://www.sysresccd.org)). Then run the following commands:

```

mkdir /mnt/ubuntu
mount /dev/hda2 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
chroot /mnt/ubuntu /bin/bash
vi /etc/fstab (some modifications if necessary)
vi /boot/grub/menu.lst (and i do some modifications/corrections if necessary)
grub-install /dev/hda

```

But this time the solution didn't work. I got this error after running grub-install /dev/hda:

The file /boot/grub/stage1 not read correctly

But the file is there!

I corrected (see m partitino table above) my /boot/grub/menu.lst file:

the ubuntu entries had root(0,0)
I corrected them to root(0,1)

Windows had root(0,1) and I corrected it to root(0,0).

I runned grub-install /dev/hda and still the same error message.

My ubuntu partition is there. Grub doesn't want to install. Why? Can you help please? I do not want to re-install the whole ubuntu, I just want to fix the MBR by writing grub there.

Please give me useful suggestions and don't tell me to re-install ubuntu. re-installing ubuntu is not an option when the problem is just GRUB.

Thanks in advance to help me to solve this mystery...

---

### Post by zvacet on 2007-03-12
[http://ubuntuforums.org/showthread.php?t=382288]("http://ubuntuforums.org/showthread.php?t=382288")

---

### Post by confused57 on 2007-03-12
The live cd is probably the easiest way to install grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Does "sudo fdisk -l" show Windows on /dev/hda2?

---

### Post by firepol on 2007-03-13
thank you confused57,

your link helped me to solve the problem. I will try to install grub the same way using sysresccd when I'll have time ;)

thanks again!

SOLVED


EDIT 18 May 2007: it works also with SysRescCD: [http://sysresccd.org](http://sysresccd.org) (sysresccd is a recovery cd, very fast boot, faster than the ubuntu live cd and faster than a knoppix)

---

