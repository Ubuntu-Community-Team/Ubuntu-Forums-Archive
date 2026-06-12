---
title: "Should I enable mounting of HDD automatically in a computer with SSD and HDD?"
date: 2021-01-13
forum: Installation &amp; Upgrades
---

### Post by EngineerStrange on 2021-01-13
My computer has both SSD and HDD so I am installing root as well as home in SSD. Now for storing media and other large files I will be using HDD. Should I enable automatically mounting of HDD?
Also do I have to create swap area in whichever partition/partitions I will be installing Ubuntu?

---

### Post by Impavidus on 2021-01-13
Automatically mounting your hard drive will be the easy solution. Create an empty directory to use as a mountpoint in whatever location you consider convenient (there are some directories to avoid) and setup /etc/fstab to mount it automatically at boot. You can do that after installation.

There's no need to create a swap area. If you don't, the installer will automatically create a swap file in the root partition. But you can create a swap partition yourself, if you prefer.

---

### Post by ActionParsnip on 2021-01-13
If you need frequent access to the data then yes. Otherwise you keep it unmounted (like for backup) so that the storage is offline and cannot be touched. As stated above its a case of making an empty folder then adding a line in /etc/fstab
If it's a permanent drive in the system then I recommend using Ext4 or some other Linux file system and not FAT32 or NTFS

---

### Post by EngineerStrange on 2021-01-16
Do I need to create the empty directory during installation or after installation?

---

### Post by CelticWarrior on 2021-01-16
Why do you think you need an "empty directory"?

The only situation in which a very small (1-2MB) *unformatted* **partition**, not directory, is a requirement is when installing Ubuntu or other Linux distro in BIOS/Legacy mode in a GPT drive and said partition is used in lieu of the MBR to store the bootloader.

This very specific scenario is very likely NOT applicable to yours. If the goal is dual-booting with a preinstalled Windows in any modern computer (as in from at least 2012 or newer) then Windows is already installed in UEFI mode, as it should be, therefore Ubuntu should also be installed in UEFI mode, also as it should be, in ANY UEFI enabled hardware (again, anything from the last decade).

---

### Post by oldfred on 2021-01-16
Your HDD does need to be partitioned with gpt and you have to have to create partition(s) to mount them.

If  a new user often easier to have separate /home on HDD and / (root) on SSD.
But I prefer to have /home inside / on SSD as it also has your hidden user configuration files that are regularly loaded. Data is not regularly loaded, so being on slower HDD is not normally an issue. Some dual booting like both a shared NTFS data partition for any data they want to share and ext4 data partition(s). 

Both one very large partition can create issues for backup or recovery when large, but too many small partitions can create issues where you have a lot of unused space in one partition and no space in another. Until you have used system for a while you may not know.

I still have some allocated space on both SSD & HDD for future use. But I have good idea of current sizes of my systems & data and allowed for what I expected as normal growth (primary pictures of grandkids & hopefully vacations again).

When you create /home on HDD, it automatically creates a fstab entry to mount it, gives it a mount point ( /home) and gives you ownership & permissions to use it. 
If you create a data partition you have to create your own mount point or label, add an entry to use that mount in fstab and set ownership & permissions so you can use it. Many threads with details & most is copy & paste, with minor adjustments for your specific settings.

---

### Post by Hagar Delest on 2021-01-16
> **CelticWarrior said:**
> Why do you think you need an "empty directory"?
Just to clarify: the "empty directory" is referring to ActionParsnip's advice. Indeed, the mounting point of the partition has to be an empty folder.

---

### Post by EngineerStrange on 2021-01-16
Can you explain step-by-step how to create a data partition where I can read as well as write? I have little knowledge on these things so I am unable to understand what to do in order to make a data partition.

---

### Post by Impavidus on 2021-01-16
> **EngineerStrange said:**
> Do I need to create the empty directory during installation or after installation?

> **Impavidus said:**
> Create an empty directory to use as a mountpoint in  whatever location you consider convenient (there are some directories to  avoid) and setup /etc/fstab to mount it automatically at boot. You can  do **that** after installation.
The bold word "that" refers to the entire preceding sentence.

Instructions:
1: Make a plan. What partitions do you need, on which drive do you want them, where do you mount them.
2: Use the partitioning tool on the live disk to create those partitions. Every live disk of every Ubuntu flavour (and most other Linux distros) has a partitioning tool (usually gparted) built in.
3: During installation, tell the installer which partition to use at which mountpoint. If the mountpoint you want is not listed, skip that partition.
4: After installation, add the partitions you skipped in step 3 to your /etc/fstab and create their mountpoints as empty directories.

More about fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Some knowledge about file permissions may come in handy: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

On a Linux-only computer, only use native Linux partitions. Stick to ext4 partitions, unless you really know what you're doing.

---

### Post by Hagar Delest on 2021-01-16
At least with ubiquity, when I install Xubuntu, the mounting points do not yet exist but are created during installation according to the path provided. So just the path during the partitioning and it will be fine.
Note that you can run gparted from the live usb without installing the whole system. Just launch the live usb as you were merely testing it, then launch gparted from the menu.
Then either update your fstab or use the "disk" utility for that.

---

### Post by yancek on 2021-01-16
If you are going to be using it regularly and keeping it attached, then permanently mount it.  You can do all of this during the install.

---

### Post by bcschmerker on 2021-01-19
**FWIW, I'd installed multiple hard drives on my currently-unable-to-boot Hot Rod gPC (see "[Hot Rod gPC down, need motherboard](https://ubuntuforums.org/showthread.php?t=2456551)"), and HDD boot sequence is an option in most BIOS setup utilities.**  The GIGABYTE® GA-MA78GM-S2HP v2.0 has always been finicky about i8042 keyboards, and I'd rather land something less finicky prior to ordering a 3270/5250 Emulator (i8042 interface) from Unicomp®; the GIGABYTE® GA-MA78GM-US2H (any hardware Version) and ASUS® M3A78-EM (any hardware Version) should be able to take the AMD® Athlon 64® 3500+ CPU (I've already shortlisted the Athlon II® x2 220 for MPU upgrade, as it matches the performance of the original, since kaputt, 95*max* W Athlon64® X2 5600+ on 65*max* W), 1 GiB x 4 DDR2-800 unbuffered non-ECC main memory, and one Western Digital and three Toshiba SATA HDDs from the down GA-MA78GM-S2HP v2.0;  I'd listed the WD on SATA 0 as the first when the gPC was last up.

A CPU/chipset upgrade will force reinstall of 20.04.1-LTS Focal but might give opportunity to retrofit a "smallest-available" SSD for /boot.

---

