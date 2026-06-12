---
title: "I installed Ubuntu 6.10 but only Windows starts"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by Frankie82 on 2006-11-15
Hi everyone,

I tried installing Ubuntu 6.10 in a dual-boot configuration together with windows xp. Everything seems to go correctly but when I restart the pc no boot manager window appears and windows xp starts. Below is some more information on my system configuration and on the procedure I followed to install Ubuntu.

Before the installation:

hard disk 1

partition 1: windows 
partition 2: documents, etc
un-allocated space for linux

hard disk 2:
two partitions 

During the Ubuntu installation I created two partitions in the unallocated space of hard disk 1 (one partition for swap and one partition for the operating system) and I mounted them with the commands "swap" and "/". 

After this, a message appeared asking where I wanted to install GRUB and I left the default setting (If I remember correctly, it was "h0").

The installation proceeded without any errors to the end but when I restarted the pc, no boot manager window appeared and the system just started with Windows XP.

I am not an expert on linux installations, boot managers, etc... so I really don't know where to look to solve this problem.

I don't know if this can help but if I look at the structure of the  hard disk the two linux partitions appear in the "extented" area of the disk as logical partitions.

Thanks... sorry for the long post

---

### Post by bulldog on 2006-11-15
Did you try to boot from the second hard disk?
It seems to happen that GRUB installs on the wrong drive.

Give it a go,you can alter the boot order in your BIOS or by entering a button when you boot.

If there's no GRUB at all we can reinstall it from the live cd no problems with that.

---

### Post by Frankie82 on 2006-11-15
Hi,
thanks for the reply.

I cannot boot from the second disk because it is connected to a pci controller and so it is not detected in the bios. 

Do you know how to check if the GRUB was installed at all??
Or, if it was installed, how to check the settings??

---

### Post by lixy on 2006-11-15
It seems like it installed it on the wrong drive.

What I'd do if I were you is use the Edgy CD as a live-CD. Just tell it to install at the first prompt  but avoid clicking on the install icon when the desktop is loaded. Then, most likely it'll mount all the partitions which you can easily browse. Look for /boot/grub on the root partition of your fresh install. There's a file called menu.lst in there, which will answer the 1st part of your question. I'm not sure how to check where grub was installed though.

---

### Post by bulldog on 2006-11-15
Just reinstall GRUB on your first hdd again with the live cd.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next commands. 
```
root (hd?,?)
```
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

### Post by Frankie82 on 2006-11-15
I tried the procedure that you suggested. The location I get after executing the command 

find /boot/grub/stage1 

is hd(1,6). 

I then continued to follow the instruction and it seemed successful (I got no error messages), but when I restart the pc just windows keeps on loading.

Do you have any other suggestions? Thanks, I appreciate your help!

Frankie

---

### Post by Frankie82 on 2006-11-15
Bulldog, I think I find out where the problem is.

I started the Ubuntu installation and I reviewed how the hard disks are detected by ubuntu:

/dev/hde: IDE3 master (hde) - This is a PATA disk
/dev/sda:SCSI1(0,0,0)(sda) - This is a SATA disk and it is selected in the bios as the disk from which to boot

The first hard disk (hde) that is detected as master is not the hard disk on which I installed windows and linux. So I think that what happened is that when I installed GRUB on hd0 I actually installed it on the wrong disk.

Can the problem be solved by simply substituting, in your previous explanation, the line "setup (hd0)" with "setup (hd1)"?

By the way, do you have any idea why ubuntu detects my disks in the wrong order? 

Thanks again for your help!

---

### Post by bulldog on 2006-11-16
Yes you can install GRUB in hd1 with no problem.

It's a fact that Ubuntu can have some trouble when you use Sata and Pata disks.
Usual your first hdd is IDE and second Sata,but if you change the boot order in your BIOS you have two masters in fact because Sata disks are not set as master or slave anymore.

So GRUB can install on the wrong disk by mistake.

But I think you solved it,nice peace of work.

---

