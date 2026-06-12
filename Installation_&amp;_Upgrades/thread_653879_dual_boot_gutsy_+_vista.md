---
title: "dual boot: gutsy + vista"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by kaiwan on 2007-12-30
Hi! 
I had Gutsy and XP working great. I am wondering is it the same procedure with vista, that is:
- install vista
- make partition for gutsy
- install gutsy
- gutsy adds vista automatically in grub menu

---

### Post by ajgreeny on 2007-12-30
More or less, though I think you need to make space with Vista's own partitioning software rather than the ubuntu gparted.  If neither is installed at the moment it is probably easiest to make the partitions the sizes you want first and then install Vista and then ubuntu in the pre-made partitions.  Ubuntu and grub will normally find Vista as it did XP, and add it to the menu.lst file.

---

### Post by wagoner on 2007-12-30
Grub will not boot vista, so you cannot intall grub to the mbr like you would with xp.  I would

- intall vista leaving disk space for gutsy
- use remaining disk space to make partition for gutsy
- intall gutsy and put grub on the root partition (/dev/sda2 or whatever)
- chainload grub from the vista bootloader.

Vista doesn't use boot.ini like XP does.  You will need to use bcdedit to add an entry for grub on the root partition on gutsy.  Here are some instructions to use bcdedit:

[http://www.thorsten-lux.de/files/wiki.html](http://www.thorsten-lux.de/files/wiki.html)

---

### Post by logos34 on 2007-12-30
> **wagoner said:**
> Grub will not boot vista, so you cannot intall grub to the mbr like you would with xp.

Wrong.  

Grub will **sometimes** not boot Vista.

So I would do what ajgreeny suggested and install vista on a premade partition, then install gutsy on the remaining space.  If by chance you do hae problems booting vista with grub, THEN restore vista boot loader to mbr and go the easybcd route.

---

### Post by kaiwan on 2007-12-31
why will grub not recognize vista sometimes?

---

### Post by logos34 on 2007-12-31
> **kaiwan said:**
> why will grub not recognize vista sometimes?

Not sure about the details.  It varies.  Most have success using grub.  [Read this]("https://help.ubuntu.com/community/WindowsDualBoot") or [this]("http://www.linuxjournal.com/article/4622#comment-268023")

---

### Post by wagoner on 2007-12-31
Ok, so maybe it doesn't happen all the time.

However, I think it is misleading for the distros to distribute install disks that will resize ntfs partitions and overwrite the mbr without any warning.  It seems that there are a lot of unsuspecting noobs out there that get caught in this trap.  Perhaps this was a good idea with older versions of windows, but it shouldn't be done with vista.  I'm a bit of a noob myself, so it's just my opinion.:)

---

### Post by logos34 on 2007-12-31
> **wagoner said:**
> Ok, so maybe it doesn't happen all the time.

Not even most of the time.  Most of the time grub works with vista.  But it fails enough times to qualify as an 'issue'.

> However, I think it is misleading for the distros to distribute install disks that will resize ntfs partitions and overwrite the mbr without any warning.  It seems that there are a lot of unsuspecting noobs out there that get caught in this trap.  Perhaps this was a good idea with older versions of windows, but it shouldn't be done with vista.  I'm a bit of a noob myself, so it's just my opinion.:)

I agree that newcomers to linux ought to be given more of a 'heads up' about potential grub problems with Vista, and particularly the need to resize Vista with the latter's disk manager rather than with gparted  on the ubuntu install cd.  Vista has been out barely a year, and while one could excuse the Feisty release (April) for lacking any mention of conflicts (it was well into development before vista debut), by the time of Gutsy there should have been some mention of it. I doubt many people read the community documentation main page before installing.

---

