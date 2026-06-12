---
title: "Grub doesn't load. Straight to XP"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by Dodelijk on 2007-12-18
Hello All, 

I've just installed Ubuntu on my desktop and everything went fine. When I start my machine up the Grub boot loader asks me which operating system to choose and all is good. Following this success I've tried to install on my laptop. This time the bootloaded does not appear when i boot the comp. and it goes straight to XP. Here's how i my partitions are set out and how i installed: 

I have one disk with four partitions:
1 - a very small partition for DELL's diagnostic things(FAT16). 
2 - a partition of around 15  Gb for this XP installation. 
3 - a partition (NTFS) for storing work. 
4 - The Linux partition (ext3) 
5 - A swap space of 2146Mb. 

For installing in step 4 i selected Manual from the three options. 
In step 5 i selected the Linux partition and clicked Edit and in 'Mount point' 
i put "/" and then selected this partion for formatting. Then i just did the rest of 
the installation with default options. 


Any idea what i've done wrong. I don't really know what i'm supposed to be doing when setting up partitions and i think perhaps i've got them in the wrong order or something.
By the way; i just put the Live CD in and went to the end of the installation-setup and the default location for the Grub to be installed is (hd0). Does this mean that it has been installed on the first of my partitions(which incidently only seems to load/boot when i hold a special key during start-up).

Thanks ......  

p.s. I've tried looking at similar posts first and the suggestions didn't work.

---

### Post by elliotjreed on 2007-12-18
[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

... is a great thread to start - it sorted out my GRUB problems!

---

### Post by Dodelijk on 2007-12-18
Hi, 

Thanks for the reply. 
Which one of the methods did you try? 

I can't do post one because i don't have an install Cd only the live one. 
For post two i tried typing "find /boot/grub/stage1" at the grub> prompt and i got
"Error 15: File not Found"

So then i figured from my description of my partition layout that my linux partition must me 
(hd0,3) so i typed "root (hd0,3)" and got "Selected disk does not exist"

---

### Post by rsambuca on 2007-12-18
Are you sure you completed the entire installation process?  If your grub 'find' command didn't find stage1, then you don't have grub loaded on your machine, which leads me to think the installation didn't finish.  Do you recall making an extended partition with two logical partitions inside of it, because you can't have more than 4 primary partitions on one hard drive, and you seem to think you have 5.

---

### Post by Dodelijk on 2007-12-18
Hi Thanks, 

Here's how my drive seems to be layed out: 
All on the same disk:

1 - Dell utility - FAT - Primary
2 - System - NTFS - Primary
3 - Extended - Primary
    3a - Work - Logical
    3b - Linux - Logical 
    3c Swap - Logical

So is this my problem? Basically when i made the Linux and swap partitions i took space from the work partition but i don't remember really making it extended. Is it because the donor partition was extended that these two became extended ? 

Should i wipe the Linux and Swap, make them primary and then re-install?

---

### Post by logos34 on 2007-12-18
> **Dodelijk said:**
> 
1 - Dell utility - FAT - Primary
2 - System - NTFS - Primary
3 - Extended - Primary
    3a - Work - Logical
    3b - Linux - Logical 
    3c Swap - Logical


root is (hd0,5), sda6

umm...if 'find' can't see stage1, then maybe rsambuca is right, install didn't finish or something.  You could try this though: reboot to hard drive and right after post hit Esc key--if grub appears we'll know at least it installed to the mbr.  (it could be 'hiddenmenu' is enabled or 'timeout' set to 0).  If not then there's a major problem and you should reinstall.

edit: normally ubuntu root doesn't need to be on a primary.  I've never had a problem with mine on logical partitions

---

### Post by Dodelijk on 2007-12-18
Hello, 

tried hitting Esc and it didn't work. I've just looked on the linux partition and i see that it's 100% used space(out of 10Gb) could this indicate that the installation went wrong somewhere? 

Would setting these partitions to Primary and installing do anything?

---

### Post by rsambuca on 2007-12-18
If your drive is like that, you should be fine.  What are you using to see these partitions?

---

### Post by Dodelijk on 2007-12-18
Partition magic from inside Windows. Which is where i did all the partitioning.

---

### Post by rsambuca on 2007-12-18
Load the [fs-drivers for Windows]("http://www.fs-driver.org/") and see what is on your linux partitions.  The fs-drivers allow full read/write to ext2/3 drives.

---

### Post by Dodelijk on 2007-12-18
Ok here' whit's in the linux partition: 
[IMG]http://img404.imageshack.us/my.php?image=sdsdsdsdsdsdzm2.png[/IMG]

---

### Post by Dodelijk on 2007-12-18
oops that didn't work. 

Basically there's a lot of folders(bin, boot etc) and 3 files. should i look for anything i particular?

---

### Post by rsambuca on 2007-12-18
Well, apparently something is installed!  Post your /boot/grub/menu.lst from your linux partition so we can see what is going on.

---

### Post by logos34 on 2007-12-18
> just looked on the linux partition and i see that it's **100% used space(out of 10Gb**) could this indicate that the installation went wrong somewhere?

that can't be correct.
> 
Partition magic from inside Windows. Which is where i did all the partitioning.

That's a red flag right there.  PM doesn't work well with linux. Another reason to reinstall. (it'll probably take less time than troubleshooting.)  I would use gparted on the live cd to delete the linux partitions and do 'guided' install on free space on the extended partition.

---

### Post by Dodelijk on 2007-12-18
/boot/grub/menu.lst - i don't even have a grub directory in /boot

> **logos34 said:**
> that can't be correct.


That's a red flag right there.  PM doesn't work well with linux. .

I only used PM to make the partition and was under the impression that the live CD did some formatting before the installation of files. I used PM rather than any other method becuase of the visual aspect. I really didn't want to wipe my other a partitions.

I think you're right about the saving time by reinstalling. I think it's time.

---

### Post by rsambuca on 2007-12-18
Yup, I would re-install at this point.

EDIT:  Make sure you check the md5sum of your iso and run the cd check prior to installing.

---

### Post by Dodelijk on 2007-12-18
Sorry, 

Just so i get this right. What's the 'md5sum' ?

---

### Post by rsambuca on 2007-12-18
It is a means of ensuring the file you downloaded is error free.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by alphaa1 on 2007-12-18
Try Easybcd option from windows for a change and see if you can boot into ubuntu... here is the link to try

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Dodelijk on 2007-12-18
Hello, 

Thank you all for the help. 


I've just reinstalled and all is working fine. 

YES!

---

