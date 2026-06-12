---
title: "1 drive, dual boot, win7, 64-bit, from scratch"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by morganpatrick on 2011-09-17
Hello,

I run a dual boot machine on my desktop, and now I would like to do the same on my laptop. On the desktop I have two drives, but on my laptop I have a brand-new 500gb drive.

On the desktop, my ubuntu drive is in four partitions: boot, swap, root and home. I find this is the best way to keep my data intact when ubuntu becomes corrupt, or grub becomes corrupt, or an upgrade fails.

Here is what I would like to see on the drive, ideally:
[LIST]
[*]Grub, at the front of the disk
[*]a boot partition for ubuntu
[*]a swap partition for ubuntu
[*]a root partition for ubuntu's operating system
[*]an OS partition for windows 7
[*]a big data partition where I can keep my music, videos, pictures, and other files, for either operating system
[/LIST]

However, I believe the maximum number of partitions for an NTFS drive is 4. Since I need to get both operating systems on one drive, I don't think this scheme will work.

My question is, what would be the best partition scheme for this? In general, what is the best practice for sharing windows 7 x64 and ubuntu 11.04 x64 on a totally blank hard drive?

Thanks in advance and sorry if this is redundant and I just can't find the right thread.

---

### Post by SirDrexl on 2011-09-17
Well, the drive itself isn't NTFS; that only applies to partitions (even  though a drive may only have one partition on it).  Maybe you're  thinking of the limit of 4 primary partitions.
 
 The way I did it recently was to let Windows have the bootloader, since updates could overwrite it (which would wipe out GRUB).
 
 Windows will create a 100MB recovery partition (and this is where it  boots from).  So that will use 2 primary partitions, but you won't run  out as long as some of the Ubuntu partitions are logical volumes in an  extended partition.
 
 I installed Windows first, specifying a 30GB partition, and left the  rest unallocated.  Then I formatted the remaining during the Ubuntu  installation.

 Then, I used a program called EasyBCD to add an entry for Ubuntu in Windows' bootloader.  The whole process is on this site: [http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/](http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/)
 
 You can create the partition for storage either in the Ubuntu  installation or after both OSes are installed (I'd probably do the  latter).

---

### Post by Blasphemist on 2011-09-17
Here (in the screen shot) is what I did. I started with Win7. I have everything you're asking for and the difference is that I have a bunch of distros instead of just one. I did just ubuntu first and that has affected the partition numbers but you can see what you need. Oh, there is one difference. I don't use a boot partition. And I don't use the windows boot manager but rather grub, as opposed to the post on doing that. When I install distros I have them write to the sda mbr and their own partition. I frequently change the "grub controlling" partition as I try to optimize grub2.

---

### Post by morganpatrick on 2011-09-26
Thanks for the replies, they were helpful. I went ahead and installed my dual boot this way: Windows boot loader, Windows OS, ntfs data, Ubuntu installation, swap. The last two partitions are logical.

I have a separate problem now, though. My windows 7 installer put the OS on the data drive. I didn't have an option to specify which partition to install to.

My windows 7 installation, with other software loaded, is now about 20gb. My OS partition is 60gb. The data partition is like 300gb. Can I used parted magic or gparted to move my OS to the OS partition?

Please advise, thank you.

---

### Post by SirDrexl on 2011-09-26
The problem might be that it saw the NTFS partition and then took that for installation.  I think you could intervene by choosing "advanced" (or whatever it's called) so you can tell it where to install.

Was there unallocated space for Windows to create its partition and install in?  If you want to try again, make sure you have the empty space so the installer can create the new partitions and install there.

---

### Post by oldfred on 2011-09-26
If you partition in advance, Windows installs to the active partition or the one with the boot flag. Did you have the boot flag on your data partition? If so move the boot flag with gparted or from Windows set active partition to install to which NTFS partition you want.

---

