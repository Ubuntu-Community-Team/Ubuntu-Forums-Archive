---
title: "grub-install warning - embedding is not possible"
date: 2017-12-29
forum: Installation &amp; Upgrades
---

### Post by bilekbp on 2017-12-29
Hello, after installing Ubuntu 17.04 alongside Windows 10 on my Surface Book, Grub never appeared. I'm not sure if it was ever successfully installed, so I'm attempting to do so from a Live USB of 17.04 now. 

I've tried the following commands:
sudo mount /dev/sdXXX /mnt
sudo mount /dev/sdXX /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/sdX

(sdXXX is my Ubuntu partition, sdXX the EFI system partition, sdX my hard drive)

I receive the following errors:
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.

How would I be able to fix this to enable me to install GRUB?

---

### Post by oldfred on 2017-12-29
Your system should be UEFI and generally better to install in UEFI boot mode.

But the error is that you have a gpt partitioned drive which is normally used with UEFI, but have installed Ubuntu in BIOS boot mode.
Then it installs grub to the gpt's protective MBR, but you do not have a bios_grub partition for it to install correctly in BIOS mode.

How you boot install media, is then how it installs. 
So if you want UEFI boot installer in UEFI, if you want BIOS boot on BIOS boot mode.

But you need to have either the ESP or bios_grub.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by bilekbp on 2017-12-31
Thank you for all of the assistance. May I assume based on the suggestions in this post that I should go ahead and reinstall with the settings you are recommending, that I can't repair my installation since I did not install Ubuntu in UEFI mode?

---

### Post by oldfred on 2017-12-31
If on gpt drive, which it seems like, you just need to reinstall to UEFI version of grub - grub-efi-amd64.
You can do that with Boot-Repair, booted in UEFI mode and the advanced options to totally uninstall & reinstall grub. You do not need to reinstall the entire system but can as long as you use Something Else option and choose same / (root) and same /home partitions.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by bilekbp on 2018-01-02
Thank you again - I ended up creating an EFI-only boot disk and reinstalling just because I had partitioned my 100GB as / only, to create a swap space and /home. The installation and subsequent boot through GRUB to Ubuntu completed without a hitch.

---

