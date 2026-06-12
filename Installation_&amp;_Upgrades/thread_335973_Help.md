---
title: "Help"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by J.P. on 2007-01-11
Good Morning Ladies and Gent;
I will get down to the bare facts right away. I have two Sata drive (each is 250 GB) that is sat up Raid 1.They are partition out as C:\ Vol-1 19.53 GB Window XP Pro, D:\ Vol-2 164.52 GB Virtual Memory and programs (O.K. Games), E:\ Vol-3 232.88 GB NTFS Extermal USB Disk drive, 48.83 GB Unallocated (where I'm trying to put Ubunty 6.06 LTS ( I think I have)). My problem is that after I have install Ubuntu I am told to reboot so I let Ubuntu do her thing and I remove the disk and reboot and it goes into Windows. No grub menu or anything just back into windows. What am I missing? Don't I get a chance to make up my mind as to which way I want to go. To Ubuntu or to Windows.](*,)
Now I sure would be thankful if one of you youngun could give this old man a helpful hand.

---

### Post by rpradeep on 2007-01-11
Has the installation process go upto where it will install the GRUB boot loader into the MBR (master boot record)

---

### Post by Wim Sturkenboom on 2007-01-11
If I understand you correctly, you installed Ubuntu on the external disk. As you don't see grub, it's probably also fully installed on there.
So you have to boot from the external HD; check your BIOS.

As far as I understand Grub:
Grub consists of two or more 'parts'. One you install in i.e the MBR. The other(s) go on your Linux 'disk'.
This implies that you always need your external disk to be connected, even when you want to go to Windows.

---

### Post by J.P. on 2007-01-11
> **rpradeep said:**
> Has the installation process go upto where it will install the GRUB boot loader into the MBR (master boot record)

As far as I can figure out, the installation process went thru the compleat installation process. And I am going by what the installament told me. Installament Conpleat. 
I also did not install on my extermal disk.

---

### Post by bapoumba on 2007-01-12
Hi, J.P.

I may not be able to help you all the way thru, but :

1- have you tried hitting <escape> key when booting ? Sometimes grub menu is hidden (there is an option to comment out in /boot/grub/menu.lst)

2- did you install with desktop or alternate cd ? Desktop cd is also a live cd from where you could do some tests

3- I do not know windows at all, but from there, do you windows partitions have the expected size ? (I'm not sure windows will be able to see linux partitions, i just do not know)

---

