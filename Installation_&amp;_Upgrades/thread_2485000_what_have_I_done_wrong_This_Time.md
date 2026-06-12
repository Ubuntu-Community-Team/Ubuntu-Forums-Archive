---
title: "what have I done wrong This Time?"
date: 2023-03-17
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2023-03-17
Once again, a little knowledge has proved a dangerous thing.

I was installing Ubuntu 22.04 last night.
everything seemed to be going smoothly and it got to the "Installation Complete. Restart the Computer" stage.
but when I clicked on Restart and removed the USB stick everything seemed to go haywire and freeze up.
after I forced a restart I got a message "No Boot Device Found"

I expect I messed something up when I shaved off 20GB as a partition for the Ubuntu install.
Following some instructions I found I thought I had set up:
- a 250mb efi (UEFI bootloader)
- a swap (temporary storage) area
- a 24GB / (Linux system) install partition with / as the boot point

my error messages and a screenshot of my current partition structure are attached.

Can anyone advise how I correct this?

---

### Post by MAFoElffen on 2023-03-17
Let's see. Where should I start on telling you what I see there. This might be a very long winded. I see your problems and I feel your pain.

Is Windows setup on that as Legacy Boot? That is what I see, even though, by default, Windows should have probably have originally been installed as UEFI... On a disk with a GPT partition table... But it isn't.

You created an "efi" folder on a computer that is setup as Legacy boot. Which in Legacy mode, is not even going to see, or even look for it. On MBR/msdos partition tabled disks, the Grub2 bootloader installs to the start of the disk, in what is called the boot sectors, before the first partition.

Then the original partition table, if you check the details on it in GParted, most likely says MBR/msdos partition table... MBR/msdos partition table are limited to only 4 primary partitions or 3 primaries and an extended partition. That is why it had to create an extended partition, with the additional logical partitions within it.

You could always convert it as it should be (UEFI Boot, GPT disk), but that would take some time and work...

Before I go into a recommendation on a solution, do you have good backups to restore from? And are you trying to install Desktop or Server Edition? And did you shrink the Windows NTFS partition with GParted or Windows Disk Manager?

---

### Post by yancek on 2023-03-17
Which version of windows do you have installed?  Was it preinstalled or did you or someone else install it?  It certainly appears to be a Legacy/CSM install as you have an Extended partition with logical partitions.  Wiindows won't install UEFI on an msdos drive, it needs to be GPT.  If in fact, windows is installed in Legacy mode and Ubuntu is installed in UEFI mode and both are on the same drive, you will not be able to boot windows from Grub.  If you check the drive type and find it is msdos, the simplest solution would be to reinstall Ubuntu to the same partition after ensuring Legacy mode is set in the BIOS.  Best to delete the EFI partition.

---

### Post by pjstock on 2023-03-17
I am trying to repurpose an old decomissioned  box that came with Windows 7 preinstalled on it. 
there is nothing on the computer that needs to be saved or backed up.
I would use Ubuntu 99.5% of the time but from time to time I find I have to drop into Windows to do certain things (like print to an old printer that only supports Windows - though that is a rare occurrence)
Windows 7 was the last version of Windows that I could tolerate (I would never "advance" to W10 for instance)
but I do not have the W7 install disks and so could not reinstall it if I wiped it out.

Hmmm, I have just now read up a bit on Legacy Boot (or is it Legacy BIOS) vs UEFI.
But I don't yet understand the pros and cons of either, which I should use and how I force one or the other.

on my other Ubuntu systems when I power up I get that list of Boot options with Ubuntu as the default.
But I expect my other installs succeeded more out of good luck than good design.

what I do want to do is keep the Ubuntu system files separate from my data and prevent my everyday data (like downloads) from gobbling up the 20+GB allocated for system files. I have had that problem in the past and found myself having to constantly delete files from the Ubuntu system area to keep it from running out of space.

to answer your questions:
do you have good backups to restore from?  there is nothing on this computer that needs to be saved or backedup. though if I wipe out W7 i don't have disks to reinstall it. losing W7 would not be the end of the world. But I would like to learn how to do this elegantly, purposefully.

And are you trying to install Desktop or Server Edition?  I would only use this system as a standalone PC. so I expect that would be Desktop edition.

And did you shrink the Windows NTFS partition with GParted or Windows Disk Manager? 
I used Windows Disk Manager to shave a 25GB chunk of disk off the approx 480GB main storage partition. I didn't touch the Windows partition. (ooops and now I cannot as I can't make anything boot.)

---

### Post by Impavidus on 2023-03-17
If you will be primarily using Ubuntu, it doesn't make much sense to keep that Windows partition that large. Maybe shrink it to 200GB (can be even smaller) and make a 200GB /home partition with a Linux filesystem.

Recent versions of Ubuntu automatically create an EFI partition when you install, even when installing in legacy mode. It won't be used. It shouldn't really do any harm. A 24GB root partition is doable, but may be a bit tight. There's plenty of room on your hard drive; it won't hurt to increase that to 30 or 35GB.

---

### Post by pjstock on 2023-03-17
I'll state the obvious: "I Don't Understand"

I thought I had a 12GB windows partition (/dev/sda2) (though I see it is labelled "RECOVERY")
I tried to create a 24GB ubuntu partition (/dev/sda6)

and I hoped (though working with LInux/Ubuntu is not based on "hope") that they could each share a 238GB data partition /dev/sda5
( I would like to not have as little as half the 238GB partition for data, depending on which OS I was using)

but it all might not work like that.

I swear, if I can pay attention to this install process, I will write it all up from a layperson's perspective.

questions.
How do I revive the W7 install?
How do I proceed from here?
and finally, why has what I hoped to do not worked out?

Peter

---

### Post by ubfan1 on 2023-03-17
The Windows 7 operating system is on the 438GB partition, on an MSDOS partitioned disk, therefor in legacy mode.  Your Ubuntu install could have been in either mode, depending upon machine settings (and maybe how your boot media was created). The standard install ISO boots in both UEFI and legacy, so up to the machine settings.  Some machines allow you to set a preference, UEFI over legacy etc. when both are possible.  If you didn't touch the Windows partition (like not formatting it), it should still boot from the legacy Windows boot loader at the beginning of the disk. Check your machine settings (UEFI settings/BIOS ) to see that it is not in UEFI mode (CSM is legacy).  Change it to CSM is necessary and Windows might boot again.

Without the Windows install media, I don't know how you'd restore the Windows boot loader, but grub in legacy mode should boot Windows and Ubuntu on your machine.  I guess these days, you could write data files onto your ntfs Windows partition from Ubuntu, but I usually dedicate a FAT partition for sharing.  Used to be issues with the Linux ntfs drivers, but the basic stuff is probably OK.

---

### Post by Impavidus on 2023-03-18
You've got a 12GB Windows recovery partition and a 430GB main Windows partition, with the OS, applications and documents. You created a 24GB Ubuntu partition. There is no 238GB partition, but your sda5 is a 238MB partition, so you misread. It's an automatically created EFI partition that has no use here.

---

### Post by pjstock on 2023-03-19
ahhh yes, I did misread that.
in any event, I won't be back at this machine for a week. I'll try again then.
I think I will just assume the WIndows 7 is toast and so I'll just do a straight Ubuntu install

---

### Post by pjstock on 2023-04-03
I am back at that computer I was struggling with last week.
I was going to just forget about the WIndows install and wipe everything and just do a straight Ubuntu 22.04 install.

BUT as I start that process I gett a message "this computer currently has WIndows 10 and Ubuntu 22.04 installed....." etc.

First, let me go back and reread everyone's comments to date.

Okay, I have reread comments.

I also checked the BIOS on this machine and it is currently set to Legacy Boot.

Why is it saying there is Windows 10 on here when IIRC it only ever had Windows 7 (maybe it had Windows 10. this is a family membver's castoff computer.)

And looking at the partition map again, it is still all Greek to me. 

I "thought" I had partitioned the big 500GB HDD (isn't that sda?) into 
sfa2 ntfs 12GB for Windows
sda6 ext4 25GB for Ubuntu
and the rest 416xxxMB for data.

but then there seems to be a lot of other junk out there (what is ~ 15GB sdb for instance? is that the USB Book stick?) 

iis there any way to clean this up without doing a clean install of Ubuntu?
while that would be simplest at this point, I would have learned nothing. 
I would like to be able to understand and manage partitions and this Legacty boot thing.

how should I proceed.?

If it seems to recognize both Windows 10 and Ubuntu as installed, why can I not boot to either.?

---

### Post by yancek on 2023-04-04
In the second image of your initial post, you show the Boot Options in the BIOS.  If you select the first option beginning with WDC, it should boot windows.  That is assuming the windows boot files are still there and are not corrupted.

Since this is a Legacy install of windows, the simplest solution would be to enable Legacy Boot in the BIOS and reinstall Ubuntu to the same partition.  Make sure you do not select the USB boot from the EFI options in the BIOS but the Legacy option.

You have created an EFI partition with the Ubuntu install.  If the BIOS is set to Legacy boot, it will not boot and EFI install.

---

### Post by yancek on 2023-04-04
In the second image of your initial post, you show the Boot Options in the BIOS.  If you select the first option beginning with WDC, it should boot windows.  That is assuming the windows boot files are still there and are not corrupted.

Since this is a Legacy install of windows, the simplest solution would be to enable Legacy Boot in the BIOS and reinstall Ubuntu to the same partition.  Make sure you do not select the USB boot from the EFI options in the BIOS but the Legacy option.

You have created an EFI partition with the Ubuntu install.  If the BIOS is set to Legacy boot, it will not boot and EFI install.  If you leave Ubuntu as an EFI install, Grub will not boot the Legacy windows. 

In your initial post it showed an sda1 as an Extended partition with sda5 and sda6 as logical partitions within the Extended.  In your last post, sda1 does not show? Not sure what happened here. 

I would think the simplest solution is to reinstall Ubuntu in Legacy mode.  You should then be able to boot both Ubuntu and windows, assuming of course that the windows boot files still exist where they should be and are not corrupted.  Linux systems will not repair the windows boot files.  You need a windows recovery disk to do that.

---

### Post by pjstock on 2023-04-04
thank you all for your time.
in the end I just started from scratch and did an All-Ubuntu install and wiped out whatever was there.
I concluded that for the 1 in 1000 (10,000) times I might need Windows, I can use my dual boot laptop.

---

### Post by him610 on 2023-04-05
Re: post #4 > ...like print to an old printer that only supports Windows...
Don't know the make and model of your printer, but I have a 15 year old laser printer from Dell. Drivers for it were abandoned in Win 8. It has always worked fine using *buntu. It is still my primary goto printer using Xubuntu 24.04.2.

---

### Post by TheFu on 2023-04-05
For printers, if you decide to get a new one, pick from the list that supports "driverless printing" from the [https://openprinting.github.io/printers/](https://openprinting.github.io/printers/) list.

The same goes for scanners.  There's a "driverless scanning" standard.  Also, many scanners will scan and store their files directly onto flash storage plugged into the scanner.  No need for a computer at all.

---

