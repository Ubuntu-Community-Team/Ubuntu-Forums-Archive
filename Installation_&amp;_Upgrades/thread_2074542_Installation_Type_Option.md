---
title: "Installation Type Option"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by n4lbl on 2012-10-21
On a new Asus X54C WIN7 laptop I am trying to install 12.10 desktop 64 bit.  In the documentation ( [http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest) ) step 4 'Allocate drive space' (installation type box) the first option is 'Install Ubuntu alongside Windows 7'.  The actual installation type box that the installer presents me has 4 options:  1) 'Erase disk and install Ubuntu', 2) 'Encrypt the new Ubuntu installation ...', 3) 'Use LVM with the new Ubuntu installation;, and 4) 'Something else'.  What have I done wrong that makes me miss the 'Install Ubuntu alongside Windows 7' option??

GParted shows:
Partition		File System	Label		Size		Used		Unused		Flags
						
/dev/sda1	fat32		RECOVERY	25.00 GiB	12.07 GiB	12.93 GiB	hidden, lba
/dev/sda2	ntfs	 		System		100.00 MiB	33.59 MiB	66.41 MiB	boot, diag
/dev/sda3	ntfs			OS			119.24 GiB	38.79 GiB	80.45 GiB	
/dev/sda4	ntfs			DATA		153.76 GiB	3.00 GiB	150.76 GiB	
I wish I could format the data above!	

My goal is to install 12.10 in in the sda4 partition.

---

### Post by darkod on 2012-10-22
By creating sda4 from windows it made it ntfs and linux doesn't install on ntfs. If that partition is empty, and you want all that space for ubuntu, open in windows Disk Management and delete it.

Then start the ubuntu install and it will offer the "along side option" because there will be only 3 partitions + the unallocated space it will use.

If you want to install manually, you can, and you will need to created the partition you want into that unallocated space during the install.

---

### Post by 2F4U on 2012-10-22
> **n4lbl said:**
> On a new Asus X54C WIN7 laptop I am trying to install 12.10 desktop 64 bit.  In the documentation ( [http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest) ) step 4 'Allocate drive space' (installation type box) the first option is 'Install Ubuntu alongside Windows 7'.  The actual installation type box that the installer presents me has 4 options:  1) 'Erase disk and install Ubuntu', 2) 'Encrypt the new Ubuntu installation ...', 3) 'Use LVM with the new Ubuntu installation;, and 4) 'Something else'.  What have I done wrong that makes me miss the 'Install Ubuntu alongside Windows 7' option??

GParted shows:
Partition        File System    Label        Size        Used        Unused        Flags
                        
/dev/sda1    fat32        RECOVERY    25.00 GiB    12.07 GiB    12.93 GiB    hidden, lba
/dev/sda2    ntfs             System        100.00 MiB    33.59 MiB    66.41 MiB    boot, diag
/dev/sda3    ntfs            OS            119.24 GiB    38.79 GiB    80.45 GiB    
/dev/sda4    ntfs            DATA        153.76 GiB    3.00 GiB    150.76 GiB    
I wish I could format the data above!    

My goal is to install 12.10 in in the sda4 partition.

Seems as if you already have 4 partitions. If these are primary partitons and you are on a BIOS instead of EFI system, you can install unless you change one of the primary partitions into a logical. A BIOS system can have a maximum of 4 primary partitions, so at the moment you have no partition left to install on. Thats why you won't get certain options in the installation dialogue.

---

### Post by n4lbl on 2012-10-22
Many thanks.  All is working now.  I chose the Windows partition delete option to avoid the multiple boots for error correction as Windows discovers it's world has changed.

I'd like to mark this 'solved' but don't know how.

Again,,, many thanks.

---

### Post by critin on 2012-10-22
Glad you got it going! 
> 
I'd like to mark this 'solved' but don't know how.

Click on Thread Tools in the top menu above postings.

---

### Post by n4lbl on 2012-10-22
Again,,, thanks.

---

