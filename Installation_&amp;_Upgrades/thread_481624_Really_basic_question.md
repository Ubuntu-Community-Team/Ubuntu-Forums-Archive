---
title: "Really basic question"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by leebrown66 on 2007-06-22
Hi, I just want to confirm that the CD download iso image is a bootable CD?

I am trying to install on some old hardware (circa 1995) and it may simply be that the bios isn't compatible with the CD booting process.

Sorry for asking such a simple question, but it's not something I was able to find here.

Thanks,
Lee

---

### Post by loserboy on 2007-06-22
yep, it is.  even the alternate is bootable, it just doesnt have a graphical installer.  I take it you already tried making Cdrom the first boot priority?

---

### Post by coffeecat on 2007-06-22
The desktop CD boots up to a live GUI from which you can install. The alternate CD boots up but only to a text-based installer.

If you are trying to install Ubuntu to a 10+ year old machine you might want to post hardware details so that members can comment. The gnome desktop (Ubuntu) and KDE (Kubuntu) desktops are quite memory hungry and need at least 250MB RAM (if I remember correctly) - preferably 512 MB -  to run. If you've got less memory then this is one reason why the desktop CD won't boot up.

---

### Post by leebrown66 on 2007-06-22
ya, boot sequence is CDROM, C, A.  The boot activates all devices (i.e. they power up, spin, etc.) then I wait for a little while, then the BIOS informs me the HD is unbootable (not surprising as it's been formatted clean)  I tried an old 8x CDROM, a new 56x CDROM (both IDE) and no luck.

I know on some older motherboards, the CDROM needs to be master on IDE2, or slave on IDE1, quirky, I've tried all combinations of Master/Slave on IDE1 & 2 to no avail.

Don't suppose there's a boot from floppy heh heh?  If I can't boot from CDROM, I don't know how I can get anything on this machine....

Thanks,

---

### Post by loserboy on 2007-06-22
hmm, honestly it might be worth searching for a way to get a floppy to jumpstart it,  I know you can get it installed, people have got ubuntu on some oooolld stuff

---

