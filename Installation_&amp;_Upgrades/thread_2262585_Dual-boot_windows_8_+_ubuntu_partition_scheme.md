---
title: "Dual-boot windows 8 + ubuntu partition scheme"
date: 2015-01-25
forum: Installation &amp; Upgrades
---

### Post by ahobo on 2015-01-25
So I have some questions regarding a partition scheme with dualbooting Windows 8 and Ubuntu.

Let's assume I have the following scheme:
```

sda1: Windows OS    C:    50gb    NTFS
sda2: Ubuntu    /    15gb    ext4
sda3: Linux-Swap    8gb    swap
sda4: Windows user data    D:    300 gb   NTFS
sda5: Windows recovery  15gb  NTFS
```

Can / Should I put Ubuntu's **/home** partition in **sda4 **with Windows' user data partition so all my files can be in one place?
Are there drawbacks to doing that?
Should I put a partition in between **sda4** and **sda5** for Ubuntu's **/home** partition?

And optionally:
What's the difference between **/data** and **/home**? 
What are the advantages of having them separate?
Can you recommend a better partition scheme?

---

### Post by ajgreeny on 2015-01-26
There different options for you and which one you choose depends entirely on how you feel about having a separate /home partition and whether or not you have legacy BIOS or UEFI.

A separate /home partition must be on a Linux filesystem, by default ext4, so you can not make sda4 which is NTFS your Ubuntu /home, and if it were to be an ext4 partition, Windows will not see it nor be able to use it and share the data files.

You can, however, share sda4, the Windows NTFS data partition with Ubuntu quite easily, by editing /etc/fstab to mount sda4 at boot and using it as the data partition for both OSs; that is what I would do.  Anther alternative is to make soft links between folders in your  Ubuntu /home partition and the folders in the shared partition. this  makes it appear that the data files and folders are in the Ubuntu /home but  in reality they are all still sitting in sda4, the NTFS shared partition.


You then have a choice of whether to make a separate /home partition or to leave /home as a folder within root.  A separate /home partition will not need to be very big as it will contain only configuration folders and files; probably 5GB will be overkill, but I don't know your setup so it's difficult to say exactly how big.  I would leave /home within root and just make sure it was backed up regularly to a DVD or flash drive.

So, my suggestion is to share the current sda4 data partition between both OSs, and keep /home in the root partition but just make sure it is backed up regularly.  You can make all your Ubuntu partitions logical within an extended partition if you're using BIOS with its 4 partition limit, as that will assist with that limitation; Ubuntu will boot quite happily from logical partitions whereas windows will simply throw in the towel and go nowhere from a logical partition.  The advantage of having a separate home containing all your configuration and data is that it makes any reinstallation of the OS easier and quicker; you just make a new root partition and tick the box to format that when you install, but use only the mountpoint /home for  the old /home partition and DO NOT FORMAT that one, so it keeps all the files and folders untouched.  It's still good practice to backup everything before carrying out any partition editing such as a new installation just in case anything does go wrong, eg a power-loss just at the wrong moment.

For swap there used to be a rule of twice the size of your ram; that has now largely disappeared, and unless you have 8GB ram and must hibernate the system, 2 - 4GB is generally thought to be sufficient.

I hope that helps you; if you are still a bit befuddled come back again with more questions.

---

### Post by ahobo on 2015-01-26
Awesome, this is really very helpful!
I'll probably do what you recommended and use links to sda4.

Thanks!

---

