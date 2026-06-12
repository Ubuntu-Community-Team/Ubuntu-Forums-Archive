---
title: "How to remove Ubuntu and re-install Win7?"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by shezz on 2013-05-24
basically, i had windows xp on this laptop and wanted to try ubuntu.
i installed it and stupidly did not keep xp when it asked during the installation.
i did not like ubuntu so wanted to put win7 on it.
when i put in the win7 disc and tried booting from it, ubuntu just loaded and nothing happened. 
im not really sure what to do?

thank you

---

### Post by 2F4U on 2013-05-25
You have to tell your computer to boot from the Windows disc instead of the hard disk. This is usually done in the BIOS by changing the boot order.

---

### Post by Bucky Ball on 2013-05-25
Welcome to the forums (however briefly). 

Boot from the LiveCD (the Ubuntu install disk) and Try Ubuntu>when at a desktop open Gparted>right click to make sure all disks are unmounted (they should be by default)>delete all partitions leaving free space>restart and install Windows.

Done. Windows won't/can't delete the Linux EXT* partitions during install as it has no idea what they are so don't try that. You need to get rid of the EXT* partitions before you install Windows.

---

### Post by whatthefunk on 2013-05-25
Enter BIOS when your computer starts.  This is usually done by pushing ESC, F2 or F4 before the OS starts to load....it depends on your motherboard.  From there, you can tell the computer where to boot from, in this case your DVD player.

---

### Post by fantab on 2013-05-25
> **Bucky Ball said:**
> Welcome to the forums (however briefly). 

Boot from the LiveCD (the Ubuntu install disk) and Try Ubuntu>when at a desktop open Gparted>right click to make sure all disks are unmounted (they should be by default)>delete all partitions leaving free space>restart and install Windows.

Done. Windows won't/can't delete the Linux EXT* partitions during install as it has no idea what they are so don't try that. You need to get rid of the EXT* partitions before you install Windows.

+1.

Yes, windows does not know how to work with Linux filesystem ext2,3 or 4. That is why you have to delete your partitions that Ubunu installer created.

---

### Post by RoyBinder1972 on 2013-05-25
Thats easy...
1. enter yor BIOS setup and change "boot order" or "boot sequnce" to be HD in 1st place.
2. Load win7 disk and manually erase all partitions.
3. A friendly advice - considr keep using ubuntu since its much moer powerfull, free and easy to use from all windows vers.
i did it 6 years ago and never returned to use windows since.
start using new OS is allways a beat hard but in case of ubuntu worth the effort.

---

### Post by shezz on 2013-05-25
Thank you all!

---

### Post by Bucky Ball on 2013-05-25
Just out of curiousity, before you disappear forever, would you mind sharing what in particular didn't you like about Ubuntu? As long or brief as you like. ;)

You could perhaps post that here:

[http://ubuntuforums.org/forumdisplay.php?f=434](http://ubuntuforums.org/forumdisplay.php?f=434)

Cheers.

PS: When you're back in Win, if you want to try again, most of the flavours of Ubuntu allow you to try them by booting from the disk and running if from there without an install to the hard drive. You might prefer Xubuntu, Lubuntu or Kubuntu to Ubuntu. Some people don't like the Unity desktop environment (myself included) and these flavours don't use it.

---

### Post by shezz on 2013-05-25
im just so familiar with windows, Ubuntu just wasn't compatible with me aha. was too confusing. maybe if i gave it more time, oh well

---

### Post by Bucky Ball on 2013-05-25
Got you. Read the PS I just added to my last post. Good luck. ;)

---

### Post by shezz on 2013-05-25
Thanks!

---

### Post by shezz on 2013-05-25
ok, when i try and boot, Error: no such partition.
                                 grub rescue>
comes up?

---

### Post by Bucky Ball on 2013-05-25
Are you booting from the LiveCD, the install CD, or is this a question about the Ubuntu you have installed to your hard drive?

---

### Post by Mark Phelps on 2013-05-26
> **shezz said:**
> ok, when i try and boot, Error: no such partition.
                                 grub rescue>
comes up?

This is the error you get when GRUB is still present in the MBR but the actual GRUB code has been removed from the PC -- as this is what happens when you simply remove Ubuntu but don't replace the MBR with Windows code.

---

