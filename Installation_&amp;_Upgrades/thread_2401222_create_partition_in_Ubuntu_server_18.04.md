---
title: "create partition in Ubuntu server 18.04"
date: 2018-09-15
forum: Installation &amp; Upgrades
---

### Post by karebo on 2018-09-15
I am new to Ubuntu/Linux, the only OS I know is Windows.
I have installed Ubuntu server on my new home server, using the whole
120 GB SSD. Now I want to make a partition where I want to install
windows home server.
Is there an easy way to make a partition in Ubuntu, or should I rather make a fresh install
and create a partition in the process?
Will there be any problems installing windows home server on the other, new partition?

---

### Post by yancek on 2018-09-15
You will need to use software specifically designed for this such as GParted which is on the installation DVD/usb you used to install Ubuntu.  You can't modify partitions which are mounted and if you boot your installed system, it will have to be mounted.  The link below is to the GParted manual so review that and post back if you have specific questions/problems.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by oldfred on 2018-09-15
You say new system? That would be UEFI.
But then did you install Ubuntu in UEFI or CSM boot mode?
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
Post this:
sudo parted -l

Be sure to have good backups.

Note that for both Ubuntu & Windows how you boot install media UEFI or BIOS is then how it installs.
Windows only boots/installs to gpt partitioned drives with UEFI.
Windows only boots/installs to MBR(msdos) partitioned drives with BIOS.
If you force install in different mode, it will convert partitioning and erase entire drive.

      
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by karebo on 2018-09-16
[LEFT][COLOR=#000000][FONT=Ubuntubeta]Thank you for answers

Yes, the system is new, I was recommended MBD Supermicro X10SL7-F-O, which is not new (2013?) and runs BIOS.

I used Rufus 3.2.1397 to "burn" the ISO files to USB stick:
Ubuntu server settings: MBR/BIOS or UEFI/Fat32
Windows Home server settings: MBR/BIOS (or UEFI-CSM)/NTFS
Which means there will be no conflict if I install Windows after creating a partition?

I guess you understand that I am in a bit over my head here, but willing to learn, possibly by a few failures

yancek: "You can't modify partitions which are mounted and if you boot your installed system, it will have to be mounted"
Does this mean that I cannot create a new partition with Ubuntu already installed, that I will have to make a new installation and
create a partition (ie not choosing "use the Whole HD") in the process?

Edit:
confusing: I entered BIOS and found an insert: " UEFI Ubuntu"
What does this mean? An UEFI Ubuntu running on BIOS MBD?
Does this have any consequence for partitioning and installation of Windows Home Server?
[/FONT][/COLOR][/LEFT]

---

### Post by yancek on 2018-09-16
> [COLOR=#000000][FONT=Ubuntubeta]Does this mean that I cannot create a new partition with Ubuntu already installed,[/FONT][/COLOR]

No, not necessarily.  Depends upon the layout of your drive.  The point I was trying to make is that rather than using the installed Ubuntu you should use the DVD or USB you used to install Ubuntu.  Then open GParted and make sure the partitions are not mounted, the ones you want to modify.  THis is explained in the GParted link I posted above.  If you have questions after reviewing the link, post back. 

In your original post, you indicate that you have Ubuntu installed and working, is that correct?  If so, use the install DVD/USB and GParted to shrink the Ubuntu partition to make room for windows.  When you install windows, make sure you select the "CUSTOM" install option so that you can select the free/unallocated space you created with GParted.  If you don't do this, I expect windows will overwrite everything.  If you have an entry UEFI Ubuntu, that would indicate you have an EFI install of Ubuntu so you would need to install windows EFI also.  I would expect the windows installer to detect this.

---

### Post by karebo on 2018-09-16
I am sorry yancek, but beeing newbie in Ubuntu, not used to navigate in an OS by commands.
I have been Reading the GParted instruction but found no answer to the question: how do I start GParted from the USB?
If I put the USB stick in place and start the computer, I suppose the installed Ubuntu will start. So how do I open the USB GParted?

---

### Post by oldfred on 2018-09-16
Are you using the server version? It does not have gui apps.
You need to use the Ubuntu desktop live version and you start gparted once Ubuntu is running like any other gui app. Click in lower left corner.
But most very new users with server find command line a bit much. So they install a gui, but not the full desktop with all the gui apps. Many lightweight gui for a server like lxde or openbox or fluxbox. 

Always good to have a live installer or repair disk for current version of every operating system you have installed.

 Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Direct link to downloads page, most want  ubuntu-18.04-desktop-amd64.iso
[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

Both Windows & Ubuntu install in the boot mode UEFI or BIOS that you boot install media.
If drive is gpt, then you can only install Windows in UEFI mode, or if drive is MBR(msdos) you can only install Windows in BIOS boot mode, but it then must install to a primary NTFS partition with boot flag if you create one in advance. Default install normally uses two primary partitions.

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

