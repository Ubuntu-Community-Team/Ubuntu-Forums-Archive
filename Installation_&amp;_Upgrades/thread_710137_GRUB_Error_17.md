---
title: "GRUB: Error 17"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by tomihasa on 2008-02-28
I have been installing Linux to my machines, and now I'm trying to install Xubuntu 7.10 to my old tailored computer, including MaxPoint Miditower ATX, ABIT KT7A100 KT 133A Socket A RAID motherboard, AMD K7 1400 MHz Thunderbird processor, 768 MB SDRAM memory, and Seagate Barracuda 40.8 GB IDE hard drive.

After installing Xubuntu, I get the usual:

```

Verifying DMI Pool Data .............
Boot from ATAPI CD-ROM :

```

And then:

```

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17

```

Any suggestions?

---

### Post by Pumalite on 2008-02-28
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by dstew on 2008-02-28
This error means grub is not installed correctly. There can be lots of reasons for this, but it should be easy to fix. Do you have a Live CD, or alternate install CD?

---

### Post by piotrwoj on 2008-02-28
1) [http://beta.sysresccd.org/systemrescuecd-x86-1.0.0-rc2.iso](http://beta.sysresccd.org/systemrescuecd-x86-1.0.0-rc2.iso)
2) mount disk, chroot to installed system and:
mount --bind /proc /chroot/proc
mount --bind /dev /chroot/dev
mount -t devpts none /chroot/dev/pts
chroot /mnt/chroot /bin/bash
repair

---

