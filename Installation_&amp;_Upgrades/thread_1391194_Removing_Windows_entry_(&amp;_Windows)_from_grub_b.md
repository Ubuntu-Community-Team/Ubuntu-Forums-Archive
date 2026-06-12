---
title: "Removing Windows entry (&amp; Windows) from grub bootloader?"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Nightstrike2009 on 2010-01-26
Hiya everybody,

I currently dual boot and wish to know how to remove the Windows partition/drive while still allowing Ubuntu 9.04 to load safely as my main OS. 

I know how to restore windows partition by;
> If MBR gets damaged boot from MS Windows Xp disc, Select "R" for "recovery console", select main windows installation drive (admin password usually nothing, just press enter) and type "FIXMBR" this will allow you to boot windows again, but Ubuntu partition will be unbootable and require installing ubuntu again to dual boot. 


But this leaves Ubuntu partition Un-bootable as it removes the grub menu, how would I do the same for Ubuntu and make window partition un-bootable so I can remove it?

---

### Post by darkod on 2010-01-26
The procedure you quoted reinstalls XP bootloader on the MBR deleting grub. In that case of course you can't boot ubuntu any more.
But why do you want this procedure at all?
If you only want to delete windows partition, then just use Gparted and delete it. After that just open menu.lst (if you are using 9.04 and grub1) and delete the windwows entry. That will remove it from grub boot menu. Even if you leave it in the grub boot menu for a while, doesn't hurt. Of course you won't be able to boot windows after deleting its partition but if the entry remains few days in the grub menu it will do no harm.

On the other hand, if you plan to install another winows in place of the current, that will delete grub from the MBR (windows doesn't give you an option to avoid this) and in that case you need to reinstall grub to the MBR. Instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Make sure you use 9.04 disc if you are running 9.04 and use the instructions for 9.04 (9.10 has grub2, different instructions).

---

### Post by Nightstrike2009 on 2010-01-26
Thanks darkod,

I was just providing info on how to do the opposite, but I wish to do the same for windows but didn't know how, was just my way of explaining my problem I suppose. :-)

> **By darkod:**After that just open menu.lst (if you are using 9.04 and grub1) and delete the windows entry. That will remove it from grub boot menu

What file would i need to edit the windows entry on grub 1.97beta (Grub2)?, this would be handy for me to know as I Plan to upgrade to 10.04LTS on release.

I am not using 9.10 at moment because it doesn't recogise HUAWEI K3565 REV2 (Vodafone Mobile Connect 3g modem) correctly and cannot connect to the internet, so I am stuck with 9.04 for now.

---

### Post by darkod on 2010-01-26
With grub2 it's even easier because it automatically detects other OSs, and when they are gone too. :)

So, in 9.10 you would just delete the windows partition and then run:
sudo update-grub

and new grub.cfg file is generated and windows is no longer in grub menu.

---

### Post by Nightstrike2009 on 2010-01-26
Cheers Darko, you have been a real help I will mark my thread solved now thanks to you, I would click your Thanks button but since we no longer have them.

THANKS FRIEND ;-)

---

### Post by darkod on 2010-01-26
No problem, cheers.

---

