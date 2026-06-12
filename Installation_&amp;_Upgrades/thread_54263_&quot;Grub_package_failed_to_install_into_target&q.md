---
title: "&quot;Grub package failed to install into /target/&quot;"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Adiabatic Expansion on 2005-08-04
I'm trying to install Ubuntu on the following system:

1 36   GB SATA drive with NTFS partition
1 120 GB EIDE drive with NTFS partition
1 160 GB EIDE drive (set up as primary master) <-- Ubuntu will be taking this whole drive for itself

I don't care about dual-booting with Windows XP, all I want to do with this installation is drop it on its own drive and be able to read my data from the NTFS partitions when needed. 

The problem I've been having is that no matter how I try to partition this disk, both GRUB and LILO utterly fail to install and give the following error message:

[INDENT][I]The grub package failed to install into /target/. Installing GRUB as a boot loader is a required step. The install problem might however be unrelated to GRUB, so continuing the installation may be possible.

GRUB installation failed. Continue anyway?[/I][/INDENT]

Substitute "LILO" for "GRUB" for the error message that pops up with LILO. Obviously, a vague message like this doesn't help me much, but perhaps someone else here has run into this problem before.

Here are the partitioning schemes I've tried so far: 

[list]
[*] Allow Ubuntu to automatically select partition sizes, filesystems and mountpoints from a blank disk.
[*] Set up a 50 MB /boot partition in ext2 at the beginning of the disk, then a 2.7 GB swap, then the rest of the disk for / in XFS.
[*] Do the same as above, but with ext3 instead of XFS.
[*] Do the same as either of the last two, but add the option to mount /boot as read-only (this makes sense to me, how often would you write to /boot during normal usage?)
[/list]

I've tried installing LILO either on the MBR or on the /boot partition, but no such luck with either. GRUB doesn't give me any such options in the installer menu, so I have no idea where it's trying to install.

---

### Post by generallee5686 on 2006-10-16
bumping this because i get the same exact error message.

Anyone have any ideas?

---

### Post by bulldog on 2006-10-16
Yes try this one.

It install grub at the hdd where Ubuntu is installed.

Make this your master boot device and you should be able to choose which OS you want to boot.
Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

