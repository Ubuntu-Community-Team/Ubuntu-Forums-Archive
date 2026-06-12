---
title: "System Commander 8.2 and Ubuntu 7.10"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by thaxton on 2008-01-16
I got System Commander 8.2 to recognize Ubuntu 7.10.  

This assumes that you already have a Windows OS and System Commander 8.2 installed.

Install Ubuntu

When the GRUB installation starts (near the end of the entire Ubuntu installation) choose to install it on a floppy disk.  This will make sure that the MBR (System Commander's) is not overwritten.

*If you already installed GRUB to the MBR (the default) see the *** at the end of this post. Then continue here.

Now that this is done let's set the linux partition active/bootable. 

At the System Commander startup screen choose Partitioning, choose Manual Partitioning, locate the Ext3 file system and select it.  Under the Advanced menu select Set/Toggle Active/Bootable.  This will set that partition to Bootable.  You'll get a confirmation at the end of the process if it worked.

Let's double check.

Exit the Partitioner and Reboot.  When you get back to the System Commander startup screen you should see a Linux choice, don't use it yet, choose Information.  This will list your partitions.  Ensure that the Linux Partition is Bootable.  If it isn't bootable, repeat the above steps and recheck it.

Exit the Partition Information screen, place the GRUB boot floppy in your drive.  Select 'Boot from Drive A:' (Floppy) from menu.  This will start up Ubuntu.

Open a Terminal Window.

Type 'mount' hit ENTER.

This will show you the mounted volumes we are looking for '/dev/xxxx on / type ext3'  'xxxx' will be replaced with your volume location.  Mine is /dev/hda3, write yours down.

Now lets install GRUB to this volume.

From a Terminal window Type 'sudo grub-install /dev/xxxx' 
(replace 'xxxx' with your volume info) hit ENTER.

If you get "Installation finished. No error reported."  It completed successfully.

Shut down Ubuntu and remove all Floppies / CDs.

Restart and System Commander should have a Linux choice to use.

*** If you already installed GRUB to the MBR (the default) you will need the System Commander Rescue Disk to restore the MBR (System Commander's) to its version.  But before doing this, insert a blank floppy then, from a Terminal window in Ubuntu type 'sudo grub-install /dev/fd0'  replace fd0 with your floppy device if it is different.  This will create the GRUB boot floppy.  The GRUB boot floppy lets you boot Ubuntu just by inserting the floppy and restarting the computer (assuming you have the floppy set up to boot before other devices in the BIOS).

After creating the GRUB floppy remove it, reboot with System Commander Rescue floppy inserted and choose 'Enable System Commander'  This will restore the System Command MBR.  Remove the floppy and reboot.  System Commander should come up.


Let me know it this works for you and other versions of Ubuntu & System Commander,

Thomas Lepkowski

---

### Post by calibre97 on 2008-04-18
I have System Commander 9 and am trying to work with 7.04. I don't have a floppy (you still did?) for my laptop. I do have a PC Card CompactFlash adapter though that the Live CD saw. Can I choose that to do the shenanigans with grub to get it installed to my Linux partition?

---

