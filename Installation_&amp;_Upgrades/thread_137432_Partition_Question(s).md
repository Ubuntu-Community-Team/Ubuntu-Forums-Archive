---
title: "Partition Question(s)"
date: 2006-02-27
forum: Installation &amp; Upgrades
---

### Post by ditane on 2006-02-27
Hey everyone. I am brand new to ubuntu and linux in general.  I have tried the live cd over the past few days, and from what I have seen, I really like it. I was getting ready to redo my computer anyway, so I figured I would actually install ubuntu and try it for a while. My problem is that I have to use Windows for some of the stuff I do (some of my classes REQUIRE it) Anyway here are my questions.  I read some of a guide that was very helpful in the way of partitioning and such, however, it didn't give any firm recommendations about stuff like partition sizes and the swap file. I have about 30-35GB to work with for both operating systems and all files and data, etc.  What I would like to do, would be to have an Ubuntu partition, a Windows partition, and a files partition for sharing stuff between them.  What would be the best way to go about that? I would like to try having a separate /home partition that I saw mentioned. Would Windows and Ubuntu be able to share this data, or should I do something else for that? Any recommendations on the partition sizes? What about the swap file size?

Thanks for any help anyone can offer

---

### Post by Bartender on 2006-02-28
HI, ditane -
If you're referring to the hermanzone guide, it didn't give firm recommendations because it's up to you.  If you're just experimenting with Ubuntu and need most of the drive for existing Windows projects (like video editing or some such) you might want to dedicate less to Ubuntu.  I've got a simple installation, just Ubuntu and Automatix and a few small files, and it's creeping up to about 4 or 5 GB if I remember correctly.  
As I understand it, the logic behind the separate /home partition is so you can nuke the Ubuntu partition and keep your personal data intact.  For example, this would be super for upgrading to Dapper in a few months.  I wish I'd done that but I was trying to keep it simple.

That /home partition would not be readable from Windows.

The swap file size?  There are many opinions.  I just let Ubuntu decide.

I've said this over & over, but if you can, get your PC set up next to one that's online so you can follow the hermanzone steps with minimal confusion.

---

### Post by Coelocanth on 2006-02-28
I can't really help you on the partition sizes - that's something you'll need to decide for yourself. Just consider what you need to have for each OS and divide accordingly.

As to the installation: make sure you put Windows on your first partition. It doesn't like not being number 1 and generally won't play nice if you don't. Ubuntu doesn't care where you put it.

The swap file; you can let the installation set it up automatically. Fom what I've been reading, the general view (if you're going to set it up yourself) is to go with 2 GB - your RAM. So, if you have 1 GB of RAM, then 1 GB swap is plenty. Others say to go with 1.5x your RAM. I ended up letting the install do it automatically... :lol: 

For sharing files between the 2 OSes, I recommend setting up a seperate FAT32 partition, as both OSes can read and write to that file system. Windows can't read the Linux file system and, while Ubuntu can read NTSF, there are some serious risks of data corruption if you try to write to it.

Home partition: some say it's a good idea to have a separate partition for your /Home, other's say it's not necessary. I tend to believe it isn't absolutely necessary, but it could be a good idea. If you *do* have it on its own partition, you can quite easily reintstall Ubuntu without losing your data. Something to consider.

---

### Post by adrenaline on 2006-02-28
I think Bartender meant 4 or 5 **GB**...

---

### Post by ditane on 2006-02-28
Thanks for the quick responses. Since it seems to be really up in the air, I'll take what you said as some general guidelines and play with it from there.

---

### Post by Bartender on 2006-02-28
Thanks, adrenaline -
Fixed that

---

### Post by jibril on 2006-02-28
Sorry guys, 

me just really new to all this, but how exactly do i partition my harddrive ... I honestly have no idea .... 

And how do i know which partition to install it on?

Thanks guys

jibril

---

### Post by Coelocanth on 2006-02-28
jibril, try Herman's [Dual Boot Guide](http://users.bigpond.net.au/hermanzone/)  (I'm assuming you want to set up a dual boot with Windows).

---

### Post by Bartender on 2006-02-28
jibril -
The hermanzone instructions really do walk you thru it.  I had zero knowledge when I followed his "Ubuntu+NTFS" guide a month or so ago.
Having said that, before proceeding:

BE PREPARED for calamity.  There are just too many things that can go wrong.

- Back up the data that you can't afford to lose.  I don't care if you have to b/up to floppies.  Don't stick that install CD in the tray unless you're ready to rebuild from scratch. 
- Find your original Windows CD or Recovery CD, make sure you have your 25-character key code.
- Do you have a stamped install CD or one you downloaded & burned?  If you can, verify the install CD's viability with an md5 utility.  (I haven't been able to come up with a straightforward method for Windows users yet)
- Defrag Windows just before proceeding with installing Linux.

---

### Post by arckeda on 2006-02-28
I suggest you use the stand alone gparted cd to partition your drives because sometimes you can partition you NTSF with teh live cd gparted or the boot one (trust me i tried) then youl have to shut down your computer during the partition (then youl be screwed)

---

### Post by jibril on 2006-03-01
I tried hermanzone guide and i got screwed :(.

I tried the shrinking part but it began shuffling around filesystems for so many partitions( i have two internal HDD's) that i didnt know which was which and aborted. Then i tried to run pre-installed XP but it said corupt file system even though i hadnt commited :(

After that i re-installed XP and made two partitions at the start. a 5GB and a 31 GB partition, with XP in the latter. 

I successfully installed XP and then started installing ubuntu in the other partition. It all installed well till i commited the changes. 

after all the installation and the headache, i was pretty happy on having two OS's, till GRUB refused to show XP anywhere. :(

I remember having seen the boot flag of ubuntu drive as on and that of XP as off when i had installed ubuntu in its partition. Would that have something to do with it? If yes, is there any way to fix it without re-installing all the things :(

I am now stuck with a linux system that i cant configure and a windows system i cant use'


HELP

jibril

---

### Post by munga_bill on 2006-03-01
If you can boot Ubuntu and get the output from the sudo fdsik -l command and the /boot/grub/menu.lst file and post them here someone may be able to help you.
```
sudo fdisk -l
```
```
sudo gedit /boot/grub/menu.lst
```

---

