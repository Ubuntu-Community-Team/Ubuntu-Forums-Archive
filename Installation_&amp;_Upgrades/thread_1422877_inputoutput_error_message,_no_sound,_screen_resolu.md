---
title: "input/output error message, no sound, screen resolution"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Jessica39 on 2010-03-05
Hi
I cant seem to install Ubuntu 9.10 at all. At 15% I get the following Error Message
Input/output Error During Read On/dev/sda  then I get   the creation of swapspace in partition #5 of SCSI1(0,0,0) (SDA) Failed.    Ive tried 6 times already.

Im getting no sound at all.  

How can I change the screen resolution.  800 x 600 is the highest it will go.

Im getting really discouraged with Ubuntu.  Alot of people seem to have the same problems I am having but there is no solutions.

I've checked the MEMTEST and passed, done a disk check and passed. 

ANY help is appreciated.
Jessica

---

### Post by mikewhatever on 2010-03-06
> **Jessica39 said:**
> Hi
I cant seem to install Ubuntu 9.10 at all. At 15% I get the following Error Message
Input/output Error During Read On/dev/sda  then I get   the creation of swapspace in partition #5 of SCSI1(0,0,0) (SDA) Failed.    Ive tried 6 times already.

Can you boot the installation cd, open System->Admin->Gparted and post a screenshot. Alternatively, Applications->Accessories->Terminal, and post the output of 'sudo fdisk -l' without the quotes.

> Im getting no sound at all.  

How can I change the screen resolution.  800 x 600 is the highest it will go.

Im getting really discouraged with Ubuntu.  Alot of people seem to have the same problems I am having but there is no solutions.

I've checked the MEMTEST and passed, done a disk check and passed. 

ANY help is appreciated.
Jessica

Sound and graphics are difficult to troubleshoot without knowing anything about the hardware. Sometimes, there is a simple fix, installing updates or loading a driver. I don't know if many have problems or not, but there are solutions.

---

### Post by Jessica39 on 2010-03-06
System->Admin->Gparted---No devices Found is what I get for that one



Applications->Accessories->Terminal, and post the output of 'sudo fdisk -l' without the quotes.   Nothing happened when I put the  sudo fdisk -l  without quotes.

---

### Post by mikewhatever on 2010-03-06
That's an odd issue. Having searched around, I also found other posts of similar nature with no definite explanation or solution.
I'd try launching the installer program again and select manual partitioning. Can you see disk partitions there? What else is on that hdd,? Windows? Important files? Do you know anything about the hardware (CPU, RAM, etc)?

Edit: Here is a possible solution.
[http://ubuntuforums.org/showpost.php?p=6508477&postcount=8](http://ubuntuforums.org/showpost.php?p=6508477&postcount=8)

---

### Post by Jessica39 on 2010-03-06
hi Mikewhatever
im getting sound now yayayya after downloading the Adobe Flash Player.

the HDD I bought used. It had been wiped with Linux.  I bought the same drive that I had listed below.  There is nothing on the drive. 
My computer itself is a HP M8200n Athlon 64x2, Chipset GeForce 6150SE nForce 430, 3gb Memory with a capacity for 8gb,  HDD Seagate 500gb SATA 3G 7200 RPM, Sound/ Audio High definition 8-channel audio ALC 888S Chipset.  More at the following link about what kind of computer and what it has at the following link. 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01151028&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=3548185](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01151028&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=3548185)

Im wanting to put Ubuntu on the whole disk drive.  The Manual Partition I havent done only because im not exactly sure what i'm doing and how to partition it the right way.  Its my understanding if you mess up in partioning you can change it back.     

Im fixing to try the last link in the link you posted in your last reply and see if that works.  

thanks mikewhatever

---

### Post by mikewhatever on 2010-03-06
That's great, both that you got sound working and that there is nothing on the hdd. This way, you don't have to worry about accidentally deleting something while messing with partitions. Manual partitioning is a bit intimidating, but doable, if that's what works.

---

### Post by Jessica39 on 2010-03-06
im going to try the manual partition.  your advice on what to do.  Keep in mind im wanting the Ubuntu to be on the whole disk. 
In CREATE A NEW PARTITION (note not yelling when typing in caps just showing you the title) New Partition Size in Megabytes: 500105   1.)  What do I put the New Partition Size too.   Location for the New Partition  2.)  Beginning or End   which do I pick
3.)  What do I choose from the following :   EXT3 Journaling File System,  EXT2 File System,  ReiserFS  Journaling File System,  JFS journaling File System, XFS journaling file system, FAT16 File System, FAT32 File System, Swap Area, Do Not Use this Partition.

Also the MOUNT POINT:  What do I choose?  / ,  /boot , /home , /tmp , /usr,  /var , /srv  , /opt  , /usr  , /local 


thanks again

---

### Post by mikewhatever on 2010-03-06
Right, sorry for the delay.

Let's create three partitions, root, home and swap, classic setup, so to speak. All starting from the beginning, although it doesn't matter.

1. root - the system partition:
size - 20000
file system - ext4
mount point - /

2. home - for personal files and settings:
suze - 478000
file system -ext4
mount point - /home

3. swap:
size - the rest of the unallocated space - about 2GB
file system - swap

I take it the solution you tried earlier didn't quite work, did it?

---

### Post by Jessica39 on 2010-03-06
Hi Mike
Nothing I try seems to work.  
sorry I didnt specify when you asked  I take it the solution you tried earlier didn't quite work, did it?   Naw it didnt work.

I did the Following and it didnt work.  this time it gave me this error message:   The Creation of Swap Space in Partition #6 of SCSI1 (0,0,0) (SDA) Failed
1. root - the system partition:
size - 20000
file system - ext4
mount point - /

2. home - for personal files and settings:
suze - 478000
file system -ext4
mount point - /home

3. swap:
size - the rest of the unallocated space - about 2GB
file system - swap

Im attaching a screenshot of the Partitioning Box so you can get an idea of what I did.
Any suggestions as to what to do now.

---

### Post by mikewhatever on 2010-03-06
This is an odd problem, but I believe we will find a solution. Meanwhile, try installing without creating the swap. Given the 3GB of RAM you have, swap will be barely needed anyway.

---

### Post by Jessica39 on 2010-03-06
that didnt work either I got this error:
The ext4 file system creation in partition #1 of SCSI1 (0,0,0) (SDA) Failed

---

### Post by mikewhatever on 2010-03-06
Very interesting. It looks like no matter what, neither the installer nor Gparted would create partitions. And yes, quite a few people reported a similar problem with no definite solution. Perhaps you could try Gparted live cd [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/). It's the same partitioning program, but the underlying system is Gentoo. 
Try checking the connection cabled are firmly attached, and if there is more then one socket, try switching to another.
It would also not hurt to run some test of the hdd to exclude the possibility of it being faulty.

---

### Post by Jessica39 on 2010-03-06
I did test on the hdd and it is fine.  Im going to try the Gparted program and if that doesnt work I am going to get another version Ubuntu.  I have tried a total of 9 times to install the 9.10 and as you see nothing works.  
I do so appreciate your help and ideas.

---

### Post by mikewhatever on 2010-03-06
Another version of Ubuntu or another distro altogether, Mandriva, Open suse, would be worth trying. I'd also take a look at Seagate's diagnostic software.
[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

> SeaTools for DOS
 

SeaTools for DOS tests SATA or ATA drives from a bootable CD-ROM or floppy. It can test a SATA (Serial ATA) or older ATA (PATA/IDE) interface hard drive. Because the software boots to its own operating system you can test your drive regardless of the OS installed on it. You can even test a new or completely blank drive. In addition, this version offers limited repair and data erasure.

---

### Post by mikewhatever on 2010-03-12
I've just read a thread with what seems to be a similar problem. It was suggested that the sata hdd wasn't detected because it had been used in a raid.
[http://ubuntuforums.org/showthread.php?t=1427082](http://ubuntuforums.org/showthread.php?t=1427082)

---

