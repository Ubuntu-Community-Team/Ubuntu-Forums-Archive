---
title: "GRUB question - IDE &amp; 2 SATA"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by nolfclvr on 2007-07-19
Hello all,

New to Ubuntu, and been a long time since I've been on linux at all..

I have 2 NTFS SATA drives, /dev/sda (XP) and /dev/sdb (storage),  and an IDE drive with Ubuntu /dev/hda

I'm unsure how to configure my grub so that it will show XP along with my linux

this is what i have currently
```
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

Now, I basically stole that from another post, because it seemed to be what I was looking for, but my XP wont boot, help please!

thanks

---

### Post by dabl on 2007-07-19
Qqmike to the rescue!

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by nolfclvr on 2007-07-19
I've actually been looking at that... but can't apply it to my situation :(

---

### Post by dabl on 2007-07-19
Well, I'm not sure how you're partitioned, or whereyour Windows boot partition is, but here's a real working example where I have 3 Linux OSs and Windows XP, all available in the boot menu.  This is on 1 IDE + 2 SATA drives, with Win XP installed in on "hd1" as it's called in Grub (the first SATA drive).  Ubuntu is on hd2 (the second SATA drive), Kubuntu is on hd1, second partition, and E-live is on hd0 (the IDE drive). Note that WinXP needs re-mapped by chainloader:


## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-lowlatency
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=5c75276d-48e9-4705-a19c-94210edf8c2a ro quiet splash vga=788
initrd		/boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=5c75276d-48e9-4705-a19c-94210edf8c2a ro single
initrd		/boot/initrd.img-2.6.20-16-lowlatency

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Kubuntu, kernel 2.6.20-16-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=84445218-c1c0-41fc-9616-2c92a5a348d5 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

title		Kubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=84445218-c1c0-41fc-9616-2c92a5a348d5 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Elive Revolution rl2+ (unstable) kernel 2.6.18-elive (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-elive root=/dev/hda1 vga=791 splash=silent 
initrd		/boot/initrd.img-2.6.18-elive
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by nolfclvr on 2007-07-19
Well, this time when I selected windows xp, it sais "Starting up..."

but froze, haha

---

### Post by dabl on 2007-07-19
Well, Windows broken -- there's a shocker!  (not .......)  :)

---

### Post by nolfclvr on 2007-07-21
Windows works fine, I just have to change the boot order to boot my SATA drive before my IDE

---

### Post by confused57 on 2007-07-21
Open a terminal and post the output of:
```
gedit /boot/grub/device.map
sudo fdisk -l
```
the -l is a lowercase "L"

If your XP drive is (hd2), you could try:
```
title		Microsoft Windows XP Professional
map (hd0) (hd2)
map (hd2) (hd0)
rootnoverify (hd2,0)
savedefault
chainloader	+1
```

---

### Post by nolfclvr on 2007-07-21
Thanks, I'll give it a go next time I boot into ubuntu

---

