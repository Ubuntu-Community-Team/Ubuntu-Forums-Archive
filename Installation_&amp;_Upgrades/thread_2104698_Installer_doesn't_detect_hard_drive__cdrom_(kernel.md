---
title: "Installer doesn't detect hard drive / cdrom (kernel support missing?)"
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by Flandry on 2013-01-14
Good evening.  I think i know what's wrong but am not sure how to go about fixing it. Here's the deal:

I have a GA-A75N-USB3 motherboard (AMD A75 chipset) w/ llano APU. I am using a hard drive i used in a previous box, and it was dual-boot winxp and kubuntu. I have been using windows reinstalled on the win partition since i got the new box and am now trying to install linux. All the hardware works fine in windows.

The problem:
Not one distro installer that i have tried detects the hdd or cdrom! I can boot the install CD (or a USB key with the install on it) but then it fails to find any media but the USB key. There are no other sd devices or any other devices that could be a hdd or cdrom.

I have tried the latest kubuntu, mint, debian stable and mepis installers, and they all hit the same problem.

So, kernel doesn't support my mobo's storage controller chip? Besides "wtf?!" (mobo is about a year old at this point, and not exactly from a no-name OEM), what's to be said about this?

A look at the mobo spec page
[http://www.gigabyte.com/products/product-page.aspx?pid=4030#sp](http://www.gigabyte.com/products/product-page.aspx?pid=4030#sp)
says the I/O Controller	is iTE IT8720 chip and I don't see any other specific third-party chip info that seems relevant. The hits i found for IT8720 all seem to be about HW monitoring rather than SATA so that's not it.

I went back to a review i read before buying the board and it says there are no additional ATA controller chips:
[http://www.xbitlabs.com/articles/mainboards/display/mini-itx-socket-fm1.html#sect0](http://www.xbitlabs.com/articles/mainboards/display/mini-itx-socket-fm1.html#sect0)

Very confusing.

Please help me figure out how to get linux on this box. Thanks.

---

### Post by Flandry on 2013-01-15
Anybody have a suggestion what to try or even why the standard SATA controller wouldn't be supported?

---

### Post by Sylos on 2013-01-15
I cant offer any in depth help but have you tried switching BIOS settings between IDE and AHCI?

Good luck.

---

### Post by ronparent on 2013-01-15
I have the same board on one of my machines without problems installing thru Ubuntu 12.10 and Mint 14. I believe my bios is set pretty much at the default settings. And I have have not had problems with either SATA HD or CD/DVD burner. So we may have to dig a little deeper.

Can you run a live CD session? If so, what does gparted show?

---

### Post by Flandry on 2013-01-15
> **Sylos said:**
> I cant offer any in depth help but have you tried switching BIOS settings between IDE and AHCI?

Good luck.

Good suggestion. Yes, i have tried that and there was no difference.

---

### Post by Flandry on 2013-01-15
> **ronparent said:**
> I have the same board on one of my machines without problems installing thru Ubuntu 12.10 and Mint 14. I believe my bios is set pretty much at the default settings. And I have have not had problems with either SATA HD or CD/DVD burner. So we may have to dig a little deeper.

Can you run a live CD session? If so, what does gparted show?

Yes i booted into live CD sessions for mint and one other distro (can't recall which now). I did again just now with mint, but unsurprisingly, since there are not even sd* entries in /dev for anything but the USB key, gparted only shows the partition information for that.

Strange that the same mobo works fine for you. Wish i could figure out what's different here.

---

### Post by ronparent on 2013-01-16
I doubt there is any problem with the MB. What does the HD partitioning look like in Windows?

Edit: I just thought of something. Your MB is an UEFI ready board. Are you trying to install 32bit or 64bit Linux distros. You may need the 64bit version to properly see your HD. It would be a better fit for your 64 bit MB in any case.

---

### Post by Flandry on 2013-01-16
> **ronparent said:**
> I doubt there is any problem with the MB. What does the HD partitioning look like in Windows?

Edit: I just thought of something. Your MB is an UEFI ready board. Are you trying to install 32bit or 64bit Linux distros. You may need the 64bit version to properly see your HD. It would be a better fit for your 64 bit MB in any case.

I always use the AMD64 version.

HD partition looks like this from windows:
Disk 0
931.51 GB

Win8 (C:) 50 GB NTFS Healthy(System, Boot, Primary Partition)
Data (E:) 100 GB NTFS Healthy (Primary Partition)
13.97 GB Healthy (Primary Partition)
5.58 GB Healthy (Primary Partition)
182.26 GB Healthy (Primary Partition)
575.69 GB Healthy (Primary Partition)

CD-ROM 0
...

---

### Post by ronparent on 2013-01-16
I admit I am totally puzzled. Even in cases where residual fakeRAID metadata blocks identification of the partition table, the underlying device (ie sda, etc) shows up as a blank unallocated drive. In your case the device doesn't show at all??? Yet the Windows is bootable (correct me if I don't have the basic facts straight). 

Even in the unlikely case for you that Windows weren't booting on the MBR but on an efi partition Ubuntu 12.10 or Mint 13 or 14 would pick this up.

From my own experience with the exact same MB I doubt that the MB or the disk drive are at fault - unless doubtfully, perhaps yours was a hybrid drive (ssd and spinning HD combined). We need help! Try bumping again.

Note: As I recall the default BIOS setups for that MB should allow recognition of either legacy or efi boot setups.

---

### Post by Bashing-om on 2013-01-16
just a thought, buss speed ? Can you change the ports on the buss that the hard drive connects ?
[INDENT][INDENT]a shot in the dark. 
[/INDENT][/INDENT]

---

### Post by Flandry on 2013-01-21
> **Bashing-om said:**
> just a thought, buss speed ? Can you change the ports on the buss that the hard drive connects ?
[INDENT][INDENT]a shot in the dark. 
[/INDENT][/INDENT]

Unbelievable. I feel a bit silly. At bus speed > 105 Mhz (i had it at 109), linux doesn't detect the SATA bus. Below that, it works fine. 

Problem solved, but it amazes me that linux is so sensitive to bus speed on this machine.

Thanks. :)

---

