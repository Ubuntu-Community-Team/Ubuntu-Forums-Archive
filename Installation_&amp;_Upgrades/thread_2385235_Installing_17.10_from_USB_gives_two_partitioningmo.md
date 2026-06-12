---
title: "Installing 17.10 from USB gives two partitioning/mounting failures"
date: 2018-02-18
forum: Installation &amp; Upgrades
---

### Post by licebit on 2018-02-18
[FONT=verdana]I am attempting to install Kubuntu 17.10 from USB onto my laptop. At the moment, my laptop does not have any working operating systems to boot into.[/FONT]
[FONT=verdana]
When I boot from my USB drive and begin the GUI install steps, I am asked which drive I want to use. I have a 1TB HDD and a 256GB SSD. The SSD had Windows 10 on it which I at some point in the past seem to have erased and also Ubuntu GNOME which does not seem to be working.[/FONT]
[FONT=verdana]
In any case, I have tried selecting each one on separate occasions and choosing to use the entire drive to install Kubuntu, but each time it will fail with two consecutive error codes:[/FONT]

[LIST=1]
[*]"the attempt to mount a file system with type vfat failed"
[*]ubi-partman failed with exit code 141
[/LIST]
[FONT=verdana]
I have had trouble in the past few days installing Manjaro (even using Architect) and KDE Neon, but since Kubuntu actually boots into the USB I am hoping it will work.[/FONT]

---

### Post by ubfan1 on 2018-02-18
Are you trying to install in UEFI mode?  Did you try to partition the target disk before the actual install, putting an EFI partition on it, (since that's a FAT, and perhaps the installer does not create one)? The basic whole disk install should create EFI, root, and swap partitions.  On such big disks, maybe a 50G root, and the rest a data partition for your files, or make a second root for testing upgrades, etc. 1T is an awful lot of room for a root.  Did you hashcheck the downloaded ISOs, and run a media check after creating the install media?

---

### Post by oldfred on 2018-02-18
Which drive is sda?
Are both drives gpt partitioned?

Post this:
sudo parted -l

Ubuntu's grub only wants to install the UEFI boot loader into the drive seen as sda. So if UEFI install on sdb, you still need an ESP - efi system partition (FAT32 with boot flag) on sda.

If BIOS install, and installing to sdb, you need to use something else install option and install grub boot loader to MBR of sdb. The boot loader drive selection in UEFI mode can be made, but with Ubuntu does not seem to work.

---

### Post by licebit on 2018-02-18
I'm not very Linux- or terminal-literate, so I'm sorry I don't know how to answer all of your questions. 

I believe I am trying to install in UEFI mode, but I wouldn't know how to install in a non-UEFI mode. One thing that I have been suggested to do is format both drives, but I'm not certain how to access a command line that will allow me to run those commands without an operating system on my laptop. The 256GB SSD appears to be sda and the 1TB drive is sdb. Using the installation GUI, I can choose "Guided" installation or "Manual" when selecting how to partition. The Guided installation wants to select sdb and cut it into two partitions.

It may be good to know that I did have Ubuntu GNOME 17.10 as well as Windows 10 installed and working on this laptop before things went awry.

---

### Post by oldfred on 2018-02-18
If you can boot live installer, go to terminal and copy &  paste command from above.

Newer UEFI systems offer to boot installer in two modes, one usually is UEFI:flash and the other just flash ( which is BIOS), where flash is the name or label on the flash drive.

If you want to attempt to repair installed systems, run this from live installer.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by licebit on 2018-02-18
I can boot the installer and it gives me the choice to install or "try" Kubuntu. Trying Kubuntu causes a freeze about 5 seconds of loading after clicking it. I don't know how to access command line from the installer other than getting to a live desktop.

---

### Post by oldfred on 2018-02-18
What brand/model system?
What video card/chip?

---

### Post by licebit on 2018-02-18
Ah yes, I forgot to mention that I had driver issues with installing Ubuntu GNOME, but they were fixed after I disabled Secure Boot and installed the proprietary drivers.

My laptop is an ASUS Vivobook Pro Model M580VD. It has an Nvidia GTX 1050 and i7-6700.

---

### Post by licebit on 2018-02-18
I have booted it into a live iso of GParted. Can I follow all of the advice given to me using GParted? Each drive has a 512MB EFI (?) partition which is FAT32 format, while the rest of each drive was ext4. How should I proceed?

A picture of sudo parted -l is attached.

[ATTACH=CONFIG]278580[/ATTACH]

---

### Post by Dennis N on 2018-02-18
Your display in post #9 shows partition #2 on the two disks is fat32, not ext4. You should format those ext4 for Linux.

---

### Post by licebit on 2018-02-18
It was ext4, but I reformatted it using GParted. Actually, by following the instructions listed by oldfred I now have a working Kubuntu system. Thank you!

To recap, I made sure there was a partition with "boot" flag and formatted the rest of sda to fat32. Once this was done, Kubuntu installed in a breeze.

---

