---
title: "Can some one Guide me to install Ubuntu 11.04 with Windows 7"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by azkraja on 2011-05-31
Hi  All,

I am new to Ubuntu, i have tested this software 6 month back Ubuntu 10.10 version, dual boot with Windows 7. I liked this OS, however for a Windows user its looks difficult initially, i know after spending some time and learning with this OS, it will be easier day by day. I want to install its 11.4 version in my another Laptop, but afraid to loose the data as i encountered this happening just a week before with my friends Machine. I have three partition in my Laptop, C has Windows 7 (70GB) than D Partition has 70 GB Space and E partition has 160 GB space, I need step by step guidelines to Install 11.04 in my Drive "E" Where i can make another Partition for Ubuntu using Windows 7 Shrink Volume utility. I need installation guide from experts to not loosing data as i do not have any other portable hard drive to take back up.
Please Guide me what will the best for me, if i have Total 80 GB (Allocated Drive) space for Ubuntu, i.e /root, / Home, Swap (I have 2GB RAM) etc , Waiting for some Expert guidelines.

---

### Post by baarn on 2011-05-31
i am not an expert, but i can tell you that there are many idiot-proof tutorials out there, describing how to dualboot a computer with linux and windows.

one like this for example
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
i doubt you will get spoon-fed here, but if you have questions or are unsure about certain things, just ask.

about partitioning:
you should actually have 2 windows partitions one is the hidden windows-boot partition (about 100MB) the other one shows as C:
so you should have 4 partitions on your drive. primary drives are either called hda or sda, second would end in b next in c etc. the number of the partition is appended, starting by 1.
assuming that all partitions on that computer are primary partitions, so your hidden windows boot partition is sda1, C is sda2, D sda3. and E is sda4
because you want to install ubuntu to E aka sda4 it would be best to trash this partition and make a logical out of it.

you only can have 4 primary partitions on your computer, but you can extend those partitions to serve as something like a layer around further partitions, called logical partitions.
the first logical partition you create inside an extended partition will be called sda5 no mater how many primary / extended partitions are in use.
inside this extended partition you can afterwards create as many logical partitions as you want.

i hope you understood something what i was trying to say, the partitioning tool used by the graphical installation progress should clear things up.

there is one thing i am not sure about... i often heard that there might be problems when /boot is not a primary partition, as i assumed, all primary partitions should be blocked right now, maybe you have to convert your D: partition to a logical one aswell...

i hope this helps

edit: there is a linux distribution called gparted, its mainly for partitioning purposes, you should use that in favor of the windows utility, i know that the windows thingy works fine for windows things, but its not the right thing to use for linux things i think :P

---

### Post by dadaj on 2011-05-31
You may follow the step of partition rebuilding from this link...

[http://jeffond756.xanga.com/746995183/dual-boot-windows-7-and-ubuntu/](http://jeffond756.xanga.com/746995183/dual-boot-windows-7-and-ubuntu/)

the discussion about the partition rebuilding :

[http://ubuntuforums.org/showthread.php?t=1744660](http://ubuntuforums.org/showthread.php?t=1744660)

---

### Post by azkraja on 2011-05-31
Many thanks, i will go through all these information, before start installation, following are existing partitions in my Laptop. Should i create one more partition in Drive E (sda4) for Ubuntu, as i do not want to use all space for Ubuntu.

---

### Post by Quackers on 2011-05-31
Definitely NOT!
You already have 4 primary partitions. This is the maximum number available on a mbr partitioned disc. If you try to create another partition you will cause severe problems!
If you want to install Ubuntu in your E: drive (as Windows calls it) you must first delete that partition from the Windows disk Management screen (along with any data in it!).
Then in the resulting unallocated space Ubuntu can be installed.

---

### Post by azkraja on 2011-05-31
> **Quackers said:**
> Definitely NOT!
You already have 4 primary partitions. This is the maximum number available on a mbr partitioned disc. If you try to create another partition you will cause severe problems!
If you want to install Ubuntu in your E: drive (as Windows calls it) you must first delete that partition from the Windows disk Management screen (along with any data in it!).
Then in the resulting unallocated space Ubuntu can be installed.


Many Thanks for your help. I have read this excellent thread and it gives me lot of information's regarding partitions. 

[http://ubuntuforums.org/showthread.php?t=1744660&page=3](http://ubuntuforums.org/showthread.php?t=1744660&page=3)

Many thanks

---

### Post by Quackers on 2011-05-31
Reading is good :-)
Basically, for safety sake, you must at no time exceed 4 primary partitions, one of which (and only one) can be an extended partition.
It is always a good idea to have backups of anything you wouldn't want to lose, if anything went wrong.
I use clonezilla to make a full backup of all partitions on any hard drive I am about to "play with". It is comforting to know that you can always go back to it.
Clonezilla backs up both Windows partitions and Linux partitions and will restore both.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by baarn on 2011-05-31
it should not even be possible to create more than 4 primary partitions. i don't know any tool that would let you do so ;)
whats up with the first partition (the fat32 one)? what is the use of it?

it would really be better to see how your drive looks like in gparted or with fdisk...
especially because you have more stuff on E: than you have free space on C: and D:

i would do (from what i can see on your partition table)
- find out, what the first partition is about and delete it if unused ...maybe its a recovery partition, i would delete it anyway, but thats just what i would do as i said...
- extend the second partion C: to the beginning of the drive (giving it the space of the just deleted partition) (this might break the windows bootloader, maybe put the linux /boot partition in front, it just needs around 100MB)
- copy all the stuff from D: to E:
- delete D:
- extend C: so it can hold all the stuff in E:
- copy stuff from E: to C:
- delete E:

afterwards you have just one partition C: holding all stuff from the drives D: and E:
there is only one of the primary partitions used... (or two if you created /boot in front)

a small warning, if you have any programs on D or E they might not work correctly afterwards, because of breakage in the registry (which still points to D or E).
but if you later create other logical NTFS or FAT partitions they will be assigned letters following C: 
so you could just create two logical partitions the first one would be D: the second one would be E: and copy stuff back there, voila linkage in registry is still usable. :)

and be sure that you copy all hidden and system files from D: and E: (that should be easier using a live-cd too, because you cannot copy some system files, or files that are used under windows...)
but with a live-cd you have to assure that the flags are preserved...
so the command should be something like
```

cp -Rfp /origin_dir/* /targetdir/

```i am not sure though... i make a shitload of errors myself when copying files ;)

but there shouldn't be any problems if you dont have any programs or other system stuff on those drives, in that case you can just copy all folders n files except the recycler and systemsrecovery folder (not sure what the name is)

good luck ;)

---

### Post by Quackers on 2011-05-31
baarn, please don't rely on being stopped from creating a fifth primary partition - it is all too easy to do - but don't try it!

---

### Post by baarn on 2011-05-31
you are right, it always better to know what your doing than to rely on a programs warnings
anyway... I'd love to know how that would be possible... maybe just to know when to be careful, maybe to try it out (have some old HDs here).

---

### Post by Quackers on 2011-05-31
Windows will do it, but in Vista or 7 it will give you a warning about changing simple volumes to dynamic disks.
There have been many posts on here regarding this issue and a whole variety of partition editors have been involved - allegedly :-)

---

### Post by dadaj on 2011-06-01
> **azkraja said:**
> Many thanks, i will go through all these information, before start installation, following are existing partitions in my Laptop. Should i create one more partition in Drive E (sda4) for Ubuntu, as i do not want to use all space for Ubuntu.

[http://ubuntuforums.org/showpost.php?p=10755147&postcount=24](http://ubuntuforums.org/showpost.php?p=10755147&postcount=24)

 Hi azkraja,   I also a newbie of Ubuntu. please, verify my advise before any action. If you want to create separated partitions for Ubuntu, you can follow the thread I post. I created three partitions for root, home and swap. you should ignore the first step of conversion dynamic to basic.    let me know what of the partitions you have created by typing the command of LIVE CD in terminal window: ```
sudo parted --list  
```

---

### Post by azkraja on 2011-06-01
Thank you all for your valuable guidance, due to time difference i could not reply you on time, i will go for Ubuntu according to your guidelines, i am very happy to get timely support from this excellent forum, which makes different from others. 
I will keep posting if anythings goes wrong during installation.

LOL

---

### Post by baarn on 2011-06-01
Uh yeah just to mention it (it has to be mentioned)
you really should consider backing up files atleast on an external drive or something like that.

this would not just come in handy in a situation like this, but especially when you experience a harddrive crash. there are of course tools like s.m.a.r.t. which displays the expected lifetime of your drive. but i have a 500gb harddrive here besides me, that was fit the one day an another day it only klicke-de-klacked with its heads and was practically dead... and i didn't back it up properly...
no data of value was lost in that case, because i actually had some stuff copied to my laptop that time to work with it while being mobile and the private stuff (photos mostly) were all copied from the girlfriend i had that time. but as i said that was no real backup, it was just pure luck, that i had the valuable stuff elsewhere...
i still lost a shitload of music, films and games.

you maybe think its annoying to back up your drives and to take care of your files and data, but trust me how much more annoying it will be if you lose private memories like photos, videos or other stuff that cannot be recovered.

---

### Post by azkraja on 2011-06-02
> **baarn said:**
> Uh yeah just to mention it (it has to be mentioned)
you really should consider backing up files atleast on an external drive or something like that.

this would not just come in handy in a situation like this, but especially when you experience a harddrive crash. there are of course tools like s.m.a.r.t. which displays the expected lifetime of your drive. but i have a 500gb harddrive here besides me, that was fit the one day an another day it only klicke-de-klacked with its heads and was practically dead... and i didn't back it up properly...
no data of value was lost in that case, because i actually had some stuff copied to my laptop that time to work with it while being mobile and the private stuff (photos mostly) were all copied from the girlfriend i had that time. but as i said that was no real backup, it was just pure luck, that i had the valuable stuff elsewhere...
i still lost a shitload of music, films and games.

you maybe think its annoying to back up your drives and to take care of your files and data, but trust me how much more annoying it will be if you lose private memories like photos, videos or other stuff that cannot be recovered.


You are right, I have planed to purchase a portable HDD first to back up all my valuable memories (Especially Photos and e-books, and lots of my assignments). Because i have done this with my cousin before during installation. Thanks for your guidance, otherwise the way i planed to installed Ubuntu was totally wrong (after reading all of you). thanks for saving me.

---

