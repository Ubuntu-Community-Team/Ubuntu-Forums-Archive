---
title: "Installing Windows After Ubuntu"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by Lesouteneur on 2007-12-19
I want to reinstall Windows vista  now that i already have ubuntu completely installed. I want to reinstall it but only to dual-boot without losing any of my linux data. I need it to play games. its easy if i had it installed first then ubuntu then dual boot but how do I do it after I already have Ubuntu installed?

---

### Post by fs3rp4 on 2007-12-19
Do a mbr backup with dd and after install Vista restore the mbr and setup the new OS in Grub menu.lst.

Backup
dd if=/dev/hda of=mbr.backup bs=512 count=1

Restore
dd if=mbr.backup of=dev/hda bs=512 count=1

---

### Post by al108 on 2007-12-19
You can also use [easybcd]("http://neosmart.net/dl.php?id=1") from Vista to add Ubuntu to Vista boot manager. In this case you may need to install grub on your Ubuntu partition and not in MBR.

---

### Post by rsambuca on 2007-12-19
And now for the third different option (isn't linux great?):

Use any live Ubuntu CD and just re-install grub.

sudo grub

grub> root (hd#,#)  [COLOR="Gray"]This is your Ubuntu partition[/COLOR]
grub> setup (hd0)  [COLOR="Gray"]This writes to the mbr[/COLOR]
then quit or exit (I can't remember which, offhand)

---

### Post by djbon2112 on 2007-12-19
> **rsambuca said:**
> And now for the third different option (isn't linux great?):

Use any live Ubuntu CD and just re-install grub.

sudo grub

grub> root (hd#,#)  [COLOR="Gray"]This is your Ubuntu partition[/COLOR]
grub> setup (hd0)  [COLOR="Gray"]This writes to the mbr[/COLOR]
then quit or exit (I can't remember which, offhand)

I tried doing this, but the Windows partition wasn't added and adding it manually failed. My post in another thread: [http://ubuntuforums.org/showpost.php?p=3981621&postcount=6](http://ubuntuforums.org/showpost.php?p=3981621&postcount=6) If you can help that would rock, I kinda want to get this working soon!

---

