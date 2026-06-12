---
title: "Tried to uninstall Linux 18.014, install 16.04, alongside Win10.  Bricked the laptop"
date: 2019-11-23
forum: Installation &amp; Upgrades
---

### Post by abramson98 on 2019-11-23
[http://paste.ubuntu.com/p/RWb4pPZNFY/](http://paste.ubuntu.com/p/RWb4pPZNFY/)

I'm in a world of hurt, like they say.  I got dual boot all working fine, Win10 alongside of Ubuntu 18.04.  But the software i needed to use only works with 16.04.  So I tried to uninstall and load the older version of Ubuntu, now I get to the grub> prompt  and can't get past there.  I've tried zillions of things.  Booting from Ubuntu live stick to try and fix the partitions (probably made it worse) and every option in my HP laptops "repair" utility (HP Omen).  But I can't boot windows, can't boot the 16.04 that I was in the process of loading.  I CAN boot from USB/live ubuntu 16.04.  Any help is greatly appreciated!

---

### Post by ubfan1 on 2019-11-23
Did you try booting windows from the EFI menu,(some function key at power-up that gives you a choice of boot device/os)?  That should skip grub altogether.  Did you complete the 16.04 install?  If you can still boot the installer, don't know why that wouldn't allow an install to the old 18.04 partition.

---

### Post by abramson98 on 2019-11-23
I did try that, but no luck.  I didn't install 16 with 18, I was removing 18 by deleting the Linux partition in Windows.  The idea was I was going to convert that back to free space, then install 16 from the live install disk there.  Bad idea.  The 16 install seemed to complete and I can see evidence that it's in there if a boot into Linux off my USB and look around my drive.

---

### Post by ubfan1 on 2019-11-23
The installer (for years) has tried to put the UEFI bootloaders onto sda, instead of where you indicate, but try running  sudo  grub-install /dev/nvme0n1  That should put the bootloaders onto the right device.

---

### Post by abramson98 on 2019-11-23
The only way I can see to do that is to boot Linux from USB stick.  I did that and executed the command from a terminal window (once Linux booted, again from the USB stick) and got:

grub-install: error: failed to get canonical path of `aufs'.

---

### Post by gnusci on 2019-11-23
Make a backup with a USB or CD Live Linux, then try to find the solution.

You may need to repair GRUB:

[https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

---

### Post by yancek on 2019-11-24
You're right about the method you used being a mistake.  You should have first backed up any personal data on 18.04, then booted the Ubuntu install usb and selected the partition on the SSD on which you had 18.04 and simply install 16.04 there, choosing to format that partition before beginning the install.  Too late now so do you have an option on your HP to boot from EFI file.  My HP laptop has that option by I don't know if that is universal with HP.  If you have that option in the BIOS, try booting the window and Ubuntu options that way.

> Please do not forget to make your BIOS boot on nvme0n1p1/efi/.../grub*.efi file! 

The above message is at the bottom of the boot repair report.  The efibootmgr output in boot repair does not show that file so you might boot the Ubuntu usb and mount /dev/nvme0n1p1 to see if you have an ubuntu directory there with a grubx64.efi file.  

> grub-install: error: failed to get canonical path of `aufs'. 		

Try chroot before running that command as it appears to be trying to install to the Ubuntu usb.  chroot is explained at the site below, start at Section 2.2.5 and start at number 6. 

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

---

### Post by oldfred on 2019-11-24
I have not seen this from Boot-Repair. 
I think it was trying to run an update, but failed.

> E: The package lists or status file could not be parsed or opened.
linux-generic NOT available (apt-cache policy  problem)

While probably repairable, since new install, probably quicker just to do another install.
Did you verify that ISO was correct?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

