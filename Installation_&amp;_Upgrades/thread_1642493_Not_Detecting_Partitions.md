---
title: "Not Detecting Partitions"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by bitsonhj on 2010-12-10
helle guys.am newbie here.So hello

ok. I have just got a ubuntu CD 10.10. So after normal process of changing boot(from CD), i chose "install" NOT "try" . Then came a page where it says you have enough space on your hard-disk (2.6gb free) and that you are connected to internet. Then when i click on 'forward' to go to the next step ,i get an error :> 

" Error fsyncing/closing/dev/sda = Input/output error "
Then i was able to choose between "Retry" and "ignore"(in the error box)

when i click "retry" ,i get the same error .Then when i click "Ignore",then advance...,i can't see my partitions which i have.There are only two , C & D. The partition were no where to be seen!!!

Anyway,i wanted to install ubuntu on D,bcuz my win 7 is install on C.just give me a brief explantion how i be able to see my partition in the installation process of ubuntu.If you think its a faulty error from my hard-disk,then let me know how to fix it.

[COLOR=Red]ok guys,Thanks in Advance for Replying[/COLOR]


My system configuration(acer extensa 5220) :
Intel Celeron @ 2.00Ghz,533 MHz FSB ,1MB L2 cache
356 Mb Mobile Intel graphic
2GB DDR2 Ram
Hitachi 80GB                                              (bought two years back)

Plz note that in "try" mode,everything went normal.

---

### Post by tommcd on 2010-12-10
> **bitsonhj said:**
> Then came a page where it says you have enough space on your hard-disk (2.6gb free) and that you are connected to internet. Then when i click on 'forward' to go to the next step ,i get an error 
" Error fsyncing/closing/dev/sda = Input/output error " 

The first thing you should do is run the option on the Ubuntu live CD to check the CD for defects:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
This takes a minute or two to run. If the check passes without errors then the CD is good.
Assuming the CD passes the check without errors, then from the Ubuntu live CD open a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -l
```
This will list the partitions that Ubuntu sees.
Also, a 2.6GB partition is a bit small. My Lubuntu install is currently using 2.6GB space, and I have not added very much stuff. A full Ubuntu install will likely be a bit larger. Ideally you should create a larger partition to install Ubuntu. The partition manager on the live CD can do this.

And welcome to the Ubuntu forums!

---

### Post by Quackers on 2010-12-10
Welcome to UF.
I would do a couple of things first.
I would check the MD5sum of the downloaded .iso file
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If that is ok, I would check the integrity of the cd. At the purple splash screen press F6 and choose to check the disc for errors.

At this point it might be a good idea (as a safeguard) to post a screenshot of your Windows Disk Management Console screen (Start > right-click Computer and select Manage > then on the left of the new screen select disk management).

---

### Post by bitsonhj on 2010-12-11
[COLOR=Red]**to tommcd :**[/COLOR]

i ran the cd check when ubuntu boot up(by pressing F6).and ubuntu said that there was NO error on the cd.
for the thing on the terminal i got that :
[IMG]http://i277.photobucket.com/albums/kk47/bitsonhj/Screenshot.png[/IMG]




so nothing happened .And for the 2.6gb,its ubuntu who was confirming me that there was enough space on my harddisk.its not that my hard-disk is just a little more that 2.6GB.

Don't forget,i told you ubuntu was not detecting my already made partition.

[COLOR=Red]**TO QUACKERS**[/COLOR] 

FOR THE md5sum ,check the image above .
and here is my disk manager on windows 7:
[IMG]http://i277.photobucket.com/albums/kk47/bitsonhj/diskmanagement.jpg[/IMG]



[SIZE=4][I]Thank you very much both for replying.Hope to continue to hear from you and others!;)
[/I][/SIZE]

---

### Post by Quackers on 2010-12-11
There is no free space on your hard drive for Ubuntu to install into.
You can't install into D: because it is formatted in NTFS. Ubuntu uses ext4 by default now.
As there is plenty of free space within D: I would boot Windows and shrink the D: partition using Windows Disk Management console. This will leave some unallocated space which Ubuntu can use.

---

### Post by bitsonhj on 2010-12-11
ye thanks for replying,but is not working either.

don't forget the error message in the first post.i am having the same error message(see first post) after making some unallocated space in the 'D' partition.
that the new disk management pic :
[IMG]http://i277.photobucket.com/albums/kk47/bitsonhj/desktop.jpg[/IMG]

YOU SEE, even if there is some unallocated space,ubuntu is not detecting ANY partition made on my hard-disk. I met a guy who is good at linux.he told me that it MAY be something link to my hard-disk as its a Hitachi one and that am having it over 3 years.(pretty old i think)

i know well that ubuntu create a file system called ext4 or ext3 ,but i know also that it can read NTFS and FAT.So from that point of view,i think ubuntu MUST have detected the two partitions,But that not the case.

[COLOR=Red]**THANKS FOR REPLYING,HOPE TO HEAR From YOU SOON.**[/COLOR]

---

### Post by Quackers on 2010-12-11
Yes, I agree that the installer is not finding your hard drive. It's why it's not finding it that's the problem. It could be for a few reasons.
Is your bios set to IDE mode or AHCI?
Is Raid in use, or has the hard drive ever been part of a raid array?

---

### Post by tommcd on 2010-12-11
> **bitsonhj said:**
> 
YOU SEE, even if there is some unallocated space,ubuntu is not detecting ANY partition made on my hard-disk. ...
You could try using a Parted Magic live CD to attempt to partition the drive. Parted Magic works very well in my experience. [http://partedmagic.com/](http://partedmagic.com/)
If Parted Magic does see the partitions, then create a ext4 partition in the unallocated space you created. Then boot the Ubuntu live CD and install Ubuntu to the new ext4 partition.

---

### Post by bitsonhj on 2010-12-11
ok guys.
am gonna reply you back after reading on Raid and Ahci(what's this).
[COLOR=Red][B]
Thanks for replying.I will get back to you soon.[/B][/COLOR]

---

### Post by bitsonhj on 2010-12-12
[B][COLOR=Red]TO QUACKERS :

[/COLOR][/B][COLOR=Red][COLOR=Black]frankly speaking man,i do know what raid is(from wiki),but the problem is that i don't know where to look for it(to check whether its on RAID or AHCI)??
can you help me about that.??
In fact in the message which tommcd send me just after you,i used this bootable software and i found that(am not sure) my hard-dish is on RAID.


[COLOR=Red][B]TO TOMMCD :

[/B][COLOR=Black]I downloaded the software 'pated magic..." in an iso file,i burn it,then i change my boot to ''cd' and look what i have got when i open partition...(even after i refresh it from the Gparted menu) :
[IMG]http://i277.photobucket.com/albums/kk47/bitsonhj/Screenshot-1.png[/IMG]the partition in my hard-disk is not detected.its the same when i install ubuntu.they are detecting it as a new hard-disk without any partition.


[SIZE=4][FONT=Comic Sans MS]Thanks for replying.Hope to hear from you and Quackers soon.[/FONT][/SIZE]
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by Quackers on 2010-12-12
How many hard drives are listed in your bios?
Does your bios show RAID as an option?

---

### Post by bitsonhj on 2010-12-12
only my hitachi hard-disk is listed.
and i don;t see anywhere for a RAID selection(no where to be seen in the bios )

Thnks,hope to hear from you soon.

---

### Post by Quackers on 2010-12-12
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by bitsonhj on 2010-12-12
here it is quackers :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
```

sorry but when i press the # i didn't get the thing you told me.

thanks for replying.hpe to hear from you soon.

---

### Post by Quackers on 2010-12-12
It would seem that your partition table is corrupt. That could be from a failed resizing attempt or from something else.
From the live cd use testdisk to try and restore a usable partition table.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by bitsonhj on 2010-12-12
ya thanks for the reply,the only problem is that am afraid that i may loss all my data

My question here is that you assume that my data will not be loss?

---

### Post by Quackers on 2010-12-12
I'm surprised that Windows boots ok to be honest. If the partition table is corrupted I would expect nothing to boot, but I could be wrong there.
I have never used testdisk, but many people have and have had great success with it.
In all honesty, it is not wise to be resizing and/or creating partitions on a disc that has not been backed up!

---

### Post by Quackers on 2010-12-12
As you can still get in to Windows I would suggest that you back up your data, if you haven't done that already.
I would then suggest that you run a chkdsk on the C: and D: partitions

[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

---

### Post by bitsonhj on 2010-12-12
am not saying that i don't make backup,but the problem here is that i want to have both windows and ubuntu to do my workings.
why scared for windows? thats becuz i got to do some assignment on it,and also i have bought some original software.i will wait until that there license has expire to get ride of windows.

So am scared about that(testdisk) if something went wrong(until someone who has use it tell me directly).

So after all,i think its my hard-disk which is faulty?
what do you think about that??

---

### Post by Quackers on 2010-12-12
I understand your concerns. This is why I suggest running a chkdsk first. If chkdsk finds errors you should run it until no errors are found. You should also check the fix and recover boxes.
Then try the Ubuntu installer again and see if it finds your disc. If it doesn't I can only suggest testdisk. As I say, many other people have had great success with it. It also has the capability to recover partitions.
By all means wait for a second opinion if you wish :-)

---

### Post by bitsonhj on 2010-12-12
ye thanks for replying.

i have already run chkdsk,and there was no errors.
i will just wait for a second reply on 'testdisk' then i wwill act on what i think the best.

Thanks for you concern! ;):D

---

### Post by Quackers on 2010-12-12
No problem :-)
I hope your problem is solved soon!

---

### Post by bitsonhj on 2011-07-21
Alright guys.

After all this time, i got a hardisk crash.

With this new HDD, ubuntu installation is running fine!!

---

