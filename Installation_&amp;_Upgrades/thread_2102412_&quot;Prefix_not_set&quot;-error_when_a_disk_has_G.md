---
title: "&quot;Prefix not set&quot;-error when a disk has GPT"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by Bufeu on 2013-01-07
Hi!
A friend of me wanted to try Linux, and I recommended him to try Ubuntu. I gave him my CD of Ubuntu 12.04 (x64). Yesterday, he said that Ubuntu didn't work at all, so went to his house to see with my own eyes what was wrong.

When he booted his computer from the CD a message "error: prefix not set" flashed by, followed by a GRUB menu. The options "Try Ubuntu", "Install Ubuntu" and "Check the disk for errors" was there, but if you tried to choose one of the options, the messages " error: couldn't load file" and  "error: need to load kernel first" showed up. I went home and checked the disc. No problem at all. I also, re-downloaded the .iso and reburned it, but without success. So we tried the classic method, disconnect the hardware, part by part. We found out that his HDD was the problem (he has one SSD and two HDDs). It has a 4 TB partition and as GPT-table instead of MBR. Without the HDD, GRUB successfully booted Ubuntu from the live-CD.
So, why doesn't GRUB like GPT? Is the GPT-table the problem, or it is the huge partition that is the problem? Any idea how to solve it?

---

### Post by oldfred on 2013-01-07
Gpt is not the issue. I have been using gpt since 10.04 but on smaller drives. I have it on my 160GB drive, my SSD & my flash drive I use for installs using grub to directly boot isos. And I have two other drives with MBR. 

And we have seen users with very large RAID configurations which of course had to be gpt.

First is BIOS/UEFI set for AHCI? That should be set for SSD anyway. Not sure if any other BIOS settings may make a difference.

These are all BIOS issues that users have reported, of course most will not apply. :)

       Some issues on booting install:
fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.
Though my drive was appearing in the bios and working for install it was actually "disabled"! 
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size or very large / partition over 100GB
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive that is now MBR
Disable Quickboot in BIOS
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply
Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!
lib64 folder missing??
[http://ubuntuforums.org/showthread.php?t=2069764](http://ubuntuforums.org/showthread.php?t=2069764)

---

### Post by Bufeu on 2013-01-07
> **oldfred said:**
> Gpt is not the issue. I have been using gpt since 10.04 but on smaller drives. I have it on my 160GB drive, my SSD & my flash drive I use for installs using grub to directly boot isos. And I have two other drives with MBR. 

And we have seen users with very large RAID configurations which of course had to be gpt.

First is BIOS/UEFI set for AHCI? That should be set for SSD anyway. Not sure if any other BIOS settings may make a difference.

These are all BIOS issues that users have reported, of course most will not apply. :)

       Some issues on booting install:
fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.
Though my drive was appearing in the bios and working for install it was actually "disabled"! 
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size or very large / partition over 100GB
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive that is now MBR
Disable Quickboot in BIOS
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply
Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!
lib64 folder missing??
[http://ubuntuforums.org/showthread.php?t=2069764](http://ubuntuforums.org/showthread.php?t=2069764)Hmm..? But you never had a partition bigger than 2 TiB (the limit for MBR)?

His configuration (to make it more clear):
Drive 1 (SSD):
120 GB NTFS-partition with MBR

Drive 2 (HDD):
1 TB NTFS-partition with MBR

Drive 3 (HDD):
4000 GB NTFS-parttion with GPT

EDIT: Yes, AHCI is set in the BIOS. My friend just checked.

---

### Post by darkod on 2013-01-07
> **Bufeu said:**
> Hmm..? But you never had a partition bigger than 2 TiB (the limit for MBR)?

His configuration (to make it more clear):
Drive 1 (SSD):
120 GB NTFS-partition with MBR

Drive 2 (HDD):
1 TB NTFS-partition with MBR

Drive 3 (HDD):
4000 GB NTFS-parttion with GPT

I wouldn't say the issue is the size of the gpt partition. Whether it's bigger or not than the msdos (mbr) limit is not important, that's why you use gpt because it's above the mbr limit. I can't see how the mbr limit would interfere on gpt disk.

I don't have 4TB disk to test, but I do have two new 2 x 2TB disks in my home server with gpt tables, one small root partition and the rest one huge partition, which means almost 2TB minus 10-15GB for root (don't remember exactly right now).
This is my home server so it has the server OS but it works excellently.
And I booted it with the live cd when installing because I wanted to manually prepare the partitions first, and then I started the server cd install.
So, the live cd had no problems booting the machine and preparing 2 x 2TB disks with gpt table and big 2TB partitions.

---

### Post by Bufeu on 2013-01-07
> **darkod said:**
> I wouldn't say the issue is the size of the gpt partition. Whether it's bigger or not than the msdos (mbr) limit is not important, that's why you use gpt because it's above the mbr limit. I can't see how the mbr limit would interfere on gpt disk.

I don't have 4TB disk to test, but I do have two new 2 x 2TB disks in my home server with gpt tables, one small root partition and the rest one huge partition, which means almost 2TB minus 10-15GB for root (don't remember exactly right now).
This is my home server so it has the server OS but it works excellently.
And I booted it with the live cd when installing because I wanted to manually prepare the partitions first, and then I started the server cd install.
So, the live cd had no problems booting the machine and preparing 2 x 2TB disks with gpt table and big 2TB partitions.So, what else would be the problem? It works fine without the 4 TB-drive.

EDIT: Your partition wasn't bigger than 2 TiB, right?

---

### Post by darkod on 2013-01-07
> **Bufeu said:**
> So, what else would be the problem? It works fine without the 4 TB-drive.

EDIT: Your partition wasn't bigger than 2 TiB, right?

Right. The whole disk is 2TB which is less than 2TiB and that makes it impossible for any partition to be larger than 2TiB.

Have tried changing places of the disks on the motherboard? Even better, can you try with only the 4TB disk connected? Regardless where you want to install, having only the 4TB disk can show if it maybe boots with it into live mode from the cd or not. Test it in various sata ports.

I have no idea, honestly. But it would be very weird the GPT to be issue since that's what GPT started to get used for, large partitions.

---

### Post by Bufeu on 2013-01-07
> **darkod said:**
> Right. The whole disk is 2TB which is less than 2TiB and that makes it impossible for any partition to be larger than 2TiB.

**Have tried changing places of the disks on the motherboard?** **Even better, can you try with only the 4TB disk connected?** Regardless where you want to install, having only the 4TB disk can show if it maybe boots with it into live mode from the cd or not. **Test it in various sata ports.**

I have no idea, honestly. But it would be very weird the GPT to be issue since that's what GPT started to get used for, large partitions.Good ideas. I'll try that as fast as I can, maybe tomorrow. It's a very strange problem, though.

---

### Post by oldfred on 2013-01-07
I have had gparted not show my XP drive even though XP booted. I then ran chkdsk on the XP partition and the drive then showed in gparted & XP booted a bit faster. But running chkdsk on a 4TB drive may take a long time.

---

### Post by Bufeu on 2013-01-08
> **darkod said:**
> Right. The whole disk is 2TB which is less than 2TiB and that makes it impossible for any partition to be larger than 2TiB.

Have tried changing places of the disks on the motherboard? Even better, can you try with only the 4TB disk connected? Regardless where you want to install, having only the 4TB disk can show if it maybe boots with it into live mode from the cd or not. Test it in various sata ports.

I have no idea, honestly. But it would be very weird the GPT to be issue since that's what GPT started to get used for, large partitions.
Tried, but with the 4TB disk connected (only), Ubuntu (from live-CD) didn't boot either... :-(
If any of the other disks is connected, Ububtu boots. Therefore, my conclusion is that it has spmething with GRUB and the big partition to do. Any ideas?

---

### Post by oldfred on 2013-01-08
Back with 10.04 I did have issues booting from gpt and trying to use MBR in XP. I had to explicitly add commands to tell it I was changing from gpt to MBR. Now partitions are labeled with hd0, gpt1 or hd1, msdos2.

Grub used to have a drivelist file, but they did away with it and I think they just scan attached drives or look at BIOS list of drives. But if scanning and not able to read gpt perhaps that is an issue. I do not know if you can add both an insmod part_gpt and insmod part_msdos in the same boot stanza? With my mixed MBR & gpt system I only have one or the other depending on where I am booting from.

Are you perhaps booting from gpt drive but install is in MBR drive?

---

### Post by Bufeu on 2013-01-09
> **oldfred said:**
> Back with 10.04 I did have issues booting from gpt and trying to use MBR in XP. I had to explicitly add commands to tell it I was changing from gpt to MBR. Now partitions are labeled with hd0, gpt1 or hd1, msdos2.

Grub used to have a drivelist file, but they did away with it and I think they just scan attached drives or look at BIOS list of drives. But if scanning and not able to read gpt perhaps that is an issue. I do not know if you can add both an insmod part_gpt and insmod part_msdos in the same boot stanza? With my mixed MBR & gpt system I only have one or the other depending on where I am booting from.

Are you perhaps booting from gpt drive but install is in MBR drive?Please read my first post. I recommended Ubuntu to a friend, but Ubuntu only boots from livd-CD when the 4TB-drive is disconnected. We tried yesterday with only the 4TB-drive connected, but it didn't work either.He currently has Windows installed, of course.

---

### Post by Bufeu on 2013-01-09
No ideas what's the problem and how to make GRUB boot Ubuntu?

---

### Post by oldfred on 2013-01-09
Does BIOS see 4TB drive correctly or is external? 
Back to BIOS settings or BIOS needing an update to work with very large drives.

Edit.
Are you sure you have the 64bit version of Ubuntu? It does not fit on a CD anymore, so you need DVD or flash drive to be able to correctly install.

---

### Post by Bufeu on 2013-01-10
> **oldfred said:**
> Does BIOS see 4TB drive correctly or is external? 
Back to BIOS settings or BIOS needing an update to work with very large drives.

Edit.
Are you sure you have the 64bit version of Ubuntu? It does not fit on a CD anymore, so you need DVD or flash drive to be able to correctly install.
What do you mean with if BIOS sees the drive correctly?

Yeah. Of course I'm sure it's 64bit (the .iso-file is named "ubuntu-12.04.1-desktop-amd64.iso").

---

### Post by oldfred on 2013-01-10
If BIOS does not report drive & size correctly, operating systems will not work with drive correctly, so it still could be a BIOS issue. What mode is BIOS, lba, large, ide, AHCI?

---

### Post by Bufeu on 2013-01-10
> **oldfred said:**
> if bios does not report drive & size correctly, operating systems will not work with drive correctly, so it still could be a bios issue. What mode is bios, lba, large, ide, ahci?AHCI. What? Does BIOS report the size of the drive?

---

### Post by Bufeu on 2013-01-11
No ideas/solutions?

---

### Post by oldfred on 2013-01-11
What mode is drive in? LBA, Large, AHCI or IDE?

---

### Post by Bufeu on 2013-01-11
> **oldfred said:**
> What mode is drive in? LBA, Large, AHCI or IDE?
Quoting myself...
> **Bufeu said:**
> **AHCI.** Does BIOS report the size of the drive?

---

### Post by oldfred on 2013-01-11
Sorry, Missed that was the answer.

I am out of ideas, but lets run BootInfo and see if it says anything else. It may or may not boot as it has some slightly different configurations.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

---

### Post by Bufeu on 2013-01-11
> **oldfred said:**
> Sorry, Missed that was the answer.

I am out of ideas, but lets run BootInfo and see if it says anything else. It may or may not boot as it has some slightly different configurations.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)But the computer can't even boot with a live-CD without removing the 4TB-disk, and that is the problem.

---

### Post by oldfred on 2013-01-11
Will it boot gparted liveCD or Knoppix or any of the other repair type Linux systems?

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

    
[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)

---

### Post by Bufeu on 2013-01-11
> **oldfred said:**
> Will it boot gparted liveCD or Knoppix or any of the other repair type Linux systems?

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

    
[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)
Don't know. Should we test that, with the 4TB-disk connected?

---

### Post by Bufeu on 2013-02-13
I don't know how, but I cloned the disc to a USB flash drive using *dd*, and Ubuntu booted. :)

---

### Post by oldfred on 2013-02-13
So is it just a defective drive? 

Even new drives can be defective.

---

### Post by Bufeu on 2013-02-15
> **oldfred said:**
> So is it just a defective drive? 

Even new drives can be defective.
No, the drive wasn't defective. Ubuntu just didn't want to boot using a CD. Don't ask me why...

---

