---
title: "I want to go from Ubuntu only to dual boot"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by Mattevt on 2008-07-24
I'm running only Hardy. I want to go back to a dual boot system (please don't ask me why, I have my own reasons). I booted into the live cd and set aside 5.5 gigs as ntfs. I then booted with my xp disk but during setup I get a message that setup can't find any hard disk drives.

Can someone help me?



Another thing I was thinking about doing was wiping the computer, installing XP, shrinking XP to 5.5 gigs, then reinstalling Ubuntu. Is this a bad idea?

---

### Post by tuxxy on 2008-07-24
> Another thing I was thinking about doing was wiping the computer, installing XP, shrinking XP to 5.5 gigs, then reinstalling Ubuntu. Is this a bad idea?

Thats what I would do, before you do install XP have you tried running it using Virtualbox from in Ubuntu, this way you dont need to reboot and also you could have it boot from a physichal drive too.

---

### Post by timcredible on 2008-07-24
the ntfs partition has to be the first partition for windows to be able to see it.

---

### Post by Euphorion on 2008-07-24
Hallo

Windows requires that the first partition be fee space, FAT or NTFS in order for windows to see a partition in which to install itself.

I have during my wonderings in this forum and by googling "Ubuntu Installation" seen very good guides to dual boot. One very good starting point with lots of links is the following "The illustrated dual boot page"

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

If you plan to use vista visit the following, they have a very good description of Windows after Linux. [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I have in the illustrated dual boot site found references to installing windows after Linux/Ubuntu

The other thing to do would be to make a gparted boot cd and move Ubuntu so as to create free space ahead of Ubuntu in order to install windows. This is somewhat time consuming but works. The only other thing that will happen is that should Grub (or Lilo) be installed in your MBR this will be overwritten after installing Windows and you will at first no longer be able to boot Ubuntu.

This you can solve be reinstalling Grub, this is best done using a SuperGrub CD. Available from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/). Then after reinstalling Grub you can boot XP and Ubuntu as required.

If you are using Vista then use EasyBCD available from [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1). If you use Vista and EasyBCD ensure that the Grub belonging to Ubuntu is not reinstalled in the MBR of your Harddisk, but in the partition containing Ubuntu then Partition 2 (in Grub notation hd0,1).

I hope that you will find the information you require and can get your system up and running as desired.

---

### Post by Mattevt on 2008-07-24
> **tuxxy said:**
> Thats what I would do, before you do install XP have you tried running it using Virtualbox from in Ubuntu, this way you dont need to reboot and also you could have it boot from a physichal drive too.

Virtualbox may be what I need. I have it installed and it's working, however I can't view my external (USB) hard drive in virtual box, (I also can't see my MP3 player.)

---

### Post by uidb4056 on 2008-07-24
> **Mattevt said:**
> Virtualbox may be what I need. I have it installed and it's working, however I can't view my external (USB) hard drive in virtual box, (I also can't see my MP3 player.)

If you have installed it from repositories then you have the OSE version, this version is open source but has no support for USB, if you want to work with USB you can uninstall the OSE version and then download the non open source version (but free) from virtualbox page [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Mattevt on 2008-07-24
I have figured out virtualbox and it's exactly what I need. Thanks for all the assistance, mods can close this topic if you want. I love this forum.

---

