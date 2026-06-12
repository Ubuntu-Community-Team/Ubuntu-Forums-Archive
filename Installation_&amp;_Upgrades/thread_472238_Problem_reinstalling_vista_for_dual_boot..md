---
title: "Problem reinstalling vista for dual boot."
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by Eoghanalbar on 2007-06-12
I got a laptop that came with vista. I deleted it and put on ubuntu. I discovered that it would be wiser to set up a dual boot in case I need it while I get used to linux. I want to get rid of ubuntu (done), reinstall vista, then put ubuntu back (to make sure the vista install can't mess it up).

However, I'm starting to worry that maybe you can't actually *install* from the "recovery disks" that came with the laptop (a toshiba satellite a100), because I'm getting errors, and I'm having trouble finding a concrete answer with google. Does anyone know if that's the case?

I used gparted to set up a single ntsf partition over the whole drive (~120GB) because I wanted to read/write it with ubuntu later, but that didn't work. I tried fat32. I think I tried no partitions at all (I'll have to retry that later). I'm using fdisk to totally format the hard drive as I write.

Anyone know what I'm doing wrong?

---

### Post by coppertrail on 2007-06-12
I wouldn't create the NTFS partition before installing Vista.  During the Vista install, I would delete all volumes, and then create a C system partition of say 25-30 GB.  After the install, I'd use Disk Manager to create an NTFS D volume for data.  

Then, I'd use a third party partition manager to set up my ext3 partition for Ubuntu.  

As far as your install media, Call Toshiba and ask them.  The machine may have come with a system restore partition/utility and no install media.

My Dell machines came with a system restore partition and a utility that allowed me to create a Windows XP install CD.

---

### Post by Eoghanalbar on 2007-06-13
Thanks coppertail.

Well, the combination removal of all partitionséformat (entire 120GB ugh) worked.

The ubuntu live CD was vital to getting vista installed (and man, what a long process that is! ÈOkay, now reboot five timesÈ). How ironic. :p

And now in vista youtube videos, webpages, etc, donèt get stuck partway through downloading, and IM programs donèt constantly get disconnected.

I canèt figure out why ubuntu has that problem for me, and Iève got other priorities than messing with OSes right now (gotta finish exams), so you guys probably wonèt hear out of me for a little while.

Thanks, all. Catchya later.

Now to figure out how to fix whatever I did to vista that gave it a bilingual keyboard layout...

---

### Post by Sanchya on 2007-06-28
i also have the same hardware..... and also did  the same dual boot.....

I received my laptop with vista.. then i made recovery disk and install it again with partitioned drives , made two ntfs and one fat32 partition and left space free for ubuntu.. then i install fiesty . 

My dual boot is working fine now. Although earlier it didnt made grub loader properly but with the install CD i setup grub manually.And things are perfactly fine .
 The only issue is with SOund on  ubuntu..But i think thats not the case of dual booting....

This may help you.. :-)

---

