---
title: "Dual booting with custom partitions on my laptop."
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by Extol11 on 2013-02-28
So I created all of the partitions on my laptop and had it dual booting nicely. About two days ago, lubuntu wanted to load only on CLI and while I was trying to fix this I broke something and it did not want to let me log in graphically. So while trying to reinstall Lubuntu I accidentally told it to use the whole hard drive. I had to recreate all of the partitions again but for some reason Grub was not able to load windows. It just kept going back to the grub menu when you selected Windows 7.

Here's my partition setup: 50GGB hard drive
*150GB Primary partition for Windows
*36GB Logical partition for Lubuntu
*4GB Logical partition for Swap for Lubuntu
*275GB (More or less) Logical Partition for Storage.

I'm going to try installing lubuntu again on it but I don't want to have that problem again. I think I might have installed grub on the windows partition instead of the small (100MB) partition that windows creates. Would that cause any problems? Any help will be greatly appreciated.

---

### Post by presence1960 on 2013-02-28
> **Extol11 said:**
> So I created all of the partitions on my laptop and had it dual booting nicely. About two days ago, lubuntu wanted to load only on CLI and while I was trying to fix this I broke something and it did not want to let me log in graphically. So while trying to reinstall Lubuntu I accidentally told it to use the whole hard drive. I had to recreate all of the partitions again but for some reason Grub was not able to load windows. It just kept going back to the grub menu when you selected Windows 7.

Here's my partition setup: 50GGB hard drive
*150GB Primary partition for Windows
*36GB Logical partition for Lubuntu
*4GB Logical partition for Swap for Lubuntu
*275GB (More or less) Logical Partition for Storage.

I'm going to try installing lubuntu again on it but I don't want to have that problem again. I think I might have installed grub on the windows partition instead of the small (100MB) partition that windows creates. Would that cause any problems? Any help will be greatly appreciated.

You don't want to install GRUB on any windows partition, you want it on MBR. On the partitioning window at the bottom you will see a drop down box to choose where boot loader (GRUB) gets placed. Choose sda, assuming you have a single hard disk.

---

### Post by Extol11 on 2013-02-28
> **presence1960 said:**
> You don't want to install GRUB on any windows partition, you want it on MBR. On the partitioning window at the bottom you will see a drop down box to choose where boot loader (GRUB) gets placed. Choose sda, assuming you have a single hard disk.

I do have a single hard drive, it's a laptop. Ok, to be on the clear: That'd be the 100MB (or so) partition that's at the very beginning of the drive, right?

---

### Post by presence1960 on 2013-02-28
> **Extol11 said:**
> I do have a single hard drive, it's a laptop. Ok, to be on the clear: That'd be the 100MB (or so) partition that's at the very beginning of the drive, right?

Incorrect. The MBR is at the very beginning of the disk before any of the partitions.

Forgot to ask: what windows are you running? Is your machine booting from BIOS or UEFI?

I would assume it is BIOS because you have logical partitions. If it is UEFI your disk would be gpt and there is no need for logical partitions as there is no limit on partitions on a gpt disk. But I would rather be safe than sorry.

---

### Post by Extol11 on 2013-02-28
> **presence1960 said:**
> Incorrect. The MBR is at the very beginning of the disk before any of the partitions.

Forgot to ask: what windows are you running? Is your machine booting from BIOS or UEFI?

I would assume it is BIOS because you have logical partitions. If it is UEFI your disk would be gpt and there is no need for logical partitions as there is no limit on partitions on a gpt disk. But I would rather be safe than sorry.
It's a bios. I'm running windows 7. I had managed to get all of this right the first time but then Lubuntu (for some unknown reason) boots up in CLI form, I log in and try to shut it down with sudo halt and then it doesn't turn off. The next time I boot up Lubuntu, it doesn't want to loging into the LXDE session and just keeps throwing me back into the loging screen every time I input the password right. And I think what I'm talking about is a small 100MB partition that is at the very beginning of the disk. Windows puts it there. I'll try it again tomorrow. I just tell it to install grub in the very beginning of the disk, got it. 

PS: I didn't know that UEFI had those features, dang!

---

### Post by Mark Phelps on 2013-03-01
The small partition at the front of the drive is the Windows boot partition.  You don't want to mess with this in any way, because doing so will prevent Windows from booting.

Grub actually gets installed two places -- a small part to the MBR at the beginning of the drive, and the rest to a Linux partition.

As mentioned, choose "sda" to install GRUB, not "sda1" -- or any other numbered partition.

---

### Post by Extol11 on 2013-03-01
> **Mark Phelps said:**
> The small partition at the front of the drive is the Windows boot partition.  You don't want to mess with this in any way, because doing so will prevent Windows from booting.

Grub actually gets installed two places -- a small part to the MBR at the beginning of the drive, and the rest to a Linux partition.

As mentioned, choose "sda" to install GRUB, not "sda1" -- or any other numbered partition.
I'm going to install it now. Thanks for the help, it's greatly appreciated.

---

