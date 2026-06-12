---
title: "Is there an easy fix or do I have to start all over."
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-03-07
Hello everyone,  

A brief history. 
- Fast gaming computer died. 
- Purchased a cheap computer with ecs PT800CE-A(V1.0) mobo just to get up and running. 
CPU   &nbsp;&nbsp;&nbsp;&nbsp;   
Socket 478   
FSB 800/ 533/ 400MHz CHIPSET &nbsp;&nbsp;&nbsp;&nbsp;   
VIA® PT800CE &amp; VT8237     
North Bridge: VIA® PT800 verCE     
South Bridge: VIA® VT8237 
- Cheap machine had problems from the get-go (ATI video card) 
- Used Dell 280gx w/ATI graphics as a loaner while it was being fixed. 
- Installed Ubuntu on my 250GB HD that I put into the Dell. Spent lots of time downloading applications and customizations. 
- Got the cheap machine back; now has NVIDIA graphics.  
- Put HD with Ubuntu back into cheap computer.  

Ubuntu booted from HD; had these problems: 
a) Video was slow/generic because the drivers for the NVIDIA are not installed 
b.1) Ubuntu DID NOT recognize the SATA drive on the cheap machine (Not available in Places).  
b.2) Ubuntu DID recognize the SATA drive on the Dell loaner with no extra intervention. 
c) Tried booting up with the Installation CD; it did not recognize the SATA drive either. 
d) Sound did not work.  

The forums suggest that the VIA VT8237 Chipset can cause problems if you don't have the command 
pci=nomsi in /boot/grub/menu.lst  

However, from what I read, Ubuntu now uses Grub2 now. 

I have not seen any clear way that explains what to do in the forums or Grub2 documentation.  

-- Recent Edit: The Palimpsest Disk Utility does see the 500GB SATA drive. It defines it as /dev/sdb; type is FAT and states that it is Unallocated Space; No option to mount. 

1) How do I get the SATA to be recognized?  Video: In XP to fix the video I would uninstall the ATI drivers; reboot; install Nvidia; reboot  
2.a) When Ubuntu is installed is it intertwined like a BORG Assimilation?   
2.b) Is it modularized in a way that can be changed easily?  
3) Do I need to reinstall everything?  
4) If it is necessary to install is there any way to check to see if the SATA is being recognized during the install?  
5) When I log in i type my password and Ubuntu starts. When I make a system change that is initiated by a menu option my password works. When i am using the terminal and issue an su command or sudo root my password does not work. I can't remember the system asking for a special root password during the install.


I'm hoping that I won't have to reinstall everything.  

thanks very much for your time and help,  

WD

---

### Post by sgosnell on 2010-03-07
Sorry, I know nothing about any of that equipment.  And I still have no real idea of what all you did.  But in general, just swapping the HDD to entirely different hardware is not a good idea, because the required drivers may be entirely different.  It's not that difficult to just wipe it and reinstall everything.  If you set up /home in a separate partition, you can reinstall the OS without losing your data and settings.

---

### Post by oldos2er on 2010-03-07
What file system is on the 500GB disk?

---

### Post by wizarddrummer on 2010-03-08
> **oldos2er said:**
> What file system is on the 500GB disk?

An XP system.

---

### Post by sgosnell on 2010-03-08
That doesn't answer the question.  XP can be installed on several filesystem types.  Is it NTFS, FAT32, or something different?  I would assume NTFS, since that's the way newer large drives come, but assumptions can bite you in the nether regions.  If you need the data on the drive, and want to keep the Windows installation, you probably need to defrag it with Windows, and consolidate it so that it's all as close to the front, and as contiguous, as possible.  Windows defraggers won't do a really good job of this, but just get it as good as you can.  Then boot from another drive, and use gparted to partition it, keeping the Windows partition, and put the unallocated space into whatever format you want.  The Ubuntu installer will format it to whatever you need, and can also make additional partitions if you want.  Gparted is very, very good.

---

### Post by oldos2er on 2010-03-08
> **wizarddrummer said:**
> An XP system.

That doesn't tell us which file system it uses. Assuming it's NTFS, and that it was corrupted or not shut down cleanly, Ubuntu will refuse to mount it in an attempt to preserve its data. Gparted should still see the partition though (assuming the drive is formatted as one large partition).

I don't know enough about palimpsest to know if what it's telling you is correct, that the space is unallocated. If it was truly unallocated, it wouldn't be showing it as FAT.

---

### Post by wizarddrummer on 2010-03-08
> **oldos2er said:**
> That doesn't tell us which file system it uses. Assuming it's NTFS, and that it was corrupted or not shut down cleanly, Ubuntu will refuse to mount it in an attempt to preserve its data. Gparted should still see the partition though (assuming the drive is formatted as one large partition).

I don't know enough about palimpsest to know if what it's telling you is correct, that the space is unallocated. If it was truly unallocated, it wouldn't be showing it as FAT.

For all intents and purposes this thread is solved.

I apologize, I suffer from a case of Old-timers disease.

I meant NTFS when I wrote XP.

I have probably lost all my data.

This is a new computer and I had not poked into the BIOS. There was a setting I missed to choose between RAID and IDE when the SATA was enabled.

When I was falsely thinking I had to create an array in order for XP and Ubuntu to work, the NTFS system got clobbered.

Both Unbutu and XP see the physical drive as Unallocated and FAT when it should be an intact NTFS file system, means that more than likely when I was fussing around with the VIA RAID Utility during the POST, I must have seriously screwed up. I never continued with the create process, but I did suffer a power failure during one of the sessions where I was trying to see what options were available.

It could have happened then.

Thanks all.

---

