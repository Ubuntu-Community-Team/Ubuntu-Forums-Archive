---
title: "HP pavillion dv4000 not booting ubuntu"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by tiito78 on 2006-10-19
Hi!!!

sorry 4 my english!!!!!!!!!

I´m trying to put the Ubuntu Live Cd on my USB memory Kingstone 
1G. I have followed the guide from wiki.ubuntu.com ->"Installing Ubuntu on USB Pendrive using Linux".

I have a Hp pavillion dv4000 notebook
Intel Processor 1.8GHz
ATI Mobility Radeon X700
1GB RAM

What I did: 

First I downloaded the ISO file using windows XP. Then I start Ubuntu using the Live Cd, this becouse I don´t have any Linux system on my computer. 
When the desktop start I mount my windows Hd (NTFS)

code: 
mkdir /media/windows
mount -t ntfs /dev/hda5 /media/windows/ -o uid=ubuntu,gid=users,umask=0222


Now I can see all my files on my ntfs Hd. I extract the ISO file to my USB (dapper)with all the files that have to bee there. Then I run apt-get install syslinx && mtools.
After that I run syslinux /dev/sda1 (sda1 = dapper).
When I look in the dapper cat I can see the file ldlinux.sys that syslinux create, but whit a lock on. 

When I restart my computer nothing happend, syslinux does´nt load. 

If I put the USB memory on another computer everything works fine. 

What can I do to make it work on my computer?

Hope u can help me.... I really want to make this work!!!!!!!!

My best reguards, Gracias: 

Felipe Gomez Morales

---

### Post by lfloyd on 2006-10-21
try boot options live acpi=off

---

