---
title: "New Grub2 issues anyone?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-09-25
After the updates that temporarily "lost" networkmanager, I found that the grub2 boot menu was being generated incorrectly as well.

The main entries are correct, but it appears that "other linux" installs are being read from their own grub (menu.lst) config files; at least one of mine was incorrect, because I had never actually booted from that partition, so that the UUIDs were inconsistent and the (karmic) install failed to boot. I've fixed that.

More worrying is that my (back-stop) Jaunty install is now not being set up in the grub2 menu at all; the only entry in grub.cfg for that partition is the memtest one!

Short of writing a boot stanza for Jaunty into 30_otheros by hand, or waiting for a fix to randomly appear, I'm stuck with karmic for now.

Anyone else having similar issues?

---

### Post by philinux on 2009-09-25
You could run update-grub again to see if that will sort it. There have been a few updates to grub2 and the other os detect bit.

If you need a model jaunty stanza here's what mine looks like from grub.cfg.
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 40558149-061d-43bc-9068-9c34dbdfa6c7
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=40558149-061d-43bc-9068-9c34dbdfa6c7 ro splash vga=792 quiet
	initrd /boot/initrd.img-2.6.28-15-generic
}
```

---

### Post by scradock on 2009-09-25
> **philinux said:**
> You could run update-grub again to see if that will sort it. There have been a few updates to grub2 and the other os detect bit.

If you need a model jaunty stanza here's what mine looks like from grub.cfg.
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 40558149-061d-43bc-9068-9c34dbdfa6c7
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=40558149-061d-43bc-9068-9c34dbdfa6c7 ro splash vga=792 quiet
	initrd /boot/initrd.img-2.6.28-15-generic
}
```

Thanks a lot - that (putting the stanza into 30_otheros) fixed it! Now I have access to Jaunty again.....  Re-running update-grub did no good by itself - the detection us still failing to generate the correct menuentry.

---

### Post by philinux on 2009-09-25
Ok good one.

My setup is like this.

Jaunty on sda with grub legacy on the mbr.

Karmic on sdb with grub2 but install on sdb1 not the mbr. 

So when my machine starts up I get grub legacy and I chainload into karmics grub. However update-grub works fine from karmic.

God knows this is going to be a headache when I install karmic realease onto sda and then lucid onto sdb.

---

### Post by hardawayd on 2009-09-25
i have karmic and moblin 2.1 installed but can not figure out how to modify grub.cfg to let me boot moblin 2.1 ----any ideas?

---

### Post by rburkartjo on 2009-09-25
not on my end

---

### Post by todak on 2009-09-25
Check to see of you have os-prober installed.

---

### Post by Gina on 2009-09-25
Seems a lot needs sorting out before release - I can't get Karmic plus Jaunty and other systems to multi-boot.  Alright without Karmic (and grub 2).  Since I need my Jaunty setup I have had to leave Karmic for the present :(  ATM I do not have a spare machine available just for testing.  This is the first time in several years of testing that I haven't had multi-boot available with the test version.

---

### Post by Slug71 on 2009-09-25
> **Gina said:**
> Seems a lot needs sorting out before release - I can't get Karmic plus Jaunty and other systems to multi-boot.  Alright without Karmic (and grub 2).  Since I need my Jaunty setup I have had to leave Karmic for the present :(  ATM I do not have a spare machine available just for testing.  This is the first time in several years of testing that I haven't had multi-boot available with the test version.

Has Karmic Ubuntu and Kubuntu working fine as well as ReactOS. :confused:

---

### Post by philinux on 2009-09-25
> **Gina said:**
> Seems a lot needs sorting out before release - I can't get Karmic plus Jaunty and other systems to multi-boot.  Alright without Karmic (and grub 2).  Since I need my Jaunty setup I have had to leave Karmic for the present :(  ATM I do not have a spare machine available just for testing.  This is the first time in several years of testing that I haven't had multi-boot available with the test version.

The trick is to install grub2 to karmics root partition and not the mbr.
Then chainload from Jaunty.

---

### Post by Gina on 2009-09-25
> **philinux said:**
> The trick is to install grub2 to karmics root partition and not the mbr.
Then chainload from Jaunty.Thank you, I'll give that a try :)

---

### Post by prattmd on 2009-09-25
I cannot get grub 2 to recognize moblin or F12.
how can I put legacy grub back on the MBR and grub 2 on the karmix partition?

---

### Post by prattmd on 2009-09-25
This just solved my problem:
> $ sudo apt-get install --reinstall libdebian-installer4
$ sudo os-prober
$ sudo update-grub

---

### Post by scradock on 2009-09-25
> **Gina said:**
> Seems a lot needs sorting out before release - I can't get Karmic plus Jaunty and other systems to multi-boot.  Alright without Karmic (and grub 2).  Since I need my Jaunty setup I have had to leave Karmic for the present :(  ATM I do not have a spare machine available just for testing.  This is the first time in several years of testing that I haven't had multi-boot available with the test version.
Gina - that should work. I have (2 different) 64-bit karmic installs each in its own primary partition (sda3 and sda4), one of which uses grub2 and is in charge of booting. Until the last couple of days there has been no difficulty choosing WinXP on sda1 or Jaunty on sda5 (logical partition inside extended sda2). One drive, laptop.

---

### Post by PRGUY85 on 2009-09-25
I know its offtopic, but how can you get Grub2 to display options to boot on console?

---

