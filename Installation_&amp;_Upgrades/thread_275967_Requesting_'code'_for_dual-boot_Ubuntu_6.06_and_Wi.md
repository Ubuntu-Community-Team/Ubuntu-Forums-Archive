---
title: "Requesting 'code' for dual-boot Ubuntu 6.06 and Win XP"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by Giardap on 2006-10-12
Hi,

I have the following configuration on my PC.
Windows XP Home installed on master SATA primary active hard disk (sda)
I then unplugged the SATA disk and cleanly installed Ubuntu 6.06 on a separate PATA drive (hda) - so far so good!
I reconnected the first SATA disk and now I can boot into either OS by choosing the appropriate hard-disk in the BIOS during boot up (not elegant-but practical!)
I did it this way because of many, many previous install attempts where I installed GRUB in the Windows disk MBR and ended up not being able to boot either OS - it's a long story...

I know from reading/forums that there is a file I can edit (/sys/config?) where I can manually add a second batch of text/code to automatically give me the option of booting into either OS at boot from the PATA drive. I presume this file has to do with grub and resides on the PATA drive.

I don't want to mess with the current Windows XP MBR on the SATA drive - I  would like always to be able to select this drive in the BIOS during boot and have it boot into Windows XP.

Given the configuration above can anybody point me to the file to edit and give me the appropriate text. Thanks.

---

### Post by CatKiller on 2006-10-12
I believe that the file is /boot/grub/menu.lst. If you put your XP line within the "Automagic Kernels List" section, then you'll need to redo it every time you upgrade your Linux kernel. So don't do that. According to the comments in my menu.lst, you probably want something like
```
title    Windows XP Home
root    (sd0,0)
makeactive
chainloader    +1
```It might be something slightly different - I've never done it - but that should get you on the right lines.

---

### Post by Giardap on 2006-10-14
OK I have it sorted. The correct entries follow;

The additional code to be added in the menu.lst file after the "end default options" is;

## ## End Default Options ##

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

And the device.map file reads;

(hd0)     /dev/hda
(hd1)     /dev/hdb

I should refer readers to an excellent link on this topic at;

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

It worked for me, and I hope it helps somebody else.

---

### Post by gn2 on 2006-10-14
> **Giardap said:**
> OK I have it sorted. The correct entries follow;

The additional code to be added in the menu.lst file after the "end default options" is;

## ## End Default Options ##

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

And the device.map file reads;

(hd0)     /dev/hda
(hd1)     /dev/hdb

I should refer readers to an excellent link on this topic at;

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

It worked for me, and I hope it helps somebody else.


Just keep Grub out your Windows MBR now and forever...........

---

