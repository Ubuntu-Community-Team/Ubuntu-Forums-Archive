---
title: "Can I just delete the Mint partitions and install Ubuntu? Or are there more steps?"
date: 2019-09-19
forum: Installation &amp; Upgrades
---

### Post by skyturnred2 on 2019-09-19
I'm currently dual-booting Windows and Mint. I want to just replace Mint with Ubuntu and not change anything with the Windows installation. 

Here's how I set it up. I followed this guide so that I can just disconnect the Mint drive whenever I want and the computer would boot up as if it was never dual-booted, never go into the grub menu or anything. 

So I have an SSD and a hard drive. The SSD has the Windows installation, and the other has the Mint installation installed as follows

1 - I set the motherboard to UEFI only

2 - Disabled fastboot in Windows

3 - Booted up into a live Mint usb

4 - Created a new partition table /EFI - 650 mb, primary

5 - Created a /root partition - 20 gb, ext4

6 - Created a /swap partition - 2 gb, used as swap

7 - Created a /home partition with the rest of the drive space

So my question is, can I just delete all of those partitions, reformat the entire drive so it's as if it was new, and then continue on from step 3 with Ubuntu instead?

---

### Post by ajgreeny on 2019-09-19
Choose "Something else" at the disk preparation stage of installing Ubuntu and then point to the separate partitions for root, swap if you really want to, though a swapfile is now used and a separate partition is unnecessary, and also /home, but remove the tick in the Format box for /home to keep all your data files, which I assume you must have, untouched.

You may find that some, or even many of the hidden files and folders in your current Mint home partition (which version of Mint?) are incompatible with your new Ubuntu, so it is probably wise to remove most of those hidden configuration files and folders whilst still in the live system, before rebooting into the new Ubuntu installation by just moving those hidden files and folders to a temporary folder in the new /home and then try using them one by one; I may be wrong and many of them may work fine but I simply do not know how likely that is.

---

### Post by oldfred on 2019-09-19
Do not know Mint, but based on Ubuntu.
Ubuntu's Ubiquity installer only installs grub2's UEFI boot loader to first drive, usually the Windows ESP which they then share. You have to leap thru a couple of hoops to install to ESP on HDD. Either copy /EFI/Boot & /EFI/ubuntu from SSD to HDD's ESP. Or see work around in this bug report by oldfred.
       Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

If you reformat ESP, it gets new UUID & GUID. So old entries in UEFI will not work and should be removed. And old folder in ESP should also be removed if not reformatted.
       
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

