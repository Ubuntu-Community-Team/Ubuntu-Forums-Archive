---
title: "Grub doesn't find my first disk after new install"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by Snapcase on 2013-01-18
I just installed the KXStudio 12.04 iso in a second HD. I previously had a dual boot disk with two booting partitions for Win XP and Kubuntu 12.10. These two don't show anymore in the Grub menu after the install. It only boots in KXS.

I'm pretty new to Linux, Don't know where to start.

Thanks in advance.

---

### Post by grahammechanical on 2013-01-18
When you installed KXstudio onto the second hard disk did you have the first hard disk connected?

If you did not then the Grub boot loader from KXstudio does not know about the other hard disk.

In a terminal in KXstudio run

```
sudo update-grub
```

and paste a copy of the output from that command. Does it list XP and Kubuntu (may be as 12.10 on sda)?

If it finds these 2 other OS, then see what happens when you reboot. Remember, the Grub boot loader from KXstudio is now in control of the boot process. If you want the Grub from Kubuntu to be in control ( you might at some time in the future remove the second hard disk and be unable to boot), you should

1) Boot into Kubuntu.
2) run

```
sudo update-grub
```

3) run

```
sudo grub-install /dev/sda
```

If the XP/Kubuntu hard disk is the first hard disk.

Regards.

---

### Post by Snapcase on 2013-01-18
Yes, both disks were connected. Here is the output. They don't show.

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-lowlatency
Found initrd image: /boot/initrd.img-3.2.0-35-lowlatency
Found memtest86+ image: /boot/memtest86+.bin
Found KXStudio 12.04.1 (12.04) on /dev/sda1
```

So... the former first disk is now /dev/sdb?

---

### Post by Snapcase on 2013-01-18
According to Gparted they're the opposite as listed by Grub. KXStudio is on /dev/sdb and Win and Kubuntu on /deb/sda...

---

### Post by darkod on 2013-01-18
I suggest to keep grub2 from kubuntu on the MBR, not the grub2 from kxstudio. I am not sure which version of grub it uses, although from what you posted looks like grub2 too.

You should have used the manual install and selected the kxstudio disk for bootloader destination. That would have left the first disk alone with it's bootloader intact.

Did you run that update-grub from kxstudio? If you did, the output is strange, since the /boot/vmlinuz reported is usually the running OS. So, if /boot/vmlinuz is the running kxstudio, then what is the last line it reports?

I suggest you run boot-repair to create bootinfo which has more details and post the link it gives you. You may also run the recommended repair if you want to, but in your place I would create the bootinfo first so that you know what is the problem. Even if the recommended repair fixes it, you still have to know what it was. At least that's my approach...

Depending what the bootinfo says, you can consider installing grub2 from kubuntu on the MBR of /dev/sda (or /dev/sdb depending on which disk it is). You can do that with the kubuntu cd.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Snapcase on 2013-01-18
It's not Grub. It's me.... I just screwed it all up. I intalled KXStudio in the wrong disk. So long XP and Kubuntu...

Tip: Don't ever try to install an OS late at night if so tired and sleepy after a long hard day because you are too eager. You may want to kill yourself afterwards. Just like me.... Thankfully I have backups of most of it.

---

### Post by darkod on 2013-01-18
You may be able to recover the partitions with testdisk since most of the data is not overwritten yet. If you want to try:
[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You need to do it from live mode of course.

---

### Post by Snapcase on 2013-01-18
Thanks so much. I'll try that, though I don't have much faith,,,

---

