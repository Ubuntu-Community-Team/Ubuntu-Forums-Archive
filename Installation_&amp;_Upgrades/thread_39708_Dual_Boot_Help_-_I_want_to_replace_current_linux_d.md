---
title: "Dual Boot Help - I want to replace current linux distro with ubuntu"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by gkjones on 2005-06-06
Hi all,

I just need my hand holding through the installation process.

I currently have a dual boot machine M$ XP & SuSE. I want to replace SuSE with ubuntu.

I expected the install process to detect that I already had Linux and ask if I wanted to over write it - but it doesn't.

All I need to know is do I need to re-format my ext3 partition, ext3 and swap partitions or neither?

(I got twitchy at this point and exited the install!!)

Any help with this - and the next few steps in the install would be greatfully received

Regards

Keith

---

### Post by mingus on 2005-06-06
Whether the install process tries to keep SuSE or not is determined by what you do with the partitions.  In other words, after Ubuntu is installed the process will check the disk for all other OS's on the disk and build a grub file for booting all of them.

So to overwrite SuSE is just a matter of choosing the partitions you want to use for Ubuntu.  You'll need to define the mount points for the partitions, and the installer will want to re-format those.  Or you can delete the current partitions and create new ones.  Applies to swap as well.  Plan the partitions ahead of time and use expert mode to control the process.

Note that the installer's default is to use grub *and* to write the boot loader to the MBR.  Advisable to have bootable Windows recovery media (like the install CD)  available to repair the MBR should something go awry.  Or alternatively, create a boot floppy and verify the whole install before changing the MBR.

The other next step to be careful about is the apt-get configuration.  You'll be asked in the second stage whether the remaining packages will come from the install CD or the Net.  Don't say network unless you are actually connected.  If you say CD, you can update those packages later after you're on the Net.

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=gkjones]Hi all,

I just need my hand holding through the installation process.

I currently have a dual boot machine M$ XP & SuSE. I want to replace SuSE with ubuntu.

I expected the install process to detect that I already had Linux and ask if I wanted to over write it - but it doesn't.

All I need to know is do I need to re-format my ext3 partition, ext3 and swap partitions or neither?

(I got twitchy at this point and exited the install!!)

Any help with this - and the next few steps in the install would be greatfully received

Regards

Keith[/QUOTE]
 If you want to replace SuSE with Ubuntu, you will need to reformat the partition that holds SuSE (should be ext3) and use it for Ubuntu. WARNING: you lose all data on that partition - if there is anythinig you want to save (like your documents, if the are on the same partition), back it up on a CD. 

Swap parition is only used as a temporary storage --- thus, its contents is erased at each boot. Shouldn't make any difference whether you reformat it or not.

---

