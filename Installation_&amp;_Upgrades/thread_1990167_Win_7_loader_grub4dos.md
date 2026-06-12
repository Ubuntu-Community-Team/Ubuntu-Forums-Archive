---
title: "Win 7 loader grub4dos"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by francosibillini on 2012-05-29
I'm trying to install ubuntu 11.04 in dual boot with win 7 loader. I've followed the bottom procedure.
But when I reboot I obtain:

grub>

promp of grub4dos

I don't really know how to solve.
Please 
Is there anybody out there tha can help me?

Install Linux Ubuntu 11.04

Raid/LVM was not an issue when testing and partitions were created manually during installation. Ubuntu was installed on previously created Unallocated space with its boot loader installed to the Linux EXT4 partition. Windows still booted automatically after Ubuntu installation. Finally EasyBCD was run in Windows to create the Ubuntu 11.04 entry in Win7's boot manager thereby creating the Windows-controlled dual-boot.

Bootup from the Linux Ubuntu 11.04 live CD 
In the Welcome window, select the correct language and click Install Ubuntu. 
Read the Preparing to install Ubuntu window and click Forward. 
 
In Allocate drive space, select Something else (that's IMPORTANT), and click Forward.

In the new Allocate drive space, do not click 'Install Now' until instructed. 
This section has been designed by the Ubuntu team with dual-booters in mind. Thanks team! 

Highlight the free space you created earlier on the correct hard disk (sda=1st disk, disk0) (sdb=2nd, disk1) 
and click the Add button. Note: the vertical scroll bar appears only when you mouse-over it.
The Create partition window will open.
In Type for the ..., select Primary (but Logical if 3 Primaries already exist on that disk) 
- if in any doubt, select Logical.
In New partition size ..., enter all available minus about 2000 MB for the Swap.
In Location for the ..., select Beginning.
In Use as:, select Ext4 journaling system (the default) in the drop-down.
In Mount point:, select / (forward slash) in the drop-down.
Click OK.
Back in Allocate drive space, highlight the now smaller free space (scroll down if necessary) 
and again click Add.
The Create partition window will open again.
In Type for the ..., select Logical.
In New partition size ..., use all available space (unless creating a data partition).
In Location for the ..., select Beginning.
In Use as:, select swap area in the drop-down.
In Mount point:, no change is allowed.
Click OK.

If you left space for a Linux data partition, now use remaining free space to create, exactly as above, another EXT4 partition for your own data but select /home for Mount Point 
 
The next part is VITAL for the correct location for Ubuntu's boot loader (GRUB2).
The default is for /dev/sda and you must not accept it.
You are still in Allocate drive space. 
Note of the Device name allocated to the Ubuntu EXT4 partition, like /dev/sda5 or /dev/sdb1.
In the drop-down under Device for boot loader installation:, 
select the /dev/sd** name you just identified for the Ubuntu EXT4 partition.

Make sure you are happy with what's displayed on-screen. 
When you are ready click 'Install Now', or click Quit. 

Linux Ubuntu 11.04 will now install itself on the new Ubuntu EXT4 partition and will place Ubuntu's boot loader (GRUB2) at the start of that partition. 
 
During the installation, you can attend to location, keyboard, password, imports, etc. 
(Log in automatically, under Password, is useful for many home users). 

Click Restart Now when installation is finished, remove the DVD when requested and press the Enter key. 
Window 7 will boot normally.
We can now use the EasyBCD 2.1 utility to add Ubuntu 11.04 to the Windows 7 boot loader.

Place a Linux Ubuntu 11.04 boot option in Windows boot loader

Restart to Windows 7
Install and run EasyBCD 2.1 from the Windows 7 drive. 
Click Add New Entry in the left pane.
Click the Linux BSD tab under Operating Systems in upper right pane.
In Type, select Grub2 in the drop-down.
In Name, use a name like Linux Ubuntu 11.04
In Device, it will be Automatically configured - we used GRUB2, not GRUB(legacy).
Click Add Entry in the same pane and wait a few moments while EasyBCD locates Ubuntu.
Optionally, you can now modify the timeout of the boot loader menu 
- click the Edit Boot Menu (left pane) and set the Boot default OS after to about 5 seconds.
Exit EasyBCD.
Restart computer. Select Linux Ubuntu 11.04 from the Windows 7 boot menu.

---

### Post by fantab on 2012-05-29
Welcome to the forum.

Like they say, "Keep it simple, silly". GRUB is the finest of the Boot Loaders out there and it is very simple to use. So why do you want to take EasyBCD route? 

Secondly is there any particular reason why you are using 11.04 when 12.04 is out there?

Now, Did you Create LVM? because AFAIK LVM does not work with Windows... correct me if I am wrong.

If you have created LVM then please wait for someone more knowledgeable to help you out.

---

