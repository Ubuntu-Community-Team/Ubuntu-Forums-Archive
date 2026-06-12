---
title: "Add XP partition to existing Feisty install?"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by mikeize on 2007-09-12
Is this possible?  I was so excited to put Ubuntu on my fresh box that I didn't realize that I should have put XP first.  Now I've installed a bunch of programs, and tweaked a bunch, and generally worked through some major headaches.  Can I still do a dual-boot with XP (I want it for games :) ).

If not, is there a good way to back up EVERYTHING I've done so far-- incl. settings and applications?  -That way I can just restore everything later...  Thanks.

-mike

---

### Post by Pumalite on 2007-09-12
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php), shrink Ubuntu's partition.
Install XP and then re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by mikeize on 2007-09-13
Working on this...  Made an NTFS partition for XP, but haven't yet been able to install XP onto it.  I'll keep playing with it and check back in later.  Thanks for pointing me in the right direction.

-mike

---

### Post by dabl on 2007-09-13
Or you could install Virtual Box or VMWare Player on your Linux system, and then install Win XP in that.  It would save you the partitioning thing.  :)

---

### Post by Pumalite on 2007-09-13
> **mikeize said:**
> Is this possible?  I was so excited to put Ubuntu on my fresh box that I didn't realize that I should have put XP first.  Now I've installed a bunch of programs, and tweaked a bunch, and generally worked through some major headaches.  Can I still do a dual-boot with XP (I want it for games :) ).

If not, is there a good way to back up EVERYTHING I've done so far-- incl. settings and applications?  -That way I can just restore everything later...  Thanks.

-mike
You are welcome. I hope it helps.

---

### Post by mikeize on 2007-09-13
> **dabl said:**
> Or you could install Virtual Box or VMWare Player on your Linux system, and then install Win XP in that.  It would save you the partitioning thing.  :)


That's a good idea, and I would except that pretty much the *only* reason I want XP is to play system intensive games.  It's my understanding that the VM solutions share resources with the host, and therefore may be to slow/unstable for decent gaming.  

As for dual-booting... still haven't got it working!  I have a FAT32 partition (I've read I can format it to NTFS after XP install), but I can't get XP to install!  I tried all kinds of things with the SuperGrub disk, such as hiding the Linux partitions, fixing Windows boot, but no luck!  XP will start loading drivers and checking hardware, etc, but then I always get a blue screen saying that it couldn't install for some reason.  

Of course, every day that passes, Ubuntu gets more and more customized, and reinstallation looks less and less attractive-- so I'm determined to work this out somehow. 

-mike

---

### Post by Pumalite on 2007-09-13
Now you are talking! Get a console for your games and stick to Ubuntu.

---

### Post by mikeize on 2007-09-13
> **Pumalite said:**
> Now you are talking! Get a console for your games and stick to Ubuntu.

eh...  I just spent all my money building a new computer, lol!  Nothing left for console gaming :(

I wish there was a way to install XP from cd onto the partition...  FROM Ubuntu.

-mike

---

### Post by Pumalite on 2007-09-13
Are you kidding?...We are trying to make people feel freer
Besides, Micro$%& is a dying dinosaur.

---

### Post by mikeize on 2007-09-13
> **Pumalite said:**
> Are you kidding?...We are trying to make people feel freer
Besides, Micro$%& is a dying dinosaur.

?
Do you mean "freer" to develop games for Linux?  Tuxkart just doesn't cut it for me I'm afraid...

---

### Post by Pumalite on 2007-09-13
Then install XP the traditional way.

---

### Post by pxwpxw on 2007-09-13
**mikeize**

In a similar situation, multi booting, xp refusing to install, I resorted to using the XP isntall disk rescue console mode to reformat the partition.

This was from the rescue console dos command line.

Not sure which came first.

run fixmbr (this means you will have to reinstall grub later)

run format for the target XP partition using the dos command line.

This also left xp with a C: drive, which it likes.

WARNING:Hazardous.

---

### Post by wolfen69 on 2007-09-14
i personally would wipe everything and start over. this way you can get even more used to installing and tweaking. you'll be a pro after a couple times.

---

### Post by mikeize on 2007-09-14
> **pxwpxw said:**
> **mikeize**

In a similar situation, multi booting, xp refusing to install, I resorted to using the XP isntall disk rescue console mode to reformat the partition.

This was from the rescue console dos command line.

Not sure which came first.

run fixmbr (this means you will have to reinstall grub later)

run format for the target XP partition using the dos command line.

This also left xp with a C: drive, which it likes.

WARNING:Hazardous.

Thanks guys.  I've been trying to do this kind of thing with SuperGrub disk, but no joy yet I'm afraid.  I also tried making a boot-floppy, but I get an error like, "non-system disk" or something like that.  Tried a fresh disk, but same thing.  Perhaps just as well since I am dead scared of formatting from the command line!
So in the meantime I installed Cube: Sauerbraten, and Nexuiz.  Decent enough games, but not Call of Duty 2!  So I'm looking into WINE solutions, since this really is all about gaming for me at this point.
I just can't bring myself to start from scratch-- it was such a headache configuring my graphics, and DVD playback, customizing, etc.  But in a month... who knows :)

-mike

---

