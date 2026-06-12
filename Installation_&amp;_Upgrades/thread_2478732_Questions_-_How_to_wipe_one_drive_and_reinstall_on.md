---
title: "Questions - How to wipe one drive and reinstall on a dual-boot system???"
date: 2022-09-04
forum: Installation &amp; Upgrades
---

### Post by drumone on 2022-09-04
I have a dual-boot system that I built from scratch in mid-December 2021.  I use Ubuntu as my main system one one SSD and Windows 11 on a second SSD. I only use Windows for a few specialty programs that I can't get for Linux based systems. Not surprisingly, I am having major issues with Windows not allowing access to my software, combined with overheating issues. I think the software and overheating are directly linked, even though I don't know how. This leads to my questions.

1. How do I identify which drive is which (Linux vs. Windows)? 
2. From the Linux side of the machine, how do I completely wipe the hard drive with Windows on it?
3. How do I re-install Windows without losing the Linux GRUB menu/boot?

I've run dual-boot systems for about the last 15 years. However, I've always loaded Windows first and then Ubuntu, never the other way around. I'm comfortably using the Terminal, provided that I have exact lines of code to run from someone else. Please feel free to provide links to other posts, if this has been discussed elsewhere, as I wasn't able to find them. Thank you!!!

---

### Post by tea for one on 2022-09-04
Assuming that both systems are installed in UEFI mode?
Are the disks identical i.e. size/manufacturer etc?
Make sure that you have backups before proceeding?
> **Neil_Harbel said:**
> How do I identify which drive is which (Linux vs. Windows)? 
Open a terminal and run ```
sudo parted -l
``` Look for ntfs partitions and/or Microsoft reserved etc.
If you are in doubt, post the terminal output in code tags.
> **Neil_Harbel said:**
> From the Linux side of the machine, how do I completely wipe the hard drive with Windows on it?
I don't think that you need to use the Ubuntu disk.
Backup your Windows data.
Isolate, de-activate or remove the Ubuntu disk.
Install Windows and restore data.
> **Neil_Harbel said:**
> How do I re-install Windows without losing the Linux GRUB menu/boot?
After you have installed Windows and checked that it is all OK, activate/attach your Ubuntu disk.
Boot into Ubuntu via UEFI one-time boot menu, open a terminal and run
```
sudo update-grub
```

Alternatively, boot either OS from UEFI boot menu.

---

### Post by yancek on 2022-09-04
In addition to using parted -l to list drives and partitions suggested above, you can use fdisk -l as well as lsblk to get this information.  With an SSD you should see something like the below info for each drive.  The first drive should show as the first entry below, the second drive as the second entry.  The various partitions will also be listed as will the filesystem type.

>  nvme0n1
nvme0n2

As explained in the post above, since both systems are UEFI (see lines 13-17 in boot repair output) you can boot either drive from the BIOS firmware.  I agree with the suggestions above to accomplish your goal.

---

### Post by oldfred on 2022-09-04
Note that both systems may be booting from one ESP - efi system partition if UEFI.
Ubuntu's Ubiquity installer only installs grub's boot files into first drives ESP. First drive is defined by UEFI/BIOS, so may not be drive you are installing into. Windows may do the same.

If UEFI system, best to install all systems in UEFI boot mode. How you boot install media UEFI or BIOS from UEFI/BIOS one time boot key, is then how it installs. Windows requires gpt partitioned drives for UEFI boot. Ubuntu should but does not.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) &

---

### Post by tea for one on 2022-09-04
> **oldfred said:**
> Note that both systems may be booting from one ESP - efi system partition if UEFI
Ah, yes - excellent observation. 
I should have mentioned that it is ideal to have an OS on separate drives, each with an ESP.
If one ESP controls two or more drives/operating systems, there is a loss of flexibility if the drive containing the single ESP develops a hardware fault.

I think that the OP should provide the partition details before proceeding.

---

### Post by drumone on 2022-09-04
Forgive my lack of knowledge, but much of what you described is foreign to me. Thanks oldfred for the links with explanations! If I'm remembering correctly, I used the following link to help me install Ubuntu on one of my hard drives. [https://www.linuxjournal.com/content/installing-ubuntu-two-hard-drives](https://www.linuxjournal.com/content/installing-ubuntu-two-hard-drives)  I feel confident that everything is UEFI (see my system specs below) and it shows that I have GPT partitions. In the UEFI I can set either hard drive to boot first, but I have the Ubuntu drive selected to be first. 

Due to the issues I'm having with Windows, I want to completely erase the hard drive and re-install it using my original OEM DVD. Can I erase the drive using the Ubuntu Disks utility? If so, how? Now that I know which drive is which, I feel like I should be okay with the re-installation of Windows. I just need to know how to completely wipe that drive and start over. I feel it's a necessity for me to start with a clean drive.

[LEFT] SPECS:[/LEFT] [LEFT] 
 [/LEFT] [LEFT] Asus ROG Crosshair VIII Dark Hero AMD X570 ATX motherboard[/LEFT] [LEFT] AMD Ryzen 9 5950x processor[/LEFT] [LEFT] Fractal Lumen S24 CPU liquid cooler[/LEFT] [LEFT] Asus Dual-RX6600 GPU[/LEFT] [LEFT] G.Skil RipJaws V 64GB RAM[/LEFT] [LEFT] Samsung 980 Pro SSD &#8211; 1TB NVMe &#8211; 2 (Ubuntu OS on one, Windows OS on the other)[/LEFT] [LEFT] Corsair RM850x power supply[/LEFT] [LEFT] Fractal Define R5 ATX Midtower case[/LEFT] [LEFT] Fractal Dynamic X2 GP-14 140mm case fans &#8211; 2 in the front,1 in the rear
[/LEFT]

---

### Post by oldfred on 2022-09-04
If Ubuntu drive is first, Windows will probably install its boot files into that drive.
With old BIOS installs, Windows would just overwrite whatever was at the start of the drive with its own boot partition. 
Not sure what it does with UEFI.

I would suggest to see if you can disable or turn off the Ubuntu NVMe drive in UEFI drive settings. Most UEFI have a setting to enable/disable a drive. Then you do not have to open case & remove the NVMe drive.

Just be sure to have good backups. Then if something goes awry, it is easy to reinstall & restore.

---

