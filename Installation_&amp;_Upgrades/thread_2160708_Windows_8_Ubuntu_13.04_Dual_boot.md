---
title: "Windows 8 Ubuntu 13.04 Dual boot"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by virgiliox on 2013-07-07
Hi, I'm aware that this has been asked several times but I can't seem to find an answer that pertains to my case. I've been trying to install Ubuntu on a separate hard drive to dual boot with Windows 8. Every time I try to install it, the installer doesn't detect my Windows 8 installation. If I go on and install Ubuntu in the separate hard drive, when it reboots, it goes straight to the windows 8 logo, which then proceeds to go on a boot loop and won't boot into windows unless I turn off my PC and disconnect the HDD that has Ubuntu on it. I tried checking to see if I had secure boot on but my motherboard does not have it in the bios. I also disbaled the fast startup from the Windows 8 settings. I really don't want to give up on installing Ubuntu since I've used it in the past and I want to use it with this  new hardware that I have. I would install it by itself but unfortunately I need Windows for college purposes. Here's my current setup:



[LIST]
[*]Motherboard: Gigabyte Z77X-UD3H 
[*]32 GB RAM 
[*]Intel i5 3570k 
[*]128GB SSD (windows 8 disk) 
[*]2 TB HDD (for data and personal files) 
[*]500 GB HDD (Intended for Ubuntu installation) 
[/LIST]

Thank you in advance for your help. If you need any more information just let me know and I'll post it.

---

### Post by Penguenci on 2013-07-07
> **virgiliox said:**
> Every time I try to install it, the installer doesn't detect my Windows 8 installation.

What do you mean the installer doesn't detect your Windows installation? I take it you mean you don't get a GRUB menu with dual boot showing Windows as an option. If so, open your terminal and type ```
sudo update-grub
```

Given that your Windows loader is intact, this should solve the problem. You may need to play with the drive mapping later on if you have multiple drives though. But let's deal with that if need be.

> **virgiliox said:**
> If I go on and install Ubuntu in the separate hard drive, when it reboots, it goes straight to the windows 8 logo, which then proceeds to go on a boot loop and won't boot into windows unless I turn off my PC and disconnect the HDD that has Ubuntu on it.

This simply means you're booting from the drive which has the Windows 8 MBR installed on it. Go to your BIOS and set it to boot from the drive with the Linux GRUB MBR, and you're all set.

---

### Post by virgiliox on 2013-07-07
What I meant is that after the Ubuntu installation, after the reboot, not even Windows 8 loads. it just shows the logo for like 1 second and then the computer automatically reboots. And that keeps happening unless I disconnect the drive with Ubuntu. does this have anything to do with where the boot loader is installed during the Ubuntu installation?

---

### Post by virgiliox on 2013-07-07
Sorry, I meant to say my Windows 8. It says that there were no other operating systems found.

---

### Post by virgiliox on 2013-07-07
[https://www.dropbox.com/s/9h4dw6a5ngfp6rs/Partitions.JPG](https://www.dropbox.com/s/9h4dw6a5ngfp6rs/Partitions.JPG)


That's my current partition layout. Disk 1 is where my personal files are. Disk 2 is the SSD with Windows 8 Installed and Disk 3 is where I intend to install Ubuntu.

---

### Post by Penguenci on 2013-07-08
You might want to try Ubuntu with a primary partition instead, and what I said about installing the bootloader on the disk instead of the Ubuntu partition still goes. Also make sure to set the Ubuntu disk for boot. Then you'll have GRUB instead of the Windows bootloader, and it'll likely detect Windows 8. You can always run the aforementioned command on the Terminal if it doesn't. 

If the problem still persists after all that, I'm afraid it's a GPT-specific issue and since I'm not familiar with that I won't be able to help you much.

---

### Post by fantab on 2013-07-08
> **virgiliox said:**
> [https://www.dropbox.com/s/9h4dw6a5ngfp6rs/Partitions.JPG](https://www.dropbox.com/s/9h4dw6a5ngfp6rs/Partitions.JPG)


That's my current partition layout. Disk 1 is where my personal files are. Disk 2 is the SSD with Windows 8 Installed and Disk 3 is where I intend to install Ubuntu.

You have change the Partition Table on the disk you want to install Ubuntu to. Have you changed it to GUID Partition Table [GPT]?
GPT because your Windows 8 is probably booting in UEFI mode. And Ubuntu too needs to be installed in UEFI. Only GPT can let Ubuntu dual boot with Windows in UEFI mode. 

When you are done. Create First Partition on that disk as 300MB partition formated with FAT32. (This is not a Must but it is recommended).

To install Ubuntu in UEFI you need to boot it in UEFI mode. If you boot in UEFI mode then you will see a Black Screen with options, if not its regular purplish Ubuntu screen.

---

### Post by virgiliox on 2013-07-08
thanks for the advice. I do know how to boot it in UEFI mode, however, I do not know how to partition the drive with a GPT. Can you please advise me on how to achieve this. thank you.

---

### Post by virgiliox on 2013-07-08
Also, how should I proceed if the Ubuntu installer does not detect Windows 8?

---

### Post by Cihy on 2013-07-08
I deleted all partitions using linux installation usb without Win partition ofcourse. Ive been using partition guide while installing or help or whatever it calls giving linux rest of the system. Install grub as one of installation steps. I was choosing ex4 with libraries for linux and it works.

---

### Post by virgiliox on 2013-07-08
I just changed the partition table of the HDD to GPT. I'll try to install it now and I'll post the results briefly.

---

### Post by virgiliox on 2013-07-08
I was able to successfully install Ubuntu on the separate HDD. I don't get Windows 8 in the GRUB menu but I can still boot into it by pressing F12 on startup through the BIOS. this doesn't bother me. However, is there a way to add Windows 8 to the GRUB menu. that would make it easier. Once again, thank you all for your help and advice.

---

### Post by oldfred on 2013-07-08
I only have BIOS but use gpt partitioning.
        I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

If you want command line install and use gdisk which is the gpt equivalent to fdisk. It is in the repository so easy to install from Software Center, synaptic or command line:
sudo apt-get install gdisk
      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

Since Windows is UEFI you must have Ubuntu in UEFI if you want to easily dual boot. You will have to use Boot-Repair to correct the chain load entries as it has a bug and only creates BIOS type entries that do not work with UEFI.

More info in link in my signature on two drive installs.

---

### Post by virgiliox on 2013-07-08
Thanks for the advice. I was able to make the GPT partition with Partition Wizard in Windows.

---

