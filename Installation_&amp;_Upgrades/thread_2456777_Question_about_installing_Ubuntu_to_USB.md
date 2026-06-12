---
title: "Question about installing Ubuntu to USB"
date: 2021-01-19
forum: Installation &amp; Upgrades
---

### Post by canuckled on 2021-01-19
Is it possible to install Ubuntu to a USB stick? I'm not talking about a bootable stick, for the purposes of trying it out, or installing to a computer. I was wondering if it was possible to have Ubuntu installed as if it was a portable computer?

---

### Post by oldfred on 2021-01-19
I have installed to flash drives & SSDs as USB drives in both BIOS and UEFI boot modes.
Often better not to use Ubuntu, but use one of the lighter weight flavors.
You need to partition in advance, I suggest gpt even if BIOS. 
When first starting to convert from my old BIOS system to newer UEFI system, I used gpt but had to have a bios_grub partition for BIOS boot and an ESP for UEFI boot.
And then only a reinstall of grub could convert the install from one boot mode to the other. 

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.
1. 30+ GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB or all (See below if 18.04 or later) Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
4. You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
5. No swap partition for 18.04 or later, it uses a swap file like this entry in fstab:
     /swapfile                                 none            swap    sw              0       0

[https://ubuntuforums.org/showthread.php?t=1872303](https://ubuntuforums.org/showthread.php?t=1872303)
[https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083812#1083812](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083812#1083812)
USB settings to help speed & life
[https://ubuntuforums.org/showthread.php?t=2350851&p=13600375#post13600375](https://ubuntuforums.org/showthread.php?t=2350851&p=13600375#post13600375)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[https://en.wikipedia.org/wiki/Flash_memory](https://en.wikipedia.org/wiki/Flash_memory)

---

### Post by ActionParsnip on 2021-01-19
Sure. Ubuntu doesn't care. Just remember to write GRUB to the USB stick and it can boot wherever you plug it in and tell the BIOS to boot USB first

---

### Post by tea for one on 2021-01-19
> **oldfred said:**
> 
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.

Yes, I am an advocate of this approach.

If you have multiple drives accessible when performing an Ubuntu installation, human error and uncertainty creep in unknowingly (especially if this is your first attempt at installing Ubuntu)

As mentioned by [COLOR="#0000FF"]oldfred[/COLOR], a lighter flavour e.g.Xubuntu would be preferable for a USB stick.

---

