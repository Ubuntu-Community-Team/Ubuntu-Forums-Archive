---
title: "lvm + grub + edgy"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by talkingpidgin on 2007-03-27
When using the alternate install cd to install edgy with lvm, I was not given the option to use the grub boot loader. My /boot directory is within the volume group. Does this make it impossible to use grub?

I tried installing grub after the edgy install and was not very successful.

```
$ sudo grub-install /dev/hda
/dev/mapper/root-root does not have any corresponding BIOS drive.

$ sudo grub-install /dev/mapper/root-root
/dev/mapper/root-root does not have any corresponding BIOS drive.

$ sudo grub-install --root-directory=/dev/mapper/root-root /dev/hda
Usage: ...

```

My setup is two drives hda and hdb that include everything but swap which is the first partition on hda. Google suggest editing /boot/grub/device.map but I'm not sure how this would apply to my setup. As it is...

```

$ cat /boot/grub/device.map
(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/hdb

```

---

### Post by pmocek on 2007-05-08
see also: [Ubuntu Forums: "Alternate CD LVM install"]("http://ubuntuforums.org/showthread.php?t=415433")

---

