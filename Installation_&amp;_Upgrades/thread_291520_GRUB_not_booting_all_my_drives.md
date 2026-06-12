---
title: "GRUB not booting all my drives"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by mga on 2006-11-02
I've got GRUB on my primary IDE partition, and it boots into Ubuntu fine. But there are a couple of problems with my Windows disks:

1) GRUB offers to boot into my IDE Windows install. When I choose this, the screen goes blank and nothing happens. But I can boot the IDE Windows disk successfully by choosing it in the BIOS.

2) GRUB can't see a Windows install I have on a SATA disk, so I'm unable to use that install. My mobo is an Asus A7N8X Deluxe, which uses the SiI3112A SATA driver. I've searched online and it appears that GRUB can support this ... but it isn't happening.

How can I fix these problems?

[Further information: I was able to boot from SATA when I had the Windows bootloader on my IDE primary. It's switching over to GRUB that's caused the problem.]

---

### Post by chriscando on 2006-11-02
Is windows on the first partition? I have had some issues when it is not. I dual boot with windows and this is what part of my grub boot loader looks like:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windoze XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

What does your /boot/grub/menu.lst look like?

---

### Post by bulldog on 2006-11-02
If windows is on your second hdd you have to map the windows entry as follows```
### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by David Corrales on 2006-11-04
I have the same motherboard but my problem is that I just installed Edgy on my SATA drive (which I switched to boot first, before the IDE). I get the following message:
Kernel file not found. Please insert a system disk and reboot.

If I boot using the livecd's "Boot from the first drive" option it loads fine =/

---

### Post by David Corrales on 2006-11-05
I resolved my problem by installing GRUB on the SATA hd, not the IDE one. I probably didn't check at install time =/

---

