---
title: "Minimal bash line editing issue"
date: 2019-05-19
forum: Installation &amp; Upgrades
---

### Post by gustavoplena on 2019-05-19
A few months ago I decided to install Ubuntu 18 on dual boot along Windows 10 I already had in my notebook. However, after some weeks, I realized that I let too little memory in my SSD (480 GB) for Windows, so I took some space from Ubuntu partition for apps and files that Windows could access. 
After some days I couldn't use Ubuntu anymore and Windows got really slow.
Yesterday I decided to delete the Ubuntu partition by the disk manager on Windows. Today, trying to use the PC I simply can't boot Windows, I end up in this screen saying "minimal bash line editing"

I really appreciate any help!

---

### Post by TheFu on 2019-05-19
Just a guess ... 

You'll need to use the Windows Rescue disk.
Looks like you are stuck in grub which is part of the multi-OS boot solution, but that is managed by Linux.  You need for Windows to take over the boot management - hence the Windows Rescue disk.

---

### Post by Impavidus on 2019-05-19
Your UEFI loads grub (the Linux boot loader) and grub, after reading some data from the Ubuntu partition, boots Ubuntu or loads the Windows boot loader. But since you deleted the Ubuntu partition, grub can no longer find these data and gives an error.

You may be able to boot Windows directly from UEFI.

If you want to have both Windows and Ubuntu, some more information on your system may help.

---

### Post by gustavoplena on 2019-05-19
Actually I just need Windows now, so it would be ok to keep just with it. 
How would I be able to bot from UEFI?

Thanks in advance

---

### Post by gustavoplena on 2019-05-19
Hey, actually I did manage to boot Windows now, changing the boot priority in BIOS! Thank you guys so much! 
I guess I will just reinstall everything so I don't have a problem in the future.

---

### Post by Impavidus on 2019-05-20
Yes, that's what I meant. It shouldn't be too hard to remove the Ubuntu entry from the UEFI menu. I can't tell you how exactly.

---

