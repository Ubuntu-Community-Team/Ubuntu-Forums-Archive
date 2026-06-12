---
title: "Dual Boot XP/Ubuntu 6.10, Clean Install Help"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by beeefyone on 2006-12-05
Hello, I am extremely GREEN when it comes to linux so please use general simple terms so I can understand. I have been working on putting together a dual boot machine for a while and have only been successful with extensive help from someone else using Slackware/XP. I am starting over and want to be able to do everything myself so that it is an easily repeatable process (I like to play and mess things up). 

My goal: To put together a dual boot machine running Win/Linux. To be able to complete the installs from a fresh drive, pre-partitioned. To be able to change distro's or versions or reinstall linux at any time (don't plan on leaving Ubuntu, seems like the best from my research, but just in case) without affecting Windows install, data or booting abilities. To be able to change windows versions (XP to Vista) or reinstall at any time without affecting Linux install, data, or booting abilities. I originally wanted to use the windows boot loader, but after my research it seems that GRUB is the way to go, it doesn't matter to me now, but I would like to have the option, As you can see I like to be flexible :). Optional consideration, to be able to add more bootable OS's with same abilities, by resizing partitions or pre-creating them now (only application I can think of now would be XP/Vista/Ubuntu/Kubuntu/Slackware multi-boot setup). Basically looking for dual-boot setup that is independent, expandable, and generic.

Old machine that worked (friend setup) had partitions setup like this (80GB HD, 768MB RAM):
Primary:  15? MB     FAT12    boot partition
Primary:  30GB       NTFS     Windows Root partition
Primary:  10GB       EXT3     Linux Root partition
Extended: 35GB
Logical:  1.5GB      SWAP     Linux Swap
Logical:  10GB       NTFS     Win-only Data
Logical:  23.5       FAT32    Win/Linux Share

My friend said that he had the same goal and this is how he did it.

I'm now trying to recreate this, drive is already formatted. I don't know if this is the best way but this is what I have. When I try to start recreating this I can't, because I can't format the boot drive in FAT12 using qtParted (during Ubuntu install). He used FDISK, but i'm not sure how to use that or if I need to go down that road if you guys think that is even the way to go.

I hope you understand my goal, if not, please ask for clarification. Once I get a working method I plan on cleaning up and compiling all the data and posting it where everyone can find it. Literally a step-by-step guide, because that is what I need. Hopefully by the end I will not only know what to do with your help but also why that decision is made over another. I can't wait until I can really dig-in-to Linux and become a real member of the community.

So how should I start? What should I use to create the partitions and how should I set them up?

Thank you in advance for all your help.

---

### Post by Sef on 2006-12-06
Read these to dual boot:

1) From the alternate cd, read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").

2) From the Live CD, read [Psychocats Installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by bulldog on 2006-12-06
After reading your goals,I should advice to buy a second hard disk.
So you can have windows on one drive and your other OS's on the other.

This way you can make windows and Linux independant  from each other.
You can install as many Os's on the second drive as you have space,and you can boot windows any time you want,with it's own boot loader,if something should go wrong with the Linux drive.

---

### Post by beeefyone on 2006-12-07
Sef,

Thank you for your advice, I have previously found these guides however they do not accomplish the goals that I have set forth, namely a separate boot partition and pre-setup of the HD partitions.

---

### Post by beeefyone on 2006-12-07
Hey Bulldog,

Thank you too for your reply. I understand what you are saying and would have to agree with you that that would be the best way, however for my learning, I would like to accomplish this with one HD. I do have a spare but that is one that I am going to use to play with and probably really screw up.

---

### Post by beeefyone on 2006-12-07
How about this, I guess I should start with the basics...

How do I setup a separate boot partition? What file system whould it have to be usable by windows and Linux, and what software should I use to create the boot partition. Does it have to be set to active? Will Ubuntu mount it as /boot when I do the install or do I need to move the first 512 bytes to it after install and then mount it as boot? I know I'm probably sounding garbled and maybe totally wrong but I am trying to make sense of information that I have found out there.

Where I'm at now...

I used CFDISK to create the partition table (set FAT12 part. to bootable), then I tried to install, Ubuntu did not recognize the file systems. I then figured out that these partitions needed to be "formated" or "file systems" needed to be created on the drive. I tried to use the mkfs command (not sure if this is correct) to create the file systems in the partitions as I laid them out above. I created one 16MB FAT12 FS, then tried creating the NTFS FS on the 20GB part, and then tried creating the 10GB EXT3 FS.

Once I had these FS's created using mkfs command, I decided to check if Ubuntu was recognizing the FS's yet, when gparted came up it said that my NTFS partition was like 50% full? I didn't put any files on it or install to it at this point, why is this?

The other problem, since I am a novice...
I created the partition sizes in CFDISK using standard MB notation.

Now when I try to create the FS's , it wants another notation, I think in KB? When I tried to create the FAT12 at straight 16000 (in mskfs command) it told me that there was a size mismatch and it should be 160883, so I changed it and it worked. I did not get that same warning when I tried to create the NTFS or EXT3 FS's. I just used 20000000 and 10000000 respectively. Did I do this properly?

Also, I said that I don't mind using GRUB, I don't but I read in another post that using GRUB instead of the NTLDR may cause issues with anti-virus programs, is this tru?

Am I going to have to use the Alternate CD for this, so that I can tell it where to put GRUB? Should it go in the MBR? Is there an MBR before Windows is installed.

Am I on the right track?

Thanks again!

---

