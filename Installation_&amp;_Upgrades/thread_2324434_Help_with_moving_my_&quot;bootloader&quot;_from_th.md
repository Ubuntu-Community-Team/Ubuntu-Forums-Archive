---
title: "Help with moving my &quot;bootloader&quot; from the first disk to the second one."
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by kwanbis on 2016-05-13
Hello guys. I decided to once again try to move to Linux, and so I have decided to settle for the time being in Ubuntu MATE. Don't worry, this issue appears to occur on all versions of Ubuntu 16.04, and I have seen references in the past. Let me explain.

I have a HDD and an SsD drive on my ThinkPad. The HDD is the physical disk 0, and the SSD is the physical disk 1. The  HDD is 1TB and has an NTFS partition for data, and the SSD has the Ubuntu MATE installation.

So, the problem appears to be that the Ubuntu installer installs the "bootloader" (?) on the HDD instead of on the SSD, even though Ubuntu itself is on the SSD. So now, to boot Linux, I have to select the HDD (disk0) instead of the SSD (disk1), each time I boot. I know I can tell my BIOS to boot from the HDD (disk0), but I want to fix this.

Using the DISKS application, I made the ext4 partition on the SSD bootable, but still no luck. Any ideas? Help? THANKS!

---

### Post by ubfan1 on 2016-05-13
As you've discovered, Ubuntu ignores the  "boot" flag on partitions.  What type of machine are we talking about, UEFI or legacy.  What disk partitioning is used (msdos or gpt).  Makes a big difference on what type of bootloader you install, and the partitions necessary.

---

### Post by kwanbis on 2016-05-13
> **ubfan1 said:**
> As you've discovered, Ubuntu ignores the  "boot" flag on partitions.  What type of machine are we talking about, UEFI or legacy.  What disk partitioning is used (msdos or gpt).  Makes a big difference on what type of bootloader you install, and the partitions necessary.
My machine is a ThinkPad from 2011. I believe it is legacy. The SSD is fully partitioned for Ubuntu, no Windows in sight, so it is the default partition from the install, with a big ext4 partition. Hope that is what you asked.

---

### Post by Dennis N on 2016-05-13
If you are right, and it is a legacy (BIOS) installation, boot into Ubuntu. Run **lsblk** in the terminal. See which disk (sda or sdb) Ubuntu is installed on. Look for the disk containing the / partition if you are not sure or go by the size of the disk. If your Ubuntu is on sdb, run the command:
```
sudo grub-install /dev/sdb
```
Then
```
sudo update-grub
```
and the machine should thereafter boot to the Ubuntu disk if the boot order is correctly set in BIOS.

---

### Post by kwanbis on 2016-05-13
> **Dennis N said:**
> If you are right, and it is a legacy (BIOS) installation, boot into Ubuntu. Run **lsblk** in the terminal. See which disk (sda or sdb) Ubuntu is installed on. Look for the disk containing the / partition if you are not sure or go by the size of the disk. If your Ubuntu is on sdb, run the command:
```
sudo grub-install /dev/sdb
```
Then
```
sudo update-grub
```
and the machine should thereafter boot to the Ubuntu disk if the boot order is correctly set in BIOS.
Thank that fixed it. I had tried before but i used /dev/sdb1 and it didn't work.

I wonder why is still happening 4 or 5 years latter. Should I open a bug ticket?

---

### Post by grahammechanical on 2016-05-13
> I wonder why is still happening 4 or 5 years latter. Should I open a bug ticket?

If you want but it would be a waste of time as Ubuntu developers will not agree that it is a bug. The installer defaults to installing the boot loader on the first drive (sda). But we can change the location. 

The alternative is to ask the user what drive to install the boot loader to and if there is only one drive, as is the case for many people, that may cause confusion for a lot of people.

---

### Post by kwanbis on 2016-05-13
> **grahammechanical said:**
> If you want but it would be a waste of time as Ubuntu developers will not agree that it is a bug. The installer defaults to installing the boot loader on the first drive (sda). But we can change the location. 

The alternative is to ask the user what drive to install the boot loader to and if there is only one drive, as is the case for many people, that may cause confusion for a lot of people.
I see what you mean, but if Ubuntu ends up in a non functional mode after installation, is clearly a bug. I chose automatic install, by erasing the entire hard drive, there was no option to change the GRUB location.

---

### Post by Geoffrey_Arndt on 2016-05-13
For someone with some background and knowledge (such as you have), the recommended way to install Ubuntu is a custom install (the "something else" option).    I wish that were the default for multi-drive systems.   In the custom install process, the user is clearly asked where to install the bootloader.   If sda (the normal default) shows up, the user can/should simply change it there.   Problem solved.    I have a System76 Galago, and you drive setup is exactly the same as mine, but the folks at System76 clearly knew that Grub must be installed to sdb.

I agree with Graham . . this is not really a bug, but a little help bubble message could pop up and say "hey you dorfnick" . . . you have a dual drive system, and ubuntu is on sdb . . . so, install grub there".    Same thing applies if a user has done a full-actual install on a flash-stick or usb-flash-ssd.   In that case, the bootloader should be installed to sdc, sdd, etc, however that usb drive is ID'd.

---

