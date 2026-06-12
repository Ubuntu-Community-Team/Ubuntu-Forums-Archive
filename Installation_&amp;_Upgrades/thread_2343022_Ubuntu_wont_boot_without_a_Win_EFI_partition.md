---
title: "Ubuntu wont boot without a Win EFI partition"
date: 2016-11-12
forum: Installation &amp; Upgrades
---

### Post by izznogooood on 2016-11-12
I bought a new SSD disk to replace my SSHD i currently use. 

When I was going to reinstall Ubuntu i ran upon a problem i had forgotten. My computer wont boot unless theres windows on it!

After a little research trying every possible bios settings I found that setting my SSD in SATA2 and using my old SSHD (with a small win inst.) as SATA1 worked.

The thing is though, When I installed Ubuntu i manually sat the installer to ignore the EFI on the SSHD (with win) and created a new EFI on the SSD. It still used the EFI on the SSHD! So i could just delete the EFI on the SSD i asked it to use.

I dont want windows! Why cant my Lenovo boot of the Ubuntu EFI partition (No operating system found).

My theory is now that I can install windows on the SSD, delete everything except the EFI partition. Then install ubuntu which will use the same EFI and work.

Help! :D

PS: This means that if I was a complete beginner i would break my computer if i replaced windows with ubuntu.

---

### Post by ajgreeny on 2016-11-12
There is a long thread at [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) with lots of info on UEFI and the problems of some machines refusing to boot anything but a windows efi bootloader meaning you have to rename the ubuntu efi bootloader files.

I have never had this personally so can give you no more details but hopefully that thread might help you.

---

### Post by oldfred on 2016-11-12
There is no Windows ESP - efi system partition.
There is only the UEFI ESP which is used by all UEFI bootable installs. 

And for whatever reason grub only installs to the ESP on drive seen as sda.
If you want grub on another drive you have to manually copy the /EFI/ubuntu folder from the ESP on sda to the ESP on your other drive.
But if an external drive, UEFI only boots from /EFI/Boot/bootx64.efi.
For external drives we then copy shimx64.efi to bootx64.efi in the external drives ESP. You still have to have the /EFI/ubuntu folder as shim is hard coded to find other files in /EFI/ubuntu.

For UEFI installs you need the  ESP, / (root), and  swap as minimum partitions. Many add additional partitions for /home, /mnt/data, backups (not really backups but another copy), and partitions for larger groups of specific data files.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by izznogooood on 2016-11-12
Thank you both for your inputs.

I did a simple workaround that i would not recommend. I just copied the EFI partition from the SSHD to the SSD (gparted) and reinstalled using that as EFI and making my partitions the way I like it.

So for some reason my BIOS does not like the EFI partition created by the Ubuntu installer.

Anyway, no windows now :popcorn:

---

### Post by oldfred on 2016-11-12
Many UEFI will find the .efi entries in the ESP and add them back on a cold (full power down) reboot.
Some only find Windows, some also find the fallback or /EFI/Boot/bootx64.efi and a few will add Ubuntu.

But you can add any missing entries with efibootmgr. And most newer UEFI can add entries from UEFI directly. Some like Acer require a UEFI supervisory password to be able to see other/new entries to add.
see 
man efibootmgr

To see current entries:
sudo efibootmgr -v

---

