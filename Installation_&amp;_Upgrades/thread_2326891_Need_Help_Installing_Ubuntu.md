---
title: "Need Help Installing Ubuntu"
date: 2016-06-05
forum: Installation &amp; Upgrades
---

### Post by Mike_Stampone on 2016-06-05
I purchased a SanDisk Ultra USB 3.0 32GB flash drive today to install Ubuntu 16.04 LTS 64-bit on my desktop computer.  I followed the installation instructions by using Startup Disk Creator on my Ubuntu laptop.  So I have a bootable USB flash drive.  I am trying to install on a Samsung PRO 950 m.2 hard drive and my motherboard is Z170A GAMING M5 made by MSI.  Sometimes the installation completes.  In that case it tells me to reboot, but it never actually boots up.  Otherwise,during the install process it might say fatal error, something about not being able to install on /dev/nvme01xxx (my m.2 hard drive).  I have looked at the BIOS and the only thing I can see of interest is Boot Mode which reads UEFI+Legacy.  I've tried to install different ways about 10 times today.  If it helps I was able to install Linux Mint but it didn't come with a driver for my ethernet so I gave up on that.  I also tried installing Ubuntu using the dd write method, YUMI, and RUFUS none of which worked.  The one which got furthest (complete install but no boot) was the dd method and Startup Disk Creator method.  Please help!  I am a computer programmer and this is really stressing me out because I need to get back to work!

---

### Post by jeremy31 on 2016-06-05
What version of Ubuntu?  Strange that Linux Mint would install as their latest version is based on Ubuntu 14.04.

I am not sure what is going on unless it has something to do with initramfs and it needs nvme to be put in /etc/initramfs-tools/modules

Can you use try without installing when booting to the USB flash drive?

---

### Post by Mike_Stampone on 2016-06-05
Thanks for the quick reply.

> What version of Ubuntu?
Ubuntu Desktop 16.04 LTS.  I downloaded it this morning.

Linux Mint I was able to "Try without Installing".  If I do that with the Ubuntu USB I get the beautiful purple screen and mouse but I never get past that point.  Actually I can see an error message flicker starting at the top left of the screen and gradually descending down the screen as it flickers.  It's the familiar "Something went wrong" message.  It's all very odd.

---

### Post by jeremy31 on 2016-06-05
Do you still have the Mint ISO on a USB drive, or can you put it back on one?

If you can, boot it up, go into file manager and then under devices there should be a hard drive icon and if windows is installed there may be 2.  Click on the hard drive icon and move to /etc/initramfs-tools/ and then double click on modules and see if nvme is an entry there.

This is really starting to get out of my comfort zone, so I hope someone else that has one of these drives will post.  I am almost positive the fix involves mounting the drive from a Live USB and using change root to update the initramfs after adding nvme to /etc/initramfs-tools/modules

---

### Post by Mike_Stampone on 2016-06-05
I reinstalled Mint.  The file modules in /etc/initramfs-tools/ looks like a default.  It's just a bunch of commented lines starting with #.  By the way don't feel bad if something gets messed up.  Ubuntu is the only OS I want so there is nothing to screw up.  Please give me any and all hair-brained ideas you may have.  I'm a programmer so I'm very used to banging my head against the wall until something works :D

---

### Post by grahammechanical on 2016-06-05
Do you have any other OS installed? If there is another OS and it is windows 8 - 10 and it is installed in EFI mode, then Ubuntu must be installed in EFI mode and to do that we run the live session in EFI. Otherwise there will be boot problems. If Ubuntu is the only OS then it makes no difference whether Ubuntu is installed in EFI mode or BIOS/Legacy/CSM mode

There are other precautions to take with Windows 8 - 10 installed.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

What install option are you choosing? Erase disk and install Ubuntu? Or Something Else? NVMe indicates a solid state drive.

[https://en.wikipedia.org/wiki/NVM_Express](https://en.wikipedia.org/wiki/NVM_Express)

You seem to be mentioning 2 different problems. 1) failure to install on /dev/nvme01. 2) a completed install that fails to load to a working desktop environment. To give help for problem #2 we need to know how far the loading process goes. Do you see a boot menu (Grub)? If Ubuntu is the only OS we do not see the Grub boot menu.

Regards.

---

### Post by Mike_Stampone on 2016-06-05
Only one OS.  I'm choosing Erase disk and install Ubuntu every time.  Sorry if I was unclear.  I'm trying to install Ubuntu on my Samsung m.2 hard drive which is the /dev/nvmexxx.  I get as far as the message which says the installation of Ubuntu was successful.  Then I click the button to reboot.  At this point I get nothing.  The computer crashes and restarts if I remember correctly.  Sorry it's been a long day of troubleshooting, my mind is foggy.  Yeah only one OS so no GRUB boot menu.

Edit:
Just tried installing Ubuntu again.  Got the following message.

Title: Unable to install GRUB in /dev/nvme/
Message: Executing 'grub-install/dev/nvme/' failed. This is a fatal error.

Then I click the only button "OK".  Then I get the following.

Title: Bootloader install failed
Message: Sorry, an error occurred and it was not possible to install the bootloader at the specified location.  How would you like to proceed?
Options:
1. Choose a different device to install the bootloader on (drop down menu).
2. Continue without a bootloader.
3. Cancel the installation.

If I select options 2 or 3 I cannot click the OK button below as it's grayed out (disabled).  I have no idea what to do from here.

---

### Post by oldfred on 2016-06-06
I suggest partitioning in advance but download the very newest gparted so it works with the new NVMe drive.
 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[http://ubuntuforums.org/showthread.php?t=2318570](http://ubuntuforums.org/showthread.php?t=2318570)

 Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162) 


Are you installing in BIOS or UEFI boot mode?
If only installing Ubuntu I suggest gpt partitioning, but it needs the ESP - efi system partition for UEFI boot and/or bios_grub partition for BIOS boot. Even though I typically only boot one way or the other, I install with both partitions at beginning of drive.

       
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by jeremy31 on 2016-06-06
Have you tried "Something Else" when trying to install 16.04 and change the bootloader device to something like nvme0n1 to see if it works then?  It may help to have BIOS set to UEFI only.  This is a bug that has been reported during 15.10.

---

### Post by Mike_Stampone on 2016-06-06
Changed my BIOS to "Boot Mode: UEFI".  Then I installed GParted using the method recommended on their website.  From there I booted from USB and did the following:

1. Remove all partitions to start from entirely unallocated space.
2. Add 550 MiB Primary efi
3. Add 16 GiB Primary linux-swap
4. Add 452.98 GiB Primary ext4
5. Add the boot and esp flag to the efi partition

I wasn't able to change from "Primary" to anything else.  Maybe I missed something as it's my first experience with GParted outside the one built into the Ubuntu installer.

Then I booted into the Ubuntu installer via USB.  When it asked I knew to choose "Something Else" and pressed "Install".  It told me something about no root directory so I started modifying the partitions.  Here's what I did.

1. Selected "EFI System Partition" for the efi partition
2. Selected "swap area" for the linux-swap partition
3. Selected "Ext4 Journaling File System" and "/" (root) for the ext4 partition.

Then it seemed to install fine, just as before.  When I see "Success you need to reboot" I clicked the button.  Then, strangely, the computer goes to a black screen and shows the following:

[3.572845] nouveau 0000:01:00.0: gr:failed to load fecs_inst

I manually held the power button as I was stuck at this screen for over five minutes with no sign of forward movement.  When I turn it back on I see a solid purple screen, not the usual Desktop background.  Then the screen goes black, and within seconds after the computer reboots to the purple Desktop background.  My mouse is working and I see the flickering "Something Went Wrong" message box again.  This time I manage to click the "Show Details" and 100 flickers later I manage to get some of the info from the box:

Executable Path: /usr/bin/compiz
Package: compiz-core 1:0.9.12.2+16.04.20160415-0ubuntu1
Problem Type: Crash
Title: compiz crashed with SIGILL
.tmp.unity_support_test.1

There was more info but the flicker was giving me a headache.  If you guys want all the info from that message just ask and I will suffer through.

---

### Post by oldfred on 2016-06-06
With gpt partitioning there is no primary, extended or logical partitions. They all are one type essentially primary.

It now sounds like video problem. What nVidia card?

If UEFI, you press escape key before grub loads, to get grub menu.
       # Usually nVidia or AMD work with this:
nomodeset 

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

Or can you boot recovery mode, or second line in grub menu. It has nomodeset already.

If you can get to command line:

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  
   sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 

But if very new nVidia card you may need to add ppa to get newer nVidia driver than in Ubuntu repository.
      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by squirrel3 on 2016-06-06
It looks to me as though you're making it complicated for yourself. FYI, make sure you're installing to your HDD and not your USB. Hope this link helps.

[https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)

---

### Post by Mike_Stampone on 2016-06-07
You were right oldfred.  It was a graphics card problem.  This was the silver bullet.

sudo ubuntu-drivers autoinstall

Thanks to all who helped.  Can I report this issue somewhere to make Ubuntu better in the future?  If so, what details should I include?

---

