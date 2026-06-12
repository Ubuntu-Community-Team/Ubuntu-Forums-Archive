---
title: "GRUB seems to not work properly, what to do?"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by coral on 2007-01-20
I finally reinstalled Ubuntu after a time of Windows and it had made Really Major success since i checked in for 1,5 years ago. (but what to expect really)

One thing though, that hasn't improved is the dualboot situation.

I have four drives in my computer. One SATA disk, Two IDE on same channel, And one IDE on another channel. The Ubuntu installator however did configure GRUB quite wrong. Setting the linux disk to hd(2,0) when it really should been hd(0,0). This is where the problem is, i managed to boot Ubuntu and change the menu.ls so ubuntu always boot. But windows... I have tried changing the hd for windows to(hd0,0) (hd1,0) hd(2,0) and hd(3,0). It doesn't boot.

I just get a black screen with:
Starting Up
_ <- Blinking

You might say: Well throw windows away then, it's useless.
However: I have a quite lot of programs running there that i need to use daily. I can make it with another computer, but the best would if i got this running.

I tried the Super Grub Disk (or at least so much that felt necessary) and no success there really. Last time i had this problem i installed LILO instead, however... It was more then 2 years ago i had that problem and when that problem appeared there still was Graphical installer for LILO (doesn't seem to exist in newer versions, even if LILO is outdated it seems to work). Is this an option to use LILO or shall i try to get GRUB running against all odds?

Or, have my Windows installation finally put itself to a lifetime rest, waiting for the new one to appear.. Or am i just quite incompetent in my thing?.

You have to excuse me for my English, and have mercy om my spelling mistakes. I am from Sweden.

/Jonta

Computer:
P4 3.4 Ghz (clocked to 3.6)
4 Hdd
1 x 160 gb (IDE)
1 x 250 gb (IDE)
1 x 300 gb (SATA)
1 x 60 gb (IDE)
1024 mb ram
Ati X600 256 mb ViVo

---

### Post by coral on 2007-01-20
For more insight in my drives the sudo fdisk -l

Disk /dev/sda: 300,0 GB, 300090728448 byte
255 huvuden, 63 sektorer/spår, 36483 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1       36482   293041633+   7  HPFS/NTFS

Disk /dev/hde: 251,0 GB, 251000193024 byte
255 huvuden, 63 sektorer/spår, 30515 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hde1   *           1       30514   245103673+   7  HPFS/NTFS

Disk /dev/hdf: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hdf1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdg: 60,0 GB, 60022480896 byte
255 huvuden, 63 sektorer/spår, 7297 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hdg1   *           1        6997    56203371   83  Linux
/dev/hdg2            6998        7297     2409750    5  Utökad
/dev/hdg5            6998        7297     2409718+  82  Linux växling / Solaris

Disk /dev/sdc: 1015 MB, 1015808000 byte
32 huvuden, 61 sektorer/spår, 1016 cylindrar
Enheter = cylindrar av 1952 · 512 = 999424 byte

---

### Post by hal10000 on 2007-01-20
with the partitionig program you should remove the boot flags from your linux partition (and best to remove it from all partitions where it is not necessary)
May be you should only leave the boot flag on the partition where your windows starts from.

In which of your partitions /disks is windows installed?
Accordong to you fdisk command, grub did set the linux partition (hd2,0) correct.

Please post the contents of your /boot/grub/menu.lst and /etc/fstab files.

sudo grub

---

### Post by coral on 2007-01-20
How do i access the partition program from ubuntu directly?

Disk /dev/hde: 251,0 GB, 251000193024 byte
That is my windows drive.

menu.lst =
"
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdg1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdg1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1
"

fstab:
"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdg1
UUID=c42c47ac-48c2-4209-af1e-985adde0382e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdg5
UUID=b372539d-7085-4de3-8b7d-7e4f9397db4f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
"

---

### Post by hal10000 on 2007-01-20
Access to the partition program: type simutaneously <ALT>+<F2>, then type in [COLOR="Red"]gksudo gparted[/COLOR] You will be asked for your password.

Leave the "boot" flag only for /dev/hde1
I don't know exactly where to find the option to unset or set the boot flag, so you might have to search a little bit.

I'm somehow confused. Why do you think your linux partition is (hd0,0)? It is not.
As linux is installed to your third harddrive in the first partition, your /boot/grub/menu.lst has to look like:
```

title Ubuntu, kernel 2.6.17-10-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdg1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```
And as your windows is installed on your first harddrive, it has to look like:
```

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

```
Hope this fits.

---

### Post by confused57 on 2007-01-20
What is your hard drive boot order in bios?  The boot order in bios usually sets how grub sees the order of your hard drives...hde, hdf, hdg, etc. just means that's what IDE controller your hard drive is connected to, it wouldn't necessarily equate to hd0, hd1, hd2, etc(which is set by grub according to your bios boot order).
Also, you might want to post the output of:
```
gedit /boot/grub/device.map
```

If your drives are correct as you've reported, you'd need to add a mapping command to your Windows grub entry, here's mine that you might need to edit for your system:

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by coral on 2007-01-20
"I'm somehow confused. Why do you think your linux partition is (hd0,0)? It is not"

Why i think that?. Because i couldn't boot it if i didnt pressed the E key in grub and changed hd(2,0) to hd(0,0). So apparently, grub sees it as hd(0,0)

---

### Post by hal10000 on 2007-01-20
Then you should try what confused57 recommended. 
You MUST first look into your BIOS to verify the settings for the boot order 
Your /boot/grub/menu.lst should then look like:
```

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdg1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```
and for windows i guess you have to fiddle around with the map options, according to your BIOS settings, maybe something like:
```

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```
or 
```

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

```I guess it should be rather the first example than the last one.
you should also look into /boot/grub/device.map and if it don't works post it's content.

Before editing the /boot/grub/ menu.lst and/or /boot/grub/device.map with your editor you should try these settings by typing in "E" on the boot prompt and edit the lines manually. I guess to add the map () () options you have to first type in "A" but I'm not sure about.

---

### Post by coral on 2007-01-21
Problem Solved

A great thanks to all you helping me out
The code i was forced to use was:
```

title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

/coral

---

