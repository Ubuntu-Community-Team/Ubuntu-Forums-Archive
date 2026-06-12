---
title: "Installing Ubuntu on Two Hard Drives"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by mrees84 on 2013-06-01
Hello

I have recently bought a 64GB SSD as a second hard drive. I want to install 13.04 on the new SSD and boot from the drive and store programmes on it and use the exisiting 320GB HDD for data storage only. There is already an existing install of 13.04 on the HDD which i dont mind wiping as the data on it is backed up in multiple places. I am however a little confused as to how to go about a fresh install and how to partition the two disks in order to achieve the above. Any advice would be welcome.

Thanks
Matt

---

### Post by fantab on 2013-06-01
Currently your HDD is the first Boot Device setup in your BIOS. If you want to use and boot from SSD then you have change the HDD boot priority in the BIOS set up to first Boot SSD. When installing Ubuntu on SSD you must use the manual method to install Ubuntu with the option "Something Else'. Install GRUB - Boot loader to the SSD.

Regarding making optimum use of SSD 64GB I would create three partitions on it:
30GB Ext4 / Ubuntu 13.04
30GB Ext4 / Ubuntu 12.04
4GB SWAP

HDD 320GB:
20GB Ext4 Free
300GB Ext4 DATA.

I wouldn't use separate /home. Because from only 64GB SSD /home will be small and defeat the purpose of having it to store data.
Two Ubuntu's on SSD? Yes... 12.04 is LTS (supported upto 2017) and very stable. This will be my fallback Ubuntu in case something goes awry with 13.04 which is latest and not as stable as 12.04.

300GB for all DATA is a good idea. 20GB free just in case.

My two cents...

---

