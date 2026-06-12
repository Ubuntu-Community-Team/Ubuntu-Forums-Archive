---
title: "Uninstall Ubuntu?"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by djgaz89 on 2007-10-29
how can i uninstall unbuntu and the grub loader when i'm dual booting with vista?

i am using a single hard drive with vista on the main patrition

thanks very much

---

### Post by It_Was_Luck on 2007-10-30
Okay lets do this part first:

Once you uninstall ubuntu Grub is probably going to show Error 22, because it can't find the partition of Ubuntu (duh) because you removed it. So take your computers revoery CD (if you don't have one look below) and pop it in then type in "FIXMBR" this will go to your MBR (master Boot Record) and tell it to find windows when it boots.

If you don't have a Recovery CD, burn yourself a SuperGrub CD, it has a lot of cool stuff including a function that will do EXACT what typing in "FIXMBR" would do in a Revocery CD.
Heres the site in case you want to read up on it...
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)
and heres the download link...
[http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2](http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2)

Burn that image to a disc, boot it, then select "Windows" Then select "Fix boot of Windows" this will tell your MBR to look for Windows at boot, and this will get rid of any Grub Error you will get.


Okay now we have to do the uninstall. Go into Vista and find a partitioning program (I'm pretty sure Vista has one, if not google it) Then just remove your Ubuntu partition, then restart your computer and you'll get the Grub Error (probably 22) As I explained above use either your SuperGrub Disc or your computers Revocery CD to fix your MBR.


Hope that helped.

---

