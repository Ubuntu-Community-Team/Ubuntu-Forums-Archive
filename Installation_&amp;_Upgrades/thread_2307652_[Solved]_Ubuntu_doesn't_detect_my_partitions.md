---
title: "[Solved] Ubuntu doesn't detect my partitions"
date: 2015-12-27
forum: Installation &amp; Upgrades
---

### Post by HDArtworks on 2015-12-27
[COLOR=#111111][FONT=Ubuntu]Hi.
I install windows 7 in my pc and i try to install another linux distro. But when i go to ubuntu live and launch GParted, this error shown to me:
[/FONT][/COLOR]> /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables. Or perhaps you deleted the GPT table, and are now using an msdos partition table. Is this a GPT partition table?[COLOR=#111111][FONT=Ubuntu]

And if i press yes/no Gparted dosen't detect my partitions and it shows me about 500GB free space!

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]How can i fix this issue? And i don't want to lose my partitions and data. Is there any way to fix this issue without losing data? Thanks...[/FONT][/COLOR]

---

### Post by TheFu on 2015-12-27
Use the operating system that created the file systems to correct any file system issues. If you post the output from **sudo parted -l**, we might be able to provide a little more guidance.

Windows doesn't like GPT without both 
a) UEFI
b) 64-bit OS

So, if the Linux install is using GPT, but both of those Windows requirements are not true, then you must use MBR partitioning for the boot disk in order to support Windows on that machine.  GPT can be used for non-booting Windows drives from Vista and newer releases.

---

### Post by HDArtworks on 2015-12-27
First i create partitions in gparted and ubuntu live Disk. But i couldn't install windows 7. So after that i delete the partitions and create a new partitions with partitioning tools in windows 7 installing peccess.
In win7 everything is works fine and my partitions is there. But in GParted i get that error and i can't see my partitions.

And here is the output of **sudo parted -l** :
> 
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? 


Anyway i find this method, But i'm not shure if that works and i afraid that i lose my data!
[http://askubuntu.com/a/473073](http://askubuntu.com/a/473073)

---

### Post by grahammechanical on 2015-12-27
Please load into Windows and use a Windows utility to show the partitions and then take a screen shot and post it in this thread. Let us see what Windows is seeing. It might bring some enlightenment.

Also, does the motherboard have a BIOS boot system or a UEFI boot system. We use the word BIOS to refer to a motherboard utility that we can use to change motherboard settings. But motherboards released in recent years have something called UEFI. Knowing what we have could be important information.

The GPT partitioning scheme is backwards compatible with a BIOS motherboard but I think that there is a requirement for a BIOS boot partition. Whereas, with UEFI the requirement is for an EFI boot partition. As I say, "I think." But the lack of a BIOS boot partition may be what Gparted is complaining about.

Regards.

---

### Post by HDArtworks on 2015-12-27
Here is the screenshot from my partitions in windows.(Attached)
I have 136GB for linux, the others is NTFS.

My motherboard is P5Q-SE. I don't know my motherboard is BIOS boot system or UEFI boot system, although i think it is BIOS boot system.

---

### Post by oldfred on 2015-12-27
Windows only boots in UEFI mode from gpt partitioned drives.
Windows only boots in BIOS mode form MBR(msdos) partitioned drives.

But when you install Windows in BIOS boot mode to a gpt partitioned drive it does not correctly convert drive to MBR. It leaves the backkup gpt partition table and only converts primary gpt partition table. Linux tools then see both MBR & gpt and get confused and assume you can only erase drive & start over.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by HDArtworks on 2015-12-27
Thanks for answer.
I just have one more question.
If i use gdisk or FixParts, my partitions is losing data or my data is safe?
I really care about my data and i don't have any external hard drive to backing up my data. So, thats so good if tell me that my data is safe or not!
Thanks a lot.

---

### Post by oldfred on 2015-12-27
Data is never totally safe with any system change. 
And hardware fails, usually just before you wanted to do a backup. Or even Lightning strikes and destroys system.

First thing you need to do is plan some way to backup all your data. I have some data on two drives, and do images to DVDs and flash drives of my critical data, so I have versions that are before edits or deletes that I may want later.

---

### Post by HDArtworks on 2015-12-27
Thanks a lot for all answers.
The problem is solved. :)

---

