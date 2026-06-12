---
title: "Failed to create file system- workin on pure newb knowledge"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by sugarfresh on 2008-05-26
well i'm trying to install ubuntu, i used unetbootin to get ubuntu working or i guess a temporary install. Once i get to the partitioning part, i have tried all the installation types, guided for complete installations on harddrive, manual, and the guided - resize. It doesn't matter which one i try it always says      
                    
"Failed to create a file system"
      The ext3 file system creation in partition #1 of SCSIB(0.0.0) (sba) failed.

On this partition i have Windows XP sp3 32-bit installed. i would use the cd installation method but i have no cd disks at hand.

can any of you help on this. It's taken me some time just to get a ubuntu interface without wubi, and i'm a complete noob at using ubuntu and any help on this problem/error would be much appreciated.

---

### Post by dstew on 2008-05-26
Did you defragment the Windows partition before trying to install? Maybe the partitioner was unable to shrink the Windows partition, so it could not create the new partition for Ubuntu. Also, immovable page files on the XP partition can interfere with shrinking. You should turn paging off in Windows before defragmenting.

---

### Post by sugarfresh on 2008-05-26
thank you i will try this. where can i find this paging on/off thing:confused:

---

### Post by sugarfresh on 2008-05-26
SON OF *****!!!!!!!!!!! i went to shut-down and closed out of the partition program undid all changes and what not, then i go to reboot and motherfu**** it says "Invalid or damaged Bootable partition." :mad::mad::mad:

well poop. i guess i'm goin to wait till tomorrow and get a disk from my teacher and do a live cd. that's the only way to get ubuntu on my pc now correct. course i guess i could get the xp disk from my teach and format so that its formatt so xp is only 80GB out of my 250 and give the rest to Ubuntu. hmmmmmm:(:(:( well thx i guess. kinda blows.

---

### Post by dstew on 2008-05-26
Control panels, System Properties, Advanced tab, Performance Settings button, Advanced tab, Virtual Memory change button, check the No Paging File  selection, then the Set button.

EDIT: I see your post about your boot problem. You will probably have to use a disk to repair this. There is a partition recovery program called TestDisk that you can use from an Ubuntu Live CD boot that might be able to recover your system. You can also try the Windows Recovery Console on the Windows CD.

---

### Post by sugarfresh on 2008-05-26
hmmm well i'm left with a 1 GB mp3, which i thk i can formatt to work like a flashdrive rite? if so i'm thking boot ubuntu from it, and then try and format my hardddrive to nothing, and install ubuntu onto it. Is that possible? i kno i can boot from usb i just want to know if i could format and install ubuntu onto my harddrive with my usb mp3/flahsdrive as the os.

---

### Post by sugarfresh on 2008-05-26
well thx for the support man

---

### Post by dstew on 2008-05-26
> i'm left with a 1 GB mp3, which i thk i can formatt to work like a flashdrive rite?It depends on whether or not your computer can boot a USB device. Check your BIOS boot settings to see if it is possible, If so, you can probably use the USB drive in your mp3 player to create a bootable Live CD.

---

