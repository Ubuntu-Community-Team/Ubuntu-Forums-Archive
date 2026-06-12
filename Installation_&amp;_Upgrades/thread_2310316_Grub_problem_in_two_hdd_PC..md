---
title: "Grub problem in two hdd PC."
date: 2016-01-18
forum: Installation &amp; Upgrades
---

### Post by Kanedagr on 2016-01-18
Hi! I have two hdd. In /dev/sda i have windows7 installed and in /dev/sdb i have 2 partitions (home, swap) of Ubuntu 14.04 LTS. Through BIOS I had the machine boot up from sdb (where grub is installed). Some days ago i had a problem with windows and i installed them again. But then, i noticed, in the grub menu list that the Windows option was there but when i pressed didn't work. So in order to boot into windows i had to change through bios and set sda as the first boot device. I have tried boot-repair but didn't work. Boot-repair make the windows 7 choice disappear. Any suggestions? Because now, if I want to boot to Ubuntu i have to set as first boot device the sdb and then if i want to boot into windows i have to change again the first boot device to sda.

---

### Post by grahammechanical on 2016-01-18
The files used to create the Grub boot menu are stored in /boot/grub/ in the partition that Ubuntu is installed in on sdb. When you installed Ubuntu the installation of the grub boot loader detected Windows 7 on sda and created an entry for it.

When you re-installed Windows 7 the entry in Grub became out of date because this was a different Windows 7. Partitions in Linux are identified a unique number. It is most likely that the re-install of Windows included a format & perhaps even a recreation of the partition table. In this way making the partition identification number that Grub has for the Windows partition invalid. Try loading Ubuntu and running

```
sudo update-grub
```

Watch the printout to screen.

Regards.

---

### Post by Kanedagr on 2016-01-18
&#921; will try it and get back! Thank you!

---

### Post by Kanedagr on 2016-01-18
The above command gave me this:
sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

It did the trick! I moved the sda1 loader to the first position and everything is back to normal! Thank you very much for helping me!

---

