---
title: "Install help"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by Crooksey on 2005-11-12
i recently go 5.10, and have a few questions about the install. 

1) At current i am using suse 9.3 abd my partition table looks like this

170gb of NTFS (sda1)
1gb Swap
28gb of Suse (sda6)

now if i format the last 2 partitions will ubuntu install Ok on here? 

2) Would it be best to reinstall the GRUB boot loader at the end of the install

3)does 5.10 come with ndiswrapper or do i manually install

Thanks

---

### Post by aysiu on 2005-11-12
Are you trying to replace SuSE with Ubuntu or tack on to do a triple-boot?

---

### Post by Crooksey on 2005-11-12
Replace

---

### Post by Crooksey on 2005-11-14
I have tried the install on an old machine, works fine but what about upgrading from Suse...any help? (replace Suse)

---

### Post by linbetwin on 2005-11-14
What do you mean by upgrade from SUSE?
 
If you want to replace SUSE, delete sda6 and swap and let Ubuntu repartition automatically. It will make / and swap.
 
Install GRUB to the MBR when prompted.
 
I don't know about ndiswraper.

---

### Post by aysiu on 2005-11-14
You don't need to delete SuSE before you install Ubuntu.
During the installation process, there will be a part where you're asked whether you want to erase the entire hard drive or manually edit the partition table.

Select "manually edit the partition table" and select your former SuSE partition to be formatted as ext3 and mounted as /
Select your former swap partition to be formatted as swap.

Then make sure you install Grub to the MBR.

---

### Post by Crooksey on 2005-11-15
if i do delete Suse, will that mees up Grub and will i still be able to boot?

---

### Post by wrtrdood on 2005-11-15
[QUOTE=Crooksey]if i do delete Suse, will that mees up Grub and will i still be able to boot?[/QUOTE]

Before grub installs, it checks for other OSes on the machine, lists them, then asks if it's OK to continue.  It's something of a "brute force" install which will replace the bootloader that was there before.  Suse will be history after the partition format and any reference to it in the bootloader will be wiped by the grub install.  Ubuntu will then become the default OS to boot.

  Make the selections *aysiu* said.  Be sure to tell the partition tool to format those new partitions.  This is an option on the page for each partition you set up.  The choice may default to that; certainly for swap.  The way to know is if the partition page shows a skull and crossbones on the line for the given partition it **will** be formatted.  Partitions that will **not** be formatted will show a smiley face.  After you save the partition table you will once again be shown what partitions will be formatted.  Verify that they are the right ones.

The MBR choice comes later when the install gets to the "where to put grub" question.

---

### Post by Crooksey on 2005-11-15
I am saying if  delete the 2 linux partitions and just have windows (until ubuntu) will the PC still boot and grub just show windows?

---

