---
title: "installing Ubuntu 10.10 on Windows 7 pro 32-bit (w/ dual boot)"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by Sari.S on 2010-11-19
Hello guys,

I would like to install the new, improved, and great looking Ubuntu 10.10 from inside (or outside) Windows 7 professional 32-bit but I'm not sure if using that little thing called "Wubi" is better than downloading the OS and burning it into a CD and booting the laptop with a "clean install" is a much better idea? I don't want to install it incorrectly.

I have a free 6 GB E:\ partition for Ubuntu (is it enough?) and I want to boot up my laptop with both OS in the menu.

Please, I need your help and Thank y'all in advance :)


Regards,
Sari.S

---

### Post by tommcd on 2010-11-19
Your 6GB partition will be enough to try Ubuntu. A full Ubuntu install takes up about 3.5-4GB. The only thing is that you will not have much free space in your home directory for storing files and data. However, if you only want to try out Ubuntu, the 6GB partition will suffice.
Installing Ubuntu to a dedicated linux partition is infinitely better than trying to run Ubuntu inside Windows using Wubi. Do a real Ubuntu install instead of using Wubi!
You can easily see what Ubuntu is like just by booting from and running the Ubuntu live CD. This will enable you to check out Ubuntu running "live" without making any changes to your computer.
Note that the live CD will run a bit slower than a Ubuntu installed to the hard drive, since CDROM access is slower than hard drive access.
Here is a great site for getting started with Ubuntu:[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And for dual booting Windows with Ubuntu: [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Write back if you need more help.

---

### Post by Sari.S on 2010-11-20
Thanks for your answer. I'll try to install it (after trying it) and if I need some assistance I'll come back. :)

---

### Post by Sari.S on 2010-11-22
Ok I tried it last night and I kinda like it so I wanna install it from the CD (from boot) but whats the option to install it on my other partation? because one of the options is "install along side windows". Does that mean it will be installed on C:/system partation and can't be removed? I forgot about the 2 or 3 options but nothing in that menu had the option "install on new partition"

---

### Post by tommcd on 2010-11-22
> **Sari.S said:**
>   I wanna install it from the CD (from boot) but whats the option to install it on my other partation? 
If you choose manual partitioning, then you can select the 6GB partition. Then choose to either format that partition and install Ubuntu there, or delete that partition and then create a root and swap partition in the newly created free space.

---

### Post by Sari.S on 2010-11-24
> **tommcd said:**
> If you choose manual partitioning, then you can select the 6GB partition. Then choose to either format that partition and install Ubuntu there, or delete that partition and then create a root and swap partition in the newly created free space.

Thanks for your answer, tommcd. I really appreciate it :)

Please, bear with me once again :D

Okay my E:\ is now empty and I'm ready to install Ubuntu with the manual partitioning option but which one is better? formatting the partition (again) and then installing Ubuntu OR "delete that partition and then create a root and swap partition in the newly created free space." ? 
Because I don't get the 2nd (kinda complicated) option! ;)

FYI:

1) Windows 7 is on C:/ and I don't wanna mess with it :)
2) I want to be able to delete (uninstall or re-install) Ubunut from E:\ whenever I want :)
3) whenever I start (and boot) my laptop, I want to the OS selector menu with both OS's to appear with Win 7 the default OS.

Thanks once again :)

Sari.S

---

### Post by Quackers on 2010-11-24
My own personal preference is to delete the partition and leave the resulting unallocated free space for Ubuntu to install into.
Then during the installation select the manual partitioning option and set up your new Ubuntu partitions there.
If everything goes according to plan you will get the grub menu which will make Ubuntu the default operating system with Windows as an option. This can be changed later quite easily.
Any further questions just ask. It is better to ask than to make mistakes :-)

---

### Post by tommcd on 2010-11-24
> **Sari.S said:**
> 
Okay my E:\ is now empty and I'm ready to install Ubuntu with the manual partitioning option but which one is better? formatting the partition (again) and then installing Ubuntu OR "delete that partition and then create a root and swap partition in the newly created free space." ? 

I would probably just delete the partition; but I don't think it really matters whether you delete the partition or simply choose to format the partition and install Ubuntu there. 
In either case, you will create 2 partitions in the 6GB space. You need a root partition and a swap partition. If you have a good amount of memory, the swap partition can be 500MB. Use the rest of the space for the root partition.
Write back if you need more help.

---

### Post by Sari.S on 2010-11-25
Thank you guys for your replies!


To tommcd: Ok after deleting the partition, How can I do this on E: ? > "In either case, you will create 2 partitions in the 6GB space. You need a root partition and a swap partition. If you have a good amount of memory, the swap partition can be 500MB. Use the rest of the space for the root partition."

and I do have a good amount of memory :)

Thanks :)

---

### Post by Mark Phelps on 2010-11-25
BEFORE you do anything more on this setup, go into the Backup feature on Win7 and use it to create and burn a Win7 Repair CD.  That will come in useful later should you need to repair the Win7 boot loader from your dual boot setup.

---

### Post by Quackers on 2010-11-25
> **Mark Phelps said:**
> BEFORE you do anything more on this setup, go into the Backup feature on Win7 and use it to create and burn a Win7 Repair CD.  That will come in useful later should you need to repair the Win7 boot loader from your dual boot setup.

Does that make a repair cd or a set of recovery discs? I would appreciate more details if it can make a repair cd. Is this facility version specific? I have W7 Ultimate and I haven't spotted it :confused:

---

### Post by tommcd on 2010-11-26
> **Sari.S said:**
> 
To tommcd: Ok after deleting the partition, How can I do this on E: ? > "In either case, you will create 2 partitions in the 6GB space. ...
When you get to the partitioning part of the Ubutnu install choose manual partitioning. Then choose to delete the 6GB "E" partition. This will leave 6GB unallocated space.
Then choose to create a new logical partition. Choose mount point / (for root). Then choose to use it as the ext4 file system (This will be the default anyway). Then set the size to be 5.5GB.
Then set the remaining 500MB as the swap partition. Then click "*done with partitioning, continue with setup"*" (or whatever it says exactly) and continue with the install.
Here is a good tutorial on manual partitioning. It shows how to partition the hard drive to create a separate root and home partition. This is the ideal partitioning scheme. However, since you only have 6GB, you really don't have enough space for a separate home partition.
Note that you could choose to go without a swap partition if you have at least 1-2GB of memory, as it says in this tutorial:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
FYI: The swap partition is analogous to "virtual memory" in Windows. It is hard drive space that is reserved to swap programs out of memory to the hard drive if you use up all of your memory. I have 2GB memory, and I hardly ever touch my swap partition.

---

### Post by Sari.S on 2010-11-26
> **Mark Phelps said:**
> BEFORE you do anything more on this setup, go into the Backup feature on Win7 and use it to create and burn a Win7 Repair CD.  That will come in useful later should you need to repair the Win7 boot loader from your dual boot setup.

THANK YOU SO MUCH for reminding me because it happened to me before but it took me so much to recover Windows 7 and I almost killed myself for that!

> **Quackers said:**
> Does that make a repair cd or a set of recovery discs? I would appreciate more details if it can make a repair cd. Is this facility version specific? I have W7 Ultimate and I haven't spotted it :confused:

here you go :)
[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html]("http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html")

> **tommcd said:**
> When you get to the partitioning part of the Ubutnu install choose manual partitioning. Then choose to delete the 6GB "E" partition. This will leave 6GB unallocated space.
Then choose to create a new logical partition. Choose mount point / (for root). Then choose to use it as the ext4 file system (This will be the default anyway). Then set the size to be 5.5GB.
Then set the remaining 500MB as the swap partition. Then click "*done with partitioning, continue with setup"*" (or whatever it says exactly) and continue with the install.
Here is a good tutorial on manual partitioning. It shows how to partition the hard drive to create a separate root and home partition. This is the ideal partitioning scheme. However, since you only have 6GB, you really don't have enough space for a separate home partition.
Note that you could choose to go without a swap partition if you have at least 1-2GB of memory, as it says in this tutorial:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
FYI: The swap partition is analogous to "virtual memory" in Windows. It is hard drive space that is reserved to swap programs out of memory to the hard drive if you use up all of your memory. I have 2GB memory, and I hardly ever touch my swap partition.

Thanks for all the links, help, and step-by-step's. :)

I will try to remember all what you've mentioned during the installation process. ;)

---

### Post by dino99 on 2010-11-26
make a real install (outside winblows), so resize the partition(s) to make room

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Utkarsh Ray on 2010-11-26
I use Windows 7 Ultimate x64. It seems that the recovery disc (only one cd needed) created is version and architecture (32 and 64 bit) specific. Because my recovery disc didn't work on the enterprise version trial installed on virtual pc

---

### Post by Sari.S on 2010-11-26
Hello once again :)

It is really complicated to install this OS! I'm in Ubuntu right now (trying it Again!) and I'll show you guys what I see :)

Before I do that, I want y'all to know that My HDD is 500GB and all my partitions are almost full with filesand my computer consist of 4 partitions!
I have *C:* (with my default OS on it) and  two other partitions (D) and (I) in addition to the (E) empty drive  in which I want to install Ubunut on. 

Oh yeah.. another thing, I have this (Q) not accessible drive (or call it partition) that I can't delete nor format!

screen #1
[[IMG]http://img197.imageshack.us/img197/7119/screenshotfq.th.png[/IMG]]("http://img197.imageshack.us/i/screenshotfq.png/")

screen #2  after going to option #3 (**Specify partition manually (advanced)**)
[[IMG]http://img251.imageshack.us/img251/3697/screenshot1ag.th.png[/IMG]]("http://img251.imageshack.us/i/screenshot1ag.png/")

but I don't know how to proceed and if its better to select option #1 
(**Install alongside other operating systems**)

if I select this option #1 I see the screen below
[[IMG]http://img337.imageshack.us/img337/8593/screenshot2mw.th.png[/IMG]]("http://img337.imageshack.us/i/screenshot2mw.png/")

and I know option #2 will delete the entire disc (or HDD) and remove my windows and I certainly don't wish to do that!

Thanks!

---

### Post by Quackers on 2010-11-26
As a check before you install boot from the Likve cd by selecting "try ubuntu" and when the desktop loads connect to the internet. Then please go to the site below and download the boot script to the DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tommcd on 2010-11-27
> **Sari.S said:**
> 
I have *C:* (with my default OS on it) and  two other partitions (D) and (I) in addition to the (E) empty drive  in which I want to install Ubunut on. 
Oh yeah.. another thing, I have this (Q) not accessible drive (or call it partition) that I can't delete nor format!

Rather than posting those screen shots, boot from the Ubuntu live CD and open a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -l
```
This will list all of your partitions that Ubuntu sees. The boot-info script that Quackers mentioned will also list your partitions.
That Q partition may be a hidden recovery partition or something.
So just choose to delete the 6GB E partition. Then make a logical partition for Ubuntu's root partition in the newly created free space. And (optional) create a 250MB-500-MB swap prtition.

---

