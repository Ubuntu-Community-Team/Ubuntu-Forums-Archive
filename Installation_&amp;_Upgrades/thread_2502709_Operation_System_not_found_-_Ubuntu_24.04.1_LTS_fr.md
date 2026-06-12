---
title: "Operation System not found - Ubuntu 24.04.1 LTS fresh Install on Inspiron 14R N4110"
date: 2024-11-26
forum: Installation &amp; Upgrades
---

### Post by lang22 on 2024-11-26
Hi,
    Please help.  I tried
    [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
    but that did not work.
    
    Here is the paste from boot-repair app
    [https://paste.ubuntu.com/p/j372FqcC9h/](https://paste.ubuntu.com/p/j372FqcC9h/)
    
Many thanks

**UPDATE:** A solution is to choose dual boot (Win+ Ubuntu) option during the installation.  See post#22 for more details.

---

### Post by tea for one on 2024-11-26
Line 283 - The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

You have installed in old style Legacy mode.
As your PC seems to be UEFI compatible, I would suggest that you re-install in UEFI mode.
Your disk is already GPT, which is fine (see line 291)
Fresh install indicates that there should not be any data to backup?

You may be better off with Xubuntu or Lubuntu with a 2nd Gen Intel Processor.

---

### Post by lang22 on 2024-11-26
> **tea for one said:**
> Line 283 - The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

You have installed in old style Legacy mode.
As your PC seems to be UEFI compatible, I would suggest that you re-install in UEFI mode.
Your disk is already GPT, which is fine (see line 291)
Fresh install indicates that there should not be any data to backup?

You may be better off with Xubuntu or Lubuntu with a 2nd Gen Intel Processor.

Thanks for your reply. For some reason, my 2011 laptop cannot read USB image built with Rufus' GPT partition scheme; I get "Operation System not found" error.  It only boots with MBR (Legacy?).  
To make sure it's not an Ubuntu issue, I also tried with Windows image and experienced the same problem - cannot boot with GPT image.
I did update the bios using latest version (A12) from Dell's website but that did not add anything new to the laptop's boot menu, except it changed the version number from A10 to A12.

Yes fresh install indicates no data to backup.  Since it's painfully slow to run Win10 on this laptop, I wonder if a fresh install of Ubuntu could help to speed it up.  This is not my main computer for daily use.  I only want to use it when travel. 

Thanks for the  Xubuntu and Lubuntu suggestion, I'll check out both.

---

### Post by tea for one on 2024-11-26
Your internal disk is already GPT, so I don't think it matters about the Rufus configuration.
When you boot the USB, does your PC show two options similar to attached image?

---

### Post by lang22 on 2024-11-26
> **tea for one said:**
> Your internal disk is already GPT, so I don't think it matters about the Rufus configuration.
When you boot the USB, does your PC show two options similar to attached image?

No, nothing likes your attached image.

If I remember correctly, I got something similar to this (I downloaded this image from the web.  I don't think there was an OEM Install option in my case)
[IMG]https://i.postimg.cc/kghQpXBP/try-or-install-ubuntu-1-3114992786.png[/IMG]
[IMG]https://postimg.cc/K1B3KbP0[/IMG]

---

### Post by tea for one on 2024-11-26
Ah, a little misunderstanding in play here.
Your image is the grub menu after booting the usb.

I was referring to the PC boot menu using the dedicated key (F2, F9, F10 or similar)
i.e. before booting into a live session.
This allows you choose UEFI or Legacy boot mode.
Boot in UEFI mode = Install in UEFI mode

---

### Post by lang22 on 2024-11-26
> **tea for one said:**
> Ah, a little misunderstanding in play here.
Your image is the grub menu after booting the usb.

I was referring to the PC boot menu using the dedicated key (F2, F9, F10 or similar)
i.e. before booting into a live session.
This allows you choose UEFI or Legacy boot mode.
Boot in UEFI mode = Install in UEFI mode
Sorry, my bad.  There is no such option.  Here are the images from my boot (F2) screen.  

[IMG]https://i.postimg.cc/13ndj7sW/Capture.jpg[/IMG]

[IMG]https://postimg.cc/9r6KLZDF[/IMG]

[IMG]https://postimg.cc/9r6KLZDF[/IMG]

---

### Post by oldfred on 2024-11-26
Older systems even with SSD work much better with a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

I use Kubuntu which is more of a mid-weight flavor on both newer laptop & very old laptop. 
Old laptop would not even install Ubuntu, was a bit surprised that Kubuntu installed. But it still was slow as old HDD was slow & it had little RAM.
But needed Old laptop for a trip when new laptop was in for repairs. I also had full UEFI install of Kubuntu on external SSD. Found I could add grub BIOS boot stanza on HDD to boot external SSD, bypassing UEFI, and directly booting kernel, and it worked well. Faster swap on SSD helped to make up for low RAM, but I still tried not to load too many apps at once.

---

### Post by tea for one on 2024-11-26
That's a pity, no sign of UEFI in your images.

One last double check
Can you attach your USB, power on and press F2  and see if you have more than one entry under USB or Removable Drive?

---

### Post by lang22 on 2024-11-26
I might have found something here.
My laptop has an INTEL processor but the iso image I downloaded from
[https://ubuntu.com/download/desktop#system-requirements-NobleNumbat](https://ubuntu.com/download/desktop#system-requirements-NobleNumbat)

indicated it was for an AMD cpu:
[https://ubuntu.com/download/desktop/thank-you?version=24.04.1&architecture=amd64&lts=true](https://ubuntu.com/download/desktop/thank-you?version=24.04.1&architecture=amd64&lts=true)

Could that be my problem?  If yes, where could I find an Ubuntu 24.04.1 LTS iso for Intel processor?

The lubuntu website 
[https://lubuntu.net/](https://lubuntu.net/)
has 2 downloads: one for INTEL and  the other for AMD. 

Thank you.

---

### Post by tea for one on 2024-11-26
lubuntu.net is unofficial and completely out of date - please [COLOR="#FF0000"]ignore[/COLOR] it.

This is the one you want [https://lubuntu.me/](https://lubuntu.me/)

The iso with amd in the title signifies 64-bit architecture, suitable for both Intel and AMD.
(I think AMD were the first out of the starting blocks and licensed it to Intel - something like that)

---

### Post by lang22 on 2024-11-26
> **tea for one said:**
> That's a pity, no sign of UEFI in your images.

One last double check
Can you attach your USB, power on and press F2  and see if you have more than one entry under USB or Removable Drive?
With USB attached, this is what Boot (F2) screen looks like
[IMG]https://i.postimg.cc/85Pbfwkd/Capture.jpg[/IMG]

---

### Post by tea for one on 2024-11-26
Your image in post 12 is too small to decipher.
Please use "Go Advanced" then "Attachments"

Ah, I can see it now - Still no sign of UEFI.
Perhaps, boot-repair misreported, we have no way to double check other than what you show us.

Looks like you'll have to install in Legacy mode.
If so, change your partition table to msdos before starting the installer.

---

### Post by lang22 on 2024-11-26
> **tea for one said:**
> 
....
Looks like you'll have to install in Legacy mode.
If so, change your partition table to msdos before starting the installer.

Right now  I have 3 partitions in sda:  sda1 = GRUB, sda2 = data?, sda3 = /boot
sda2 and sda3 are ext4 file system.

which partition should I change to msdos? sda3? sda2? or both?
Thank you.

---

### Post by yancek on 2024-11-26
>  which partition should I change to msdos? sda3? sda2? or both?

You don't change partitions it is the physical drive and usually this deletes the OS installed as well as all data so you need backups.  What was the reason for trying to create a separate boot partition?  You have a Legacy install on a GPT drive and you have the BIOS_boot partition (sda1) needed for the Grub core.img file (which is there) as well as Grub code in the MBR so it should boot.      Was this sysetm booting successfully for some time before you created the separate boot partition and if so, why create it?  If you had problems booting you would likely have been better of posting the problem because generally, there is no need for a separate boot partition.

You could try reinstalling the same release version of Ubuntu to sda2 and skip the /boot partition.  If you select to NOT FORMAT that partition (sda2), it should reinstall and save data but I would do backups just in case.  There might be a way to convert to GPT without data loss so maybe wait for someone to post or do an online search.

---

### Post by tea for one on 2024-11-26
> **lang22 said:**
> which partition should I change to msdos? sda3? sda2? or both?
msdos or gpt are partition tables for the whole disk.
For many years, Legacy (mbr) installations reliably used msdo partition tables, hence the reason for my suggestion.
Also, your PC has a certain vintage (2011) and may be better suited to earlier traditional formats.

---

### Post by oldfred on 2024-11-26
You may not have to change to MBR(msdos).
Only a few systems seem to complain.

I have used gpt with my 2006 BIOS only desktop since about 2010. Learned grub needed the bios_grub partition of 1 or 2MB unformatted with bios_grub if using gparted.  Or code ef02 if using gdisk.
Converted old 2006 laptop to gpt and it did not complain.

About the only place MBR still required is for BIOS installs of Windows. And Microsoft has required vendors to install Windows in UEFI boot mode with gpt partitioning since 2012.

Systems prior to 2012 usually are BIOS/MBR, but a few before then were UEFI. Windows 7 could be installed in UEFI/gpt with Secure boot off, but most installs were BIOS/MBR.

But systems that old, really do not run Ubuntu well. A lighter weight flavor works better and having an SSD makes a huge improvement.

---

### Post by jeremy31 on 2024-11-26
Some older laptops just don't know how to boot a GPT drive even with the bios_grub partition.  The old Toshiba I had didn't like GPT and the BIOS was 2013, I think but another Toshiba with a BIOS from the same year that had some UEFI support would boot the same drive without issue.  People that select to install alongside an old Windows version don't seem to have the issue, but erase disk option seems to default to a GPT partition table

---

### Post by lang22 on 2024-11-26
> **yancek said:**
> You don't change partitions it is the physical drive and usually this deletes the OS installed as well as all data so you need backups.  What was the reason for trying to create a separate boot partition?  You have a Legacy install on a GPT drive and you have the BIOS_boot partition (sda1) needed for the Grub core.img file (which is there) as well as Grub code in the MBR so it should boot.      Was this sysetm booting successfully for some time before you created the separate boot partition and if so, why create it?  If you had problems booting you would likely have been better of posting the problem because generally, there is no need for a separate boot partition.

You could try reinstalling the same release version of Ubuntu to sda2 and skip the /boot partition.  If you select to NOT FORMAT that partition (sda2), it should reinstall and save data but I would do backups just in case.  There might be a way to convert to GPT without data loss so maybe wait for someone to post or do an online search.

I was doing a fresh/clean install and therefore did not need to backup any data.  There was no issue during the installation via an USB drive.  However, after the installation, my laptop could not boot from its hard drive and displayed a "operation system not found" error.  

Before posting here, I found this guide  [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) which suggested a separate boot partition.  I tried but that did not help. The process also created information about my laptop here [https://paste.ubuntu.com/p/j372FqcC9h/](https://paste.ubuntu.com/p/j372FqcC9h/)

Whether it was 2 partitions (sda1,2) or 3 partitions (sda1,2,3), my laptop could not boot from its hard drive.
Thank you.

---

### Post by lang22 on 2024-11-26
> **oldfred said:**
> You may not have to change to MBR(msdos).
Only a few systems seem to complain.

I have used gpt with my 2006 BIOS only desktop since about 2010. Learned grub needed the bios_grub partition of 1 or 2MB unformatted with bios_grub if using gparted.  Or code ef02 if using gdisk.
Converted old 2006 laptop to gpt and it did not complain.

About the only place MBR still required is for BIOS installs of Windows. And Microsoft has required vendors to install Windows in UEFI boot mode with gpt partitioning since 2012.

Systems prior to 2012 usually are BIOS/MBR, but a few before then were UEFI. Windows 7 could be installed in UEFI/gpt with Secure boot off, but most installs were BIOS/MBR.

But systems that old, really do not run Ubuntu well. A lighter weight flavor works better and having an SSD makes a huge improvement.

It seems that my laptop cannot recognize GPT format USB.  It only works when I select MBR Partition scheme.  I also cannot find any UEFI/GPT settings in my boot (F2) screen.
I'll try lubuntu to see if it solves my boot problem.  Thank you for your suggestion.

---

### Post by yancek on 2024-11-27
From your boot repair shown in the link in post 19, lines 237 - 241 show you have a BIOS_boot partition with the core.img file needed for a Legacy install on a gpt drive.
 Line 272 shows the Ubuntu system partition on sda2 and clearly shows a gpt drive on line 291.  Line 283 indicates the system  firmware seems EFI-compatible but if you can not find any reference to EFI in your BIOS then I expect you will need to do a Legacy install of Ubuntu or another OS.

>  The boot files of [sda2 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. 

Having the boot partition at the end of the drive as quoted above from boot repair may be the problem.  Might be easier just to reinstall.

---

### Post by lang22 on 2024-11-27
> **jeremy31 said:**
>  ...People that select to install alongside an old Windows version don't seem to have the issue...

Above statement IS the solution to my problem!  Thank you Jeremy for pointing this out.

Instead of installing just Ubuntu (single boot?), which seems to cause the "Operation System not found" error, a dual boot (Win10 + Ubuntu) installation allows my laptop to automatically boot into Ubuntu without any issue.  I can also access the GRUB menu by holding down the SHIFT key during the boot process.  

I generated another boot info summary for the **dual boot** installation here: [https://paste.ubuntu.com/p/prtrygpYpQ/](https://paste.ubuntu.com/p/prtrygpYpQ/)

It is not obvious to me why boot-repair could not fix the **Ubuntu-only boot** problem: [https://paste.ubuntu.com/p/j372FqcC9h/](https://paste.ubuntu.com/p/j372FqcC9h/)

Thank you all especially @**tea for one **for your time and patient with my questions.

---

