---
title: "Windows wont play nice"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by warmnscsi on 2010-01-09
Hello, I just got done installing ubuntu 9.1 on my netbook asus 1005ha. I've installed ubuntu before but this time I was feeling adventurous and decided to install the boot loader on the same partition as ubuntu. My idea was that I could hit f9 while windows was starting up to bring up the windows boot loader and start ubuntu from there. Well of course that didn't work (what was I thinking?) So now I don't know how to boot ubuntu or if it is even possible at this point. If it is possible please let me know how I can get it working. I spent all night configuring windows 7 just the way I like it and I would hate to do anything to mess it up. Thanks.

---

### Post by adam814 on 2010-01-09
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

That should explain how to re-install grub2 on the MBR of the disk (where it should be).

---

### Post by raymondh on 2010-01-09
googling around brought this up.

[http://thpc.info/dual/vista/dualboot_vista+ubuntu804_bcd_on_vista.html#easy](http://thpc.info/dual/vista/dualboot_vista+ubuntu804_bcd_on_vista.html#easy)

Though I have installed bootloaders in partitions (instead of the MBR), I have no experience with easeyBCD and windows.

I am a fan of GRUB.  I prefer to use it (GRUB) as the MBR bootloader and segue it to 'other' boot files/loaders.

Good luck .... back-up.

Raymond

---

### Post by warmnscsi on 2010-01-09
Thanks everyone, I appreciate the help. I like knowing I always have a place with quick accurate and courteous answers to my many questions :D

I ended up erasing the partition and reinstalling to make it easy on myself and everything works fine now. On a second note,

does anyone know of any good free software to make an exact image of my windows partition and/or ubuntu partition?

---

### Post by darkod on 2010-01-09
> **warmnscsi said:**
> Thanks everyone, I appreciate the help. I like knowing I always have a place with quick accurate and courteous answers to my many questions :D

I ended up erasing the partition and reinstalling to make it easy on myself and everything works fine now. On a second note,

does anyone know of any good free software to make an exact image of my windows partition and/or ubuntu partition?

Take a look at clonezilla at [www.clonezilla.org](www.clonezilla.org). Haven't used it yet but it recognizes ntfs, ext4, ext3, etc, everything you need.

---

### Post by adam814 on 2010-01-09
If you're not afraid of the command line you could use "dd".  It's a pretty standard *nix utility for doing just that.  If you pipe it through gzip it's not so inefficient on space.

It would work more or less like this assuming /dev/sda1 was the partition you wanted to clone and you wanted a backup in your home directory:
```
sudo dd if=/dev/sda1 bs=1M | gzip -c9 > ~/sda1backup.img.gz
```You could adapt that to suit your needs.  The man pages for dd and gzip are helpful as well.

---

### Post by warmnscsi on 2010-01-10
> **darkod said:**
> Take a look at clonezilla at [www.clonezilla.org]("http://www.clonezilla.org"). Haven't used it yet but it recognizes ntfs, ext4, ext3, etc, everything you need.

Thanks I'll give that a try.

> **adam814 said:**
> If you're not afraid of the command line you could use "dd".  It's a pretty standard *nix utility for doing just that.  If you pipe it through gzip it's not so inefficient on space.

It would work more or less like this assuming /dev/sda1 was the partition you wanted to clone and you wanted a backup in your home directory:
```
sudo dd if=/dev/sda1 bs=1M | gzip -c9 > ~/sda1backup.img.gz
```You could adapt that to suit your needs.  The man pages for dd and gzip are helpful as well.

Thank you as well. I'm a little afraid of terminal. I've been using basic commands for a while now and I'm always looking to expand my skills. I'll definitely give that a shot and see what happens.

---

