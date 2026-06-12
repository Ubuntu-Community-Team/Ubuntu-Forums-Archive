---
title: "On a Ubuntu/XP/Vista computer, grub won't boot vista."
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by szabozap on 2007-12-24
So I need to use 3 OS's on the same computer, two hard drives, grub to choose between. Not a huge deal. 

I first installed Vista on an IDE drive (hda), then unplugged it as I didn't want to accidentally install grub on that drive.

I use the XP installer to divide my other, SATA drive (sda) into 3 partitions: one for XP, one for Ubuntu, and one large one to act as storage. That goes fine too, I install grub and I can boot to either XP or Ubuntu. 

The problem comes when I try to add the Vista drive to the menu.lst. I added the entry and pointed it to (hd1) instead of (hd0), but whenever I try and boot to that entry, it boots to XP instead of vista. Any idea how I can tell grub to boot to vista in this case?

Here's my menu.lst:
```
default		saved
timeout		3

title		Windows Vista
rootnoverify	(hd1,0)
makeactive
savedefault
chainloader	+1

title		Windows XP
rootnoverify	(hd0,0)
makeactive
savedefault
chainloader	+1

title		Ubuntu
root		(hd0,4)
savedefault
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8bb5af3d-2dd8-458a-85b6-01b33cf0ec87 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8bb5af3d-2dd8-458a-85b6-01b33cf0ec87 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
```

I read online that I perhaps needed to add
```
map (hd0) (hd1)
map (hd1) (hd0)
```
to the Vista entry, but when I do that grub just hangs on "Starting up...".

Any ideas?

---

### Post by Pumalite on 2007-12-24
Mapping is a good idea. Do that and report back.

---

### Post by benrboone on 2007-12-24
i second the map idea, have used many times when switching hardrives

---

### Post by szabozap on 2007-12-24
Just tried it-- grub just hangs on "Starting up..."

I'm thinking this is the problem: Tried to do a fdisk -l on the vista drive and it spits out "Disk /dev/hda doesn't contain a valid partition table." That would cause problems with grub booting to vista, right?

I can still mount the vista partition in Ubuntu, though.

edit: So any idea how I can get around the broken partition table? =/

---

### Post by Pumalite on 2007-12-24
You can try:
TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by szabozap on 2007-12-24
Argh, I suck, turns out I was scanning the CD drive and not the other hard drive. Partition table was fine. 

So we're back to grub.. I added the two map lines to no avail: now when I select the Vista option it just gives me "Starting up ..." with a blinking cursor beneath that and hangs. Ideas?

---

### Post by Pumalite on 2007-12-24
You should reinstall Ubuntu with all drives connected and let Grub install to MBR.

---

### Post by meierfra on 2007-12-24
post the output of

```
sudo fdisk -l
```

---

### Post by meierfra on 2007-12-24
When you installed Vista, was the sda drive plugged in?  And was Windows already installed on the sda drive?  Were you able  to boot Vista before you installed Ubuntu?  What happens when you boot from the IDE drive?

---

### Post by AnonCat on 2007-12-24
I use a free Vista bootloader manager called EasyBCD to handle grub.  You basically install grub to your linux partition then use EasyBCD to detect it.  Has always worked flawlessly for me and doesn't require any editing of Grub's config files.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by meierfra on 2007-12-24
> You should reinstall Ubuntu with all drives connected and let Grub install to MBR.

I wouldn't recommend this at this stage. The Ubuntu installer does not handle a mixtures of SATA and IDE drives very well.  And I think  your  problem is caused by the Vista-XP interaction and not  by Grub/Ubuntu.


> use a free Vista bootloader manager called EasyBCD to handle grub.

EasyBCD usually does a good job and you may give it a try.


I'm only afraid that when you installed Vista, it put  some of its boot information onto the SATA  drive. Windows usually puts  the boot information onto  a primary partition of the first hard  drive. This booting information might have gotten erased when you partitioned the SATA drive.  Could you describe exactly what was on the SATA drive before you installed VISA and what you did to the SATA drive after you installed Vista?

Also what is   the boot order in the bios? Did you, at anytime during the installation process, change the boot order in the bios?

Sorry for all the questions, but I like to know what is going on before making any recommendations. Having three operating  systems on a SATA and IDE drive can lead to all kinds of complications.

---

