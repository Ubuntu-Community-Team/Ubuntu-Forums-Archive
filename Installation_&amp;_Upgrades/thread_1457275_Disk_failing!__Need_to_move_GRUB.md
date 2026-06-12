---
title: "Disk failing!  Need to move GRUB"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by newbie001 on 2010-04-18
My boot disk is failing!  I am a little nervous, so I'd like to have extra eyes on this so that I don't fubar it.

My setup is as follows, with WinXP and Ubuntu living on completely separate drives:

/dev/sda -- Windows XP, bootable, grub2 installed to MBR
/dev/sdb -- Karmic 9.10, NOT bootable, NO grub on MBR

The boot disk (WinXP with grub2 on MBR) is failing.  I need to replace it, pronto.

Do I need to get any data from the MBR on the failing disk before removing it?  

Should I make the Karmic disk bootable and install grub on it before removing the failing boot disk?

Once I have Windows (re)installed on a new disc (which will still be /dev/sda) I want to install GRUB2 to its MBR and re-instate the old (current) boot options.  How should I do this?

Thanks!

---

### Post by DrMelon on 2010-04-18
> **newbie001 said:**
> My boot disk is failing!  I am a little nervous, so I'd like to have extra eyes on this so that I don't fubar it.

My setup is as follows, with WinXP and Ubuntu living on completely separate drives:

/dev/sda -- Windows XP, bootable, grub2 installed to MBR
/dev/sdb -- Karmic 9.10, NOT bootable, NO grub on MBR

The boot disk (WinXP with grub2 on MBR) is failing.  I need to replace it, pronto.

Do I need to get any data from the MBR on the failing disk before removing it?  

Should I make the Karmic disk bootable and install grub on it before removing the failing boot disk?

Once I have Windows (re)installed on a new disc (which will still be /dev/sda) I want to install GRUB2 to its MBR and re-instate the old (current) boot options.  How should I do this?

Thanks!

You should have a /boot/ partition on the boot disk, where Grub2 resides - copy the grub folder from this partition to another disk to retain settings.

Please note though, that when adding a new drive, make sure it follows the same nomenclature as other drives - you might find it'll be called hd- instead of sd-... in which case you'd be just as well doing a fresh install of Grub2.

---

### Post by newbie001 on 2010-04-18
> **DrMelon said:**
> You should have a /boot/ partition on the boot disk, where Grub2 resides - copy the grub folder from this partition to another disk to retain settings.

Please note though, that when adding a new drive, make sure it follows the same nomenclature as other drives - you might find it'll be called hd- instead of sd-... in which case you'd be just as well doing a fresh install of Grub2.

Thanks.  But, actually, no.  I probably did not explain this very well:  There is no /boot partition on the boot disk.  The boot disk (/dev/sda) is the original WinXP install.  When I later installed Hardy (now up to Karmic) on /dev/sdb, I simply installed (legacy) grub (now replaced with grub2) on the MBR of the WinXP disk.

---

### Post by newbie001 on 2010-04-18
Perhaps it would be more accurate to say... I need to replace /dev/sda and then install grub to the MBR in such a way that it still finds Ubuntu on /dev/sdb.  Perhaps grub will automagically discover Windows on /dev/sda and all my Ubuntu kernels on /dev/sdb.  But just in case it does not, I'd like to know what I should get from the failing /dev/sda before I replace it with a shiny new terabyte.  :)

---

### Post by oldfred on 2010-04-18
I prefer to have to boot loader of a system on the same drive as the system when your have more than one drive. I would install grub2 the sdb and make it the boot drive in BIOS. 

When you replace sda you can just run sudo update-grub and it will find your new windows install. Also then you will not have any issues with the windows boot loader installing to the MBR of sda. The only time you may have issue is if you remove sda, sdb will become sda and any reference to sdb may be wrong. If all your settings particularly grub and fstab use UUIDs you should have no problems.

---

### Post by newbie001 on 2010-04-18
> **oldfred said:**
> I prefer to have to boot loader of a system on the same drive as the system when your have more than one drive. I would install grub2 the sdb and make it the boot drive in BIOS. 

I think that's excellent advice.  In fact, I just did exactly that just before I read your reply.  :)  

> **oldfred said:**
> 
When you replace sda you can just run sudo update-grub and it will find your new windows install. Also then you will not have any issues with the windows boot loader installing to the MBR of sda. The only time you may have issue is if you remove sda, sdb will become sda and any reference to sdb may be wrong. If all your settings particularly grub and fstab use UUIDs you should have no problems.

I have not actually unplugged /dev/sda *yet* so it's not acid-washed yet.  As you say, /dev/sdb will probably become /dev/sda, although BIOS might have some say in this.  It appears that my /boot/grub/grub.cfg uses UUIDs, but I have not checked /etc/fstab yet.  

Thanks for the clue!

---

### Post by newbie001 on 2010-04-19
> **oldfred said:**
> I prefer to have to boot loader of a system on the same drive as the system when your have more than one drive. I would install grub2 the sdb and make it the boot drive in BIOS. 

When you replace sda you can just run sudo update-grub and it will find your new windows install. Also then you will not have any issues with the windows boot loader installing to the MBR of sda. The only time you may have issue is if you remove sda, sdb will become sda and any reference to sdb may be wrong. If all your settings particularly grub and fstab use UUIDs you should have no problems.

Fred, your advice was spot-on.  Thanks for talking me down off the ledge.  My new setup is as follows:

/dev/sda - WinXP, new drive, bootable, *no* grub.
/dev/sdb - Karmic, bootable, grub2 with entries for Karmic & XP
BIOS set to boot second drive.

Tip: Unplug your "other" drives whenever installing Windows to an initially unformatted disk.   Besides being a good idea on principle, failing to do so may result in the Windows installer identifying your other formatted drives/partitions as C:, etc.  The installer will happily make, say, F: the root of Windows.  And Windows will be happy.  But you can bet some legacy app0 will have C:\... hard-coded and then you're out of luck.  So spare the Windows instalelr any confusion.  Unplug other drives and replug them after installing Windows.

---

### Post by malcove on 2011-04-22
Just in case anyone has the same problem, I had a system booting from a failing windows xp disk on /dev/sda with Ubuntu on /dev/hdb. I wanted to change the system to boot from the Linux disk /dev/hdb instead. What confused me was that when I changed the system to boot from the other disk grub started thinking of the disk as hd0 instead of hd1, although the it was still /dev/hdb from a device point of view.

---

