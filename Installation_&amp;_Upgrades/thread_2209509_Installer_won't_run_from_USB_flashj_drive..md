---
title: "Installer won't run from USB flashj drive."
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by akmartinez1 on 2014-03-06
Hello anyone/everyone,

I'm trying to install Ubuntu 13.x 32-Bit from a USB Flash Drive onto a Lenovo IdeaPad S10-3.

I created a bootable USB Flash Drive with Ubuntu 13 32-Bit.  t boots fine on my Lenovo IdeaPad S10-3 fine but whenI click on the Install USB icon from the bar on the left it does nothing.

I'm trying to install a DuaL Boot setup on my IdeaPad with Windows 7.  I've already shrunk the main partition to free up 128Gb of drive space for Ubuntu with the remaining for the already installed Windows 7.  There are a couple of other partitions on the drive already mainly for the recovery and QuickStart for the netbook that was already installed and I don't want to change it.

Is there something that I need to do to get the installer to run?

I've installed a dual boot before following directions I found online and it worked.  I just can't get it to work on this particular system.

I know the flash drive works ant the installation of Ubuntu onit works, in fact I'm using Firefox from the flash drive to get to this site and search for help.


I've very new to Ubuntu/Linux.

Any help would be appreciated.

---

### Post by oldfred on 2014-03-06
Most Windows 7 systems use all 4 primary partitions.

Post this:
sudo parted -l

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Xubuntist on 2014-03-06
Go back into Windows and [download Rufus](http://bootableusb.net/wp-content/uploads/2014/01/rufus.rar). You'll find [instructions on how to use it here](http://bootableusb.net/install-windows-ubuntu-usb-drive-using-rufus/). Works like a dream for me.

---

### Post by akmartinez1 on 2014-03-07
Well, after attempting to install last night and posting my original question I removed the USB flash drive and tried to boot back into windows and now that's not working.

When I boot I get my Windows menu to boot into recovery mode or to boot normally.

When I boot normally it looks like it starts and a quick blue screen flashes with what looks like error information then reboots and it's all so quick I can't see what it says or can't seem to freeze it.

When I boot into recovery mode it starts Windows into a repair mode and dialog box to check for an automatic fix that it won't exit out of.

When I try to let it check for an automatic fix I get a return that it can't find a fix and I can then get into advanced mode repair and I don't know what to do from there.

Does anyone have any suggestions for this now?

I'll try to do some research but I'm hoping to get some quick suggestions on what to do from here.  I don't want to lose any data on the system because of all the work that has already been done to it with upgrading the version of windows and installing office (because I can't seem to find my installation keys after 5 years).  

Any help would be appreciated!  Thanks!

---

### Post by oldfred on 2014-03-07
Is the autofix running chkdsk. That can take a while if partition is large.
And change to Windows partition size requires a Windows chkdsk. 
Always best to change Windows partition size with Windows tools and immediately reboot so it can run its chkdsk and make whatever repairs it needs for its new size.
With dual booting do not hibernate Windows or you will have issues.

---

### Post by akmartinez1 on 2014-03-07
When I started I did shrink the main volume to free up 128Gb of drive space for the Ubuntu installation.

After the space was shrunk I did do a reboot and booted back into windows and it was working, so I'm assuming that after the re-size Windows did its thing to make sure everything was working.  The total hard drive size is about 640Gb.

Initially there were 4 partitions, but I don't remember the complete make up of the partitions. The first partition I'm assuming is for the manufacturer recovery image if I wanted to restore to factory config when delivered new.  The second partition was the main Windows partition which was C:, the third partition was some amount of space labeled Lenovo for drive D:, and the 4th was some amount of space that I'm assuming was for something that Lenovo called the Quick Start so that  you can start the system super fast into a base configuration that only had a browser, network connectivity, and a few other utilities they thought would be handy.  This QS did not require any kind of log in or anything and I'm not sure what kind of OS it is running on.  It didn't look like Windows.

Every seems to be working OK except for Windows.  I don't think all is lost yet because it actually does load the Windows recovery tools asking if I wanted to restore to a previous restore point or do some checks and such but it's just not successful enough to let Windows boot correctly.  When it does the restore to a restore point it actually asks me for my password which works, just doesn't restore successfully.

What finally did work last night though was the Ubuntu installation.  I tried it again to install onto the free space that I created and it works.  GRUB launches and asks me which to boot, and the Ubuntu install works just perfectly now.  It's the Windows side that doesn't work.  It's an option in GRUB and when I select it I still get the same results as described earlier.

When I try the advanced options from the Windows recovery it fails and gives me an error log.  Once thing I noticed was that it said something abut E:\Windows...something...something failed...  Is my problem that it's looking at an incorrectly assigned drive letter?  Why E: and not C:?

I did see some posts that others said might or has worked about /fixmbr or /fixboot.  I'm going to look it up again and see what I can learn but I'll wait for more information here before going any further.

---

### Post by oldfred on 2014-03-07
Grub only boots working Windows, so you need to fix whatever the issue is with Windows.

May be better to just temporaryly install the Windows boot loader. You can use the fixMBR command or Boot-Repair will install a generic Windows boot loader. Once Windows is fixed then you will need to boot Ubuntu live installer and use Boot-Repair to reinstall grub2's boot loader to MBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

