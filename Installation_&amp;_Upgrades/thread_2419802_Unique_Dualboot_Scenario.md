---
title: "Unique Dualboot Scenario"
date: 2019-05-25
forum: Installation &amp; Upgrades
---

### Post by levesqueonline19 on 2019-05-25
Good Day,

I have a laptop I wish to install Ubuntu on to an external USB 3 SSD, but i want to keep it completely independent, I want to have to go to boot options and select the drive to boot from it, I dont want it messing with my bitlocker drive installed on the laptop. Essentially Just using the hardware to boot my Linux OS when needed, no co-mixing.

I tried this, selected everything to be installed on the external, and everything looked good until i went into windows and figured out it did modify my laptops EFI and messed with my bitlocker which I have since fixed, but now cant boot off the external drive for Ubuntu any longer. when I try it just goes back to boot menu, likely because it installed GRub or something originally on my native windows drive?

appreciate any thoughts on how to accomplish this.

---

### Post by ubfan1 on 2019-05-25
That's bug 1396379 (or 1173457).  If you had set up an EFI partition on the external drive, you could just copy the entire contents of the internal drive's EFI partition to the external one, and it should boot.  The internal EFI was modified by having another directory, ubuntu, added, and a file, ...EFI/Boot/bootx64.efi renamed and replaced.  The new bootx64.efi is just a copy of shimx64.efi (or maybe grubx64.efi if you installed with secure boot off).  Remove it and rename the bkpbootx64.efi or whatever the backup is called back to bootx64.efi.  Your nvram which selects the OS to boot may need the order adjusted with efibootmgr.  With the external drive set up, select it to boot with some function key at power-up (f12?), and select the device.  That should bring up grub.

---

### Post by oldfred on 2019-05-25
You have to partition in advance, to include the ESP - efi system partition on external drive.

None of the selections on where to install grub2's boot loader work, but I found a work around, of unmounting default drive usually sda  or first NVMe drive and mount desired drive's ESP after install starts.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

You will need at least an ESP, FAT32 with boot flag. If drive is larger use 300 to 500MB more for future use. If drive is smaller 100MB will work. I use about 70GB, but use the FAT32 partition for my UEFI update files as UEFI can directly read FAT32, so need a bit of space for that.
I also like to separate system from user data. Newer users can use a separate /home which you can create during install or if partitioned in advance you create two ext4 partitions one for / and one for /home. Either way you have to use Something Else and choose (change button) which partition is which.

External drives only boot from /EFI/Boot/bootx64.efi if directly booting from UEFI one time boot key. Ubuntu now creates that file as a copy of grub/shim boot files.
If you let Ubuntu install to ESP on internal drive, you can set it as a default boot. But if Windows is encrypted, grub will not boot it anyway and you have to boot from UEFI boot menu.

Two drive or any second, external or other drive than sda.
Note that full install to any drive other than sda in UEFI mode has some issues. Grub's default  only installs to the ESP - efi system partition on sda. And you then have to copy files to your install. See work around in bug report, link above.
Good advice on UEFI and two drive installs and links to UEFI explanations
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)
Full install to external drive.
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator)

General UEFI install info in link in my signature below.

---

