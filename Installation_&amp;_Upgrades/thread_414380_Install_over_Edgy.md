---
title: "Install over Edgy"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Stusi on 2007-04-19
I want to completely remove linux from my linux partition and then put on feisty fawn.  Why you ask?  Well i have been letting my roomate use my computer and he knows nothing about linux and has files saved all over.  Instead of even trying to find and delete all his myspace pictures and such i'm just gonna re-install linux.  So how exactly do i completely get rid of edgy before putting on the new feisty fawn?  I looked around and can't really seem to find an answer.

Setup

HD1 - 2 partitions.  One has windows XP and the other my edgy eft instal.
HD2 - Storage (set up to work in edgy with NTFS)

Also if i un-install one can i still get to the other install file cuz of grub not having something to start with?

Thanks,

Sam

---

### Post by gozzerd on 2007-04-19
Sam

If you currently have Grub installed and can boot to both windows and ubuntu from it, and if you have burned a feisty installation cd, and if you  can successfully boot from the cd, and the installation goes well on your system, in the installation program you should be able to reformat your edgy partition, install festy to the freshly formatted partition, have grub upgraded to reflect your new feisty kernel and /boot, have a correct menu.lst entry for windows, and everything should still work fine.

However, I would read the forums first and see if the installs are going well. You might want to take some safety precautions before doing this.

The simplest way to get rid of everything is to format the partition. But if you do that first, grub will not be able to boot either hd partition. Windows will be inaccessible, and the installer may not find the windows partition. I am not sure how important that is to you, but if it is very important, you should be sure you have a way of accessing your windows partition if something goes wrong. If you have your windows install disc, that should be enough. You could boot to the recovery console, do fixmbr, and possibly fixboot, and at least be able to access your windows partition. You can also make a grub boot disk that will allow you to manually boot stuff (if you learn grub commands and syntax). You could also download and burn a boot cd from the internet before altering your installation. I have heard good things about supergrub and ultimate bootcd (UBCD). Also SBM, simple boot manager. At this point, backing up your mbr is probably not going to be very helpful, as the first thing that is going to be lost is grubs directory on Edgy, so grub will be useless until the new installation  successfully completes.

I think a systems administrator would tell you that best practice here is to make a backup copy of everything 
you really, really, really don't want to lose. But in a best case scenario, the feisty installer will take you through everything safely, and as long as you install to the correct partition, you should easily be able to have exactly what you want, your windows partition, your fresh new, clean, feisty install, and your ntfs storage partition intact. 

Are you writing to the storage partition from ubuntu? I didn't think that was supported in Ubuntu yet.

---

### Post by Stusi on 2007-04-20
If you search for 3G-NTFS i believe is the name, it lets you read/write to NTFS and is pretty stable ( i have had no problems but judging from the forum response it still has a few issues).  Thanks for the info and i think i may just upgrade to feisty for now and then wipe windows and linux when i move in a few months cuz my roomate is the ultimate myspace teenager who gets every virus known to man.  Better to let him play and break stuff before i actually try to fix anything.

In any case, thanks for the info!

---

