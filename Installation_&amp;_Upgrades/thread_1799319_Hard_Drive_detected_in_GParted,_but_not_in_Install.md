---
title: "Hard Drive detected in GParted, but not in Installation"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by monsieurdozier on 2011-07-07
I recently bought a computer offline, and I've been trying to install Ubuntu Server on it.  The hard drive is not being detected.  So I whip out the Desktop Edition, and Gparted can detect, format, and Ubuntu can open said drive no problem.  So I tried installing the Desktop Edition.  I get to the Prepare Partitions section, and the device is not listed.

The Device is a ST3160815AS SATA Drive.

It is in the BIOS as controlled by the IDE Controller, not RAID.

I'm using version 10.04 LTS for the Desktop.  Tried the 11.04 CD and this computer hates the new graphics and I'm getting a mostly black screen.  I can see the mouse and that's about it.

I don't understand why GParted can manipulate it just fine, but the controller can't.

Any help would be greatly appreciated.

---

### Post by conradin on 2011-07-07
you might want to do a checksum of the installation disk you are using, make sure its free of errors. Also check the bios and see if there is any compatability mode that sets how the IDE and SATA controlers work together.

---

### Post by srs5694 on 2011-07-07
Some additional information might be useful in helping to diagnose this problem:


[list]
[*]What chipset does the computer's motherboard use? If you don't know this, what is the make and model of the motherboard, or of the computer itself?
[*]Precisely what versions are you using, and with what results? You've mentioned desktop and server, and 10.04 and 11.04, but it's not clear to me which roles (desktop vs. server) link up with which version (10.04 vs. 11.04) and which of those combinations links up with which results, at least not for all cases. Note that new hardware sometimes requires driver support that may be absent in older distributions, so if you're using a new enough motherboard, it's possible that an Ubuntu 10.04 distribution would lack the drivers necessary to use the hard disk. (OTOH, if I'm reading your message correctly, you're saying that a 10.04 desktop worked better than some variety of server, so this may not be an issue.)
[*]Please describe *precisely* what you mean by "the hard drive is not being detected." In what part of the installation are you seeing a problem, and precisely what symptoms are you seeing? Your description sounds like the disk isn't showing up as an installation target at all; however, I've seen people use similar language to describe cases where the disk does show up as a target but with no partitions defined even though they exist. These are two very different problems.
[*]From a "live CD" that has this problem, the output of "ls /dev/sd*", of "dmesg | grep sda", and of "cat /proc/scsi/scsi" might be informative.
[/list]


There are a couple of things you can try to get around some of these problems in a generic way, but I can make no promises that they'll work for you specifically:


[list]
[*]Plugging the hard disk into a different connector on the motherboard can sometimes help get the disk recognized. This is because many motherboards provide two disk controllers, one of which may be supported and the other of which may not be. If you switch from an unsupported controller to a supported one, this will help.
[*]There's an "install Ubuntu in text mode" option on the Ubuntu 11.04 desktop DVD I've got. This might work around the video problems you mentioned, at least for the installation phase. It's conceivable that the video would begin working after installation (I've seen this happen), or you might need to reconfigure the video manually or even install a separate video card.
[/list]

---

### Post by monsieurdozier on 2011-07-07
I just finished the "Check Disc for errors" option, no errors showed up.

Here's the additional information requested:

ASUS M2A-VM Mother board

Northbridge: AMD 690G
Southbridge: ATI SB600

ATI SB600 chipset supports:
	 -	 1 x Ultra DMA 133/100/66/33 interface for two
		 (2) hard disk drives
	 -	 4 x Serial ATA 3.0 Gb/s hard disk drives supporting 	
		 RAID 0, RAID 1 and RAID 10 configuration

This is copied straight from the manual.  The manual is located [here]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CCYQFjAA&url=http%3A%2F%2Fdlcdnet.asus.com%2Fpub%2FASUS%2Fmb%2FsocketAM2%2FM2A-VM%2520HDMI%2Fe2976_m2a-vm-hdmi.pdf&rct=j&q=asus%20m2a-vm%20motherboard%20manual&ei=hvYVTrP4CZK50AG-7bRX&usg=AFQjCNFXw9jl0dXEhC-QJA4IRZs5A4dC2g&cad=rja").

So far I've tried 4 different versions with the following results:

Ubuntu 11.04 - 64 Bit - Server Edition:
I go through the installation process with no issues until I come to the Detect Discs portion.  I'm asked if I want to activate Serial ATA RAID Devices because one or more has been found.  Whether I click Yes or No the following screen only gives me these options: Configure iSCSI Volumes, Undo changes to partitions, or Finish partitioning and write changes to disk.  If I select the Finish partitioning option, I get the following message, "No root file system is defined.  Please correct this from the partitioning menu."

Ubuntu 10.04 - 64 Bit - Server Edition:
Same as Ubuntu 11.04 Server Edititon

Ubuntu 11.04 - 32 Bit - Desktop Edition:
*Installation Attempt*
In this attempt, I selected the Install Ubuntu option on the first screen. The next screen I do have a green checkmark by "has at least 4.4 GB available drive space"  On the Allocate drive space menu, the Device for boot loader installation is set to /dev/sda, with no other options in the drop down menu.  The box with the Device, Type, Mount Point, Format?, Size, and Used tabs is empty.  If I click Install Now, I get the same message as above, "No root file system is defined.  Please correct this from the partitioning menu."

*Try Ubuntu Attempt*
After clicking on the "Try Ubuntu" option, I get a black screen with the mouse.  That's it.

Ubuntu 10.04 - 32 Bit - Desktop Edtion:
*Installation Attempt*
Same as 11.04 Desktop Edition.

*Try Ubuntu Attempt*
This works as expected.  Not an issue.


If you look at the manual, on page 40 of the pdf or page 1-28 of the manual, I have the SATA cord connected to SATA1 in the illustration.

I'm going to fire up the Live CD now and post the results of the requested commands.  I appreciate all of the help so far.

---

### Post by monsieurdozier on 2011-07-07
ubuntu@ubuntu:~$ ls /dev/sd*
/dev/sda  /dev/sda1

ubuntu@ubuntu:~$ dmesg | grep sda
[    3.881479] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.881521] sd 0:0:0:0: [sda] Write Protect is off
[    3.881524] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.881545] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.881687]  sda:
[    3.914905]  sda1
[    3.915106] sd 0:0:0:0: [sda] Attached SCSI disk

ubuntu@ubuntu:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3160815AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVD-RW_GSA-H41N  Rev: RA00
  Type:   CD-ROM                           ANSI  SCSI revision: 05

---

### Post by srs5694 on 2011-07-07
First, your chipset is fairly old (at least 2007), so it's unlikely you're running into issues because of its age. The output from those commands indicates that your disk *is* being detected.

Second, concerning RAID configurations, those can be tricky. Has your hard disk ever been used in a RAID configuration of any sort? If so, there may be leftover data that's causing problems. There are ways to get rid of such data, but details depend on the type of RAID configuration, and I'm only passingly familiar with these techniques; others can better advise you on how to detect and get rid of such data, if it exists. I recommend you tell Ubuntu to *not* activate any RAID features if this is a stock installation to a single disk.

Third, it sounds like you're going through the configuration screens without defining partitions. Your description makes it sound like the 64-bit server edition isn't giving you the choice to define your partitions, but maybe I'm missing something. Your description for the 32-bit desktop edition clearly indicates that you *did* get such a screen, but it sounds like you didn't define your partitions. You must do so, and you must set a mount point for root (/), and ideally for any other filesystem partitions you create. (There may be options to do this automatically for side-by-side or replace-everything configurations, but these vary between Ubuntu versions and depending on what partitions are already present.) There are various guides online with screenshots, but the only one I happen to know offhand is [my guide for installing Ubuntu on Macs in EFI mode.](http://www.rodsbooks.com/ubuntu-efi/index.html) Most of this page will be irrelevant to you, but steps 16 and 17 show the screens you'll be using.

Whether you want to get the 64-bit server edition working or just install the 32-bit desktop version is up to you. There may be a disk setup option you're overlooking in the server edition that will bring you to a partitioning screen, but I can't promise that; my memory of the installation screens, particularly for the server versions, is foggy enough that I can't provide you with precise guidance on that score. Also, if leftover RAID data are causing you problems, you'll need to get somebody else's advice on how to clear it out. (My only suggestion is to completely erase the disk with "sudo dd if=/dev/zero of=/dev/sda" or a specialized DOS-based disk utility, which would probably take hours.)

---

### Post by monsieurdozier on 2011-07-07
I have no idea if the hard drive has been in a RAID setting or not.  I bought it used, so there's no telling really.  I'm trying the dd command now, to see if it helps.

I looked at the steps 16 and 17 in your guide, and I don't even see those screens.  I'll post a screenshot of what mine looks like.  I go from screenshot.png to screenshot-1.png.

I'll keep running the dd command, and get back with the results.

---

### Post by monsieurdozier on 2011-07-07
Well, after running the dd command everything installed like it should.  I'm having another problem with this board, but it's not hard drive or installation issues and I'll look for answers in another thread.

Thanks for all of the help.

---

### Post by srs5694 on 2011-07-07
I'm glad you got that particular problem cleared up!

---

### Post by Blasphemist on 2011-07-07
> **monsieurdozier said:**
> I just finished the "Check Disc for errors" option, no errors showed up.

Here's the additional information requested:

ASUS M2A-VM Mother board

Northbridge: AMD 690G
Southbridge: ATI SB600

ATI SB600 chipset supports:
	 -	 1 x Ultra DMA 133/100/66/33 interface for two
		 (2) hard disk drives
	 -	 4 x Serial ATA 3.0 Gb/s hard disk drives supporting 	
		 RAID 0, RAID 1 and RAID 10 configuration

This is copied straight from the manual.  The manual is located [here]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CCYQFjAA&url=http%3A%2F%2Fdlcdnet.asus.com%2Fpub%2FASUS%2Fmb%2FsocketAM2%2FM2A-VM%2520HDMI%2Fe2976_m2a-vm-hdmi.pdf&rct=j&q=asus%20m2a-vm%20motherboard%20manual&ei=hvYVTrP4CZK50AG-7bRX&usg=AFQjCNFXw9jl0dXEhC-QJA4IRZs5A4dC2g&cad=rja").

So far I've tried 4 different versions with the following results:

Ubuntu 11.04 - 64 Bit - Server Edition:
I go through the installation process with no issues until I come to the Detect Discs portion.  I'm asked if I want to activate Serial ATA RAID Devices because one or more has been found.  Whether I click Yes or No the following screen only gives me these options: Configure iSCSI Volumes, Undo changes to partitions, or Finish partitioning and write changes to disk.  If I select the Finish partitioning option, I get the following message, "No root file system is defined.  Please correct this from the partitioning menu."

Ubuntu 10.04 - 64 Bit - Server Edition:
Same as Ubuntu 11.04 Server Edititon

Ubuntu 11.04 - 32 Bit - Desktop Edition:
*Installation Attempt*
In this attempt, I selected the Install Ubuntu option on the first screen. The next screen I do have a green checkmark by "has at least 4.4 GB available drive space"  On the Allocate drive space menu, the Device for boot loader installation is set to /dev/sda, with no other options in the drop down menu.  The box with the Device, Type, Mount Point, Format?, Size, and Used tabs is empty.  If I click Install Now, I get the same message as above, "No root file system is defined.  Please correct this from the partitioning menu."

*Try Ubuntu Attempt*
After clicking on the "Try Ubuntu" option, I get a black screen with the mouse.  That's it.

Ubuntu 10.04 - 32 Bit - Desktop Edtion:
*Installation Attempt*
Same as 11.04 Desktop Edition.

*Try Ubuntu Attempt*
This works as expected.  Not an issue.


If you look at the manual, on page 40 of the pdf or page 1-28 of the manual, I have the SATA cord connected to SATA1 in the illustration.

I'm going to fire up the Live CD now and post the results of the requested commands.  I appreciate all of the help so far.

You may hate me for this but here goes. Double click on the partition and choose to put root (/) on it. I know it isn't real obvious to do the double click.

---

### Post by monsieurdozier on 2011-07-08
> **Blasphemist said:**
> You may hate me for this but here goes. Double click on the partition and choose to put root (/) on it. I know it isn't real obvious to do the double click.

The problem I was having is that the partition selection screen was not showing at all.  If you look at the screenshots posted, you can see what I was talking about.

It seems the problem was leftover RAID data.  After wiping the disc, everything worked.

---

