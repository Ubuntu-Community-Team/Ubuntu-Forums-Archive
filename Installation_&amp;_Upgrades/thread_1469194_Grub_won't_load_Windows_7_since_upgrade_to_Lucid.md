---
title: "Grub won't load Windows 7 since upgrade to Lucid"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by jonathan_ender on 2010-05-02
I am dual booting windows 7 and Ubuntu, and since the upgrade from 9.10 to 10.04 Windows 7 won't load.
I tried the solution posted in another [thread]("http://ubuntuforums.org/showpost.php?p=9211128&postcount=3") with a similar problem but to no avail.

[URL="http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector"]http://sourceforge.net/apps/mediawik...ms:Boot_Sector 
[/URL] 
Boot Info Script:
[http://wklej.org/id/326663/](http://wklej.org/id/326663/)

---

### Post by Frantic_Earthling on 2010-05-02
Have you tried *sudo update-grub* ?

Worked for me...

---

### Post by wilee-nilee on 2010-05-02
> **jonathan_ender said:**
> I am dual booting windows 7 and Ubuntu, and since the upgrade from 9.10 to 10.04 Windows 7 won't load.
I tried the solution posted in another [thread]("http://ubuntuforums.org/showpost.php?p=9211128&postcount=3") with a similar problem but to no avail.

[http://sourceforge.net/apps/mediawik...ms:Boot_Sector](http://sourceforge.net/apps/mediawik...ms:Boot_Sector) 

Boot Info Script:
[http://wklej.org/id/326663/](http://wklej.org/id/326663/)

Thanks for the bootscript link that will get you help.I looked and see some anomalies but I think just waiting for the one who know will get things fixed. The sourceforge link isn't working but all anybody really needs here is that script.

---

### Post by jonathan_ender on 2010-05-02
> **Frantic_Earthling said:**
> Have you tried *sudo update-grub* ?

Worked for me...
I tried but makes no difference.

---

### Post by frantid on 2010-05-02
your situation is similar to this:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3)

make sure you choose the right partition to fix the partition table.  you can also use the win7 dvd.

---

### Post by dino99 on 2010-05-02
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by oldfred on 2010-05-02
jonathan_ender
You first post has a link to this:
  	[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But if you copy long links from other posts they get shortened & do not work. With windows7 you have a boot partition and a system partition. I do not know which has to be repaired or maybe both. Did you try that in testdisk.
Otherwise you need to use windows:
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

dino99 - are you posting the correct link? That seems to be to your link on settting up partitions?

frantid - Your link is identical (and also by meierfra) to the link the OP had but was in error. I think meierfra gave up posting the instructions and just created a page.

---

### Post by frantid on 2010-05-02
oldfred - I couldn't open his link, but I see that in the link you posted.  I like the thread better personally, because it also has your post with links in it as well.  But I should link to the thread instead of the first post.

I don't know why there are all these errors on install.  I did notice on my lucid test partition that I do not have a device.map file in /boot/grub/  Not sure what that would cause.  I boot off an independent boot partition, so I did not get hit.

---

### Post by jbernardo on 2010-05-02
I have a similar situation. I have already reinstalled w7 boot sector (bootrec.exe), booted into w7 to check if it is ok, then reinstalled grub, and did this twice, with the same results. A configuration that worked on karmic no longer works on lucid. Grub asks me to introduce the boot media (a improvement, first it only showed a blinking cursor), and pressing any key returns me to the grub menu. I've used testdisk to make the w7 partition bootable, I've reinstalled grub, I don't know what else to do.

---

### Post by frantid on 2010-05-02
> **jbernardo said:**
> I have a similar situation. I have already reinstalled w7 boot sector (bootrec.exe), booted into w7 to check if it is ok, then reinstalled grub, and did this twice, with the same results. A configuration that worked on karmic no longer works on lucid. Grub asks me to introduce the boot media (a improvement, first it only showed a blinking cursor), and pressing any key returns me to the grub menu. I've used testdisk to make the w7 partition bootable, I've reinstalled grub, I don't know what else to do.


do you have multiple drives?

---

### Post by jbernardo on 2010-05-02
Only one, and a card reader (this is on a 1101HA asus netbook).

---

### Post by frantid on 2010-05-02
> **jbernardo said:**
> Only one, and a card reader (this is on a 1101HA asus netbook).


ok, should probably start your own thread and post up the bootinfoscript results.

---

