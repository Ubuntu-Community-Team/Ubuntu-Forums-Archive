---
title: "External HDD to Internal HDD Migration"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by SpiderGorilla on 2008-02-08
Okay, so I know my sitch is just a little bit unique. I currently run a newer Dell Inspiron 530 with an internal 250GB SATA drive and an AMD64 processor. Except it's really an Intel64 processor, but that's neither here nor there.

I also currently run an external HDD which houses my Linux partition. I've been using Ubuntu 7.10 for about two weeks solid without booting into Windows. In fact, I'm only emulating three programs from Windows via Wine, because I basically use Linux software on my PC anyway.

So after having finally determined that there's not a blessed thing I honestly use Windows for anymore, and knowing that I'm knowledgeable enough with Linux to keep myself afloat anymore, I was wanting to go ahead and install Linux on the internal HDD.

Here's the rub: I love how I have Ubuntu configured on my external HDD already. I really, really don't want to go through the pain in the *** that is getting this system to run (tablet, scanner, flash 9 plugin, compiz-fusion, they're all not exactly easy to install) all over again. Is there any way I can transfer the whole of my external Linux partition to another partition and have it Just Work(tm)?

Also, do I need to install LILO or GRUB on the MBR if I've got an entire disk devoted to the OS?

---

### Post by logos34 on 2008-02-09
You can use Gparted Live CD to format the internal and copy the ubuntu partition.  The UUID will remain the same.  Make a new swap.  Edit fstab and menu.lst, and reinstall grub to internal drive MBR if necessary.

Or use the **dd** command.  Or **cp -a**

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
(-->'Copying a partition')
[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

---

### Post by SpiderGorilla on 2008-02-09
Those are great links. Now I have to figure out why the Vista volume is locked. Even launching via Terminal using sudo gparted doesn't allow me to delete the partition.

Heh. Trust Microsoft to figure out a way to lock the Vista partition from being erased by Linux. Or is it Linux trying to keep silly Windows users from accidentally deleting their Vista partition? Hard to say.

Any ideas?

---

### Post by logos34 on 2008-02-10
> **SpiderGorilla said:**
> Those are great links. Now I have to figure out why the Vista volume is locked.

It's mounted--needs to unmounted.  Right-click on it>unmount

---

### Post by SpiderGorilla on 2008-02-10
Ah! Well then, don't I feel stupid? Yes. Yes I do.

---

