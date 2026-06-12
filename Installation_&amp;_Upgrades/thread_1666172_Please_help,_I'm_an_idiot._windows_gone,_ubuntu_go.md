---
title: "Please help, I'm an idiot. windows gone, ubuntu gone"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by daverobzippy on 2011-01-13
[SIZE=4]Really don't know where to start explaining what I've done but let's get this out of the way first, I am an IDIOT.
I fancied the idea of a dual boot laptop with windows 7 which it was already running and ubuntu.
Downloaded ubuntu and placed on usb memory stick with installer package.
restarted laptop and instructed it to boot from usb, installed ubuntu. restarted for the machine to boot straight to ubuntu,
restarted again for it to boot to nothing, just a command prompt.
I can run ubuntu from usb, enabling me to access the internet. when I look at the hdd from disk utility it is showing it as empty.
I realise I have jumped into water that is way too deep for me and have been an idiot in doing so. I have no recovery discs for windows 7. The os isn't as much a problem as the files <i should of backed up before meddling.

Any help in this would be greatly appreciated.

thanks 
[/SIZE]

---

### Post by Quackers on 2011-01-13
Welcome to UF.
It is dangerous to be installing/partitioning without the means to recover your system. Not to mention time consuming!
You don't say which version of Ubuntu you have installed. If it's 10.04 you may be better off than with 10.10, but we'll see.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by daverobzippy on 2011-01-13
Thanks for the quick reply. below is the info you requested. thanks again



 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         439,554,465   488,392,064    48,837,600  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb         14E7-144B                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  a4 f8 9b 58 fe db d3 ac  ee 92 ea 1f b5 c4 be 7e  |...X...........~|
00000010  e0 ac a0 79 83 05 81 0c  49 2d 93 c0 e7 d7 9d f0  |...y....I-......|
00000020  e5 81 d6 bc 45 63 6d 74  e5 9e ee e4 35 c3 b1 e5  |....Ecmt....5...|
00000030  b2 72 df 8e 33 48 a8 c6  db 9b d7 ff 00 0e 2f d3  |.r..3H......../.|
00000040  e1 dd ae b7 0d bc b3 de  5d 4c cd b4 29 02 38 82  |........]L..).8.|
00000050  8c 72 78 24 ee dd 81 ce  00 f5 af 2c 0b b8 e3 38  |.rx$.......,...8|
00000060  f7 af a7 3e 24 7c 55 be  f0 67 82 ae f4 ad 26 fa  |...>$|U..g....&.|
00000070  e6 c5 b5 35 6b 61 04 6e  55 0c 64 61 db 68 38 fb  |...5ka.nU.da.h8.|
00000080  b8 00 f5 19 1e 95 f3 44  63 62 97 3d b9 ff 00 0f  |.......Dcb.=....|
00000090  d7 f9 1a 9d cb 63 ad 6f  ae b4 f6 1e 54 ed 13 0e  |.....c.o....T...|
000000a0  a1 4f 19 f4 c5 6e 59 f8  da e2 2c 2d cc 4b 30 fe  |.O...nY...,-.K0.|
000000b0  f2 7c a7 fc 2b 9c 3c 9c  f7 a5 8d 37 b0 18 cf f5  |.|..+.<....7....|
000000c0  a0 2e 75 f7 be 24 d3 75  2b 54 8a 47 9a 34 77 02  |..u..$.u+T.G.4w.|
000000d0  40 a9 f3 05 cf cc 47 6c  e3 de bd 07 c4 ff 00 11  |@.....Gl........|
000000e0  74 67 f0 6c 96 da 25 d2  99 64 55 b6 48 95 4a b4  |tg.l..%..dU.H.J.|
000000f0  49 8e 4e 0f a2 82 01 f5  22 bc 39 91 50 ed 53 c0  |I.N.....".9.P.S.|
00000100  e3 39 ce 6a dc 20 41 6e  5c f5 6a 56 0b 9d d7 87  |.9.j. An\.jV....|
00000110  40 5d 26 1c 0c 0e 78 1d  b9 ad 20 71 5c 36 95 e2  |@]&...x... q\6..|
00000120  c9 2c 21 48 65 85 65 89  7a 10 70 d5 d1 59 f8 a2  |.,!He.e.z.p..Y..|
00000130  c2 ef 03 cd f2 5f fb b2  8c 7e bd 29 15 73 63 38  |....._...~.).sc8|
00000140  f7 aa f7 3a 7d b5 e1 06  68 15 d8 74 7c 61 87 d0  |...:}...h..t|a..|
00000150  f5 a9 55 d6 41 b9 48 65  3d 08 34 ec d0 33 27 50  |..U.A.He=.4..3'P|
00000160  d2 f6 5b 92 67 13 42 a3  3e 55 da 09 94 7d 09 e4  |..[.g.B.>U...}..|
00000170  7e 75 e9 7f b3 e6 99 71  e1 cd 1b 54 d7 a1 85 ad  |~u.....q...T....|
00000180  5b 58 5f b2 5b dc 46 86  30 21 49 55 9f 61 ef 99  |[X_.[.F.0!IU.a..|
00000190  23 50 4e 7f 80 8e f5 e7  5a d2 4b 73 6e 96 96 e3  |#PN.....Z.Ksn...|
000001a0  75 c5 cb ac 31 af ab 31  c0 fd 4d 7d a5 f0 cb c1  |u...1..1..M}....|
000001b0  9a d5 b7 82 2d 6c fc 23  ac 45 a8 69 76 88 20 7d  |....-l.#.E.iv. }|
000001c0  27 56 8d 39 20 02 48 46  2c b8 24 93 9c ae 4e 69  |'V.9 .HF,.$...Ni|
000001d0  01 f2 76 bd e1 7d 67 58  d7 ae a1 b8 b3 b9 8e 4d  |..v..}gX.......M|
000001e0  46 e9 cb dc 7f ac 18 91  c9 67 2e 09 e7 04 9e 79  |F........g.....y|
000001f0  cd 5b f8 e3 ab 45 a6 68  fa 6e 81 6a 04 71 e0 31  |.[...E.h.n.j.q.1|
00000200

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  ff b1 dd 01 a8 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 4b 14 e7 14 4e  4f 20 4e 41 4d 45 20 20  |..)K...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 80 77 00 00  66 ba 00 00 00 00 bb 00  |}.f..w..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Quackers on 2011-01-13
Basically the boot script says it can't read your hard drive. This is not good at all. Were you installing 10.10? Did you choose the "install alongside" option?
How many primary partitions was Windows 7 using before you tried to install Ubuntu, and what partitions did you create to install Ubuntu into, if any?

---

### Post by daverobzippy on 2011-01-13
Yes installing 10.10 no not the install alongside , the other one with advanced in brackets.
created 1 partition to install ubuntu into of size 25gb. 
Really lost now. 
thanks again

---

### Post by oldfred on 2011-01-13
If you have some data to recover testdisk & photorec may help. Even if testdisk can recover partitions, the install overwrote something so it would not be bootable, but may show files. If testdisk does not recover partition, photorec will recover files, but requires another drive to copy data to. I lost two folders and it recovered 100's of files, one text file I had saved many times was recovered many times as it found each old copy I had saved.


enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by Quackers on 2011-01-13
If Win 7 was pre-installed it may have been using all 4 primary partitions. Creating another partition may have caused serious problems. Even if that is the case, the boot script would have been able to show the details. The fact that it doesn't is more concerning.
Do you have a Windows 7 repair disc? Is there a hidden recovery partition on the hard drive - there usually is? Consult your manual for details on how to activate that partition - it is usually by tapping a key during boot (like F11 or del)

Also see oldfred's post above, re testdisk/photorec

---

### Post by daverobzippy on 2011-01-13
All that went over my head my friend. I can find the sites where the software is available to download fine, getting it to run is another matter. absolute beginner in these matters.
do I junk the laptop now??

---

### Post by daverobzippy on 2011-01-13
Quackers, no I don't have a recovery disc. the gentleman above you just added more confusion. all I can see at the moment is a scrap laptop and it's hard for me to see a way out. any help will have to be given very basically, I appreciate any time you guys can give me on this greatly

---

### Post by Quackers on 2011-01-13
What laptop?
How old is it?
Do you have a manual for it?
It is definitely not scrap - but your data could be gone. That is why oldfred posted about testdisk/photorec, which may be able to recover it all, or some of the files.

---

### Post by daverobzippy on 2011-01-13
It's an acer aspire 5738, 18 months old.
The programs to which you refer I was unable to make do anything, the whole process of getting them to run, which version to download, how to run it. all confuse me. feel really gutted to have been tripped up like this

---

### Post by Quackers on 2011-01-13
If your recovery partition is intact, it seems the way to activate it is by holding down the Alt + F10 keys during boot up.
If this works and you continue with the recovery, it will re-install the OEM version of Windows that the laptop came with - no updates, no user, no data. Like it's a brand new laptop again!.
Trying testdisk and/or photorec may be a better option for you to recover partitions or files. Details here
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
These are the only options that I am aware of for your predicament, short of buying Windows again, and re-installing Ubuntu.

Please note, whatever course of action you choose, please make recovery dvd's and a repair disc when Windows is running again. It saves a lot of heartache.
Installations and hard drive partitioning can go wrong - as you have seen.

---

### Post by daverobzippy on 2011-01-13
I will try the alt f10. ike you say no files but it's only a month since i last 
backed up photos to mothers pc.
I can download the test disk programme but don't understand how to make it run in ubuntu

---

### Post by daverobzippy on 2011-01-13
tried alt f10 and got the following message

HDD recovery validation failed
press any key to continue
error : unknown file system
grub rescue >_

Would be helpful to be able to run the software you mentioned above.
thanks again

---

### Post by daverobzippy on 2011-01-13
on another note when I was using windows it aqquired a virus which caused search results to be hijacked.
this is exactly the same when using firefox in ubuntu off the usb.

---

### Post by Quackers on 2011-01-13
It would seem that the recovery partition is damaged too.
All the details for running testdisk are in oldfred's post number 6 in this thread. Good luck to you :-)

---

### Post by coffeecat on 2011-01-13
@daverobzippy, I know that Quackers won't mind me chipping in here. As an Acer laptop owner (but not your particular model) I have a few observations.

First, your data. Your only hope is with photorec/testdisk. Testdisk is for recovering lost partitions; photorec for lost data. The problem is that the (faulty) installation of Ubuntu will have overwritten some of your harddrive. Even if you were able to reconstruct the lost partitions with testdisk, the filesystems may be badly damaged. And with photorec, many of your original personal files will be overwritten. Also, the trouble with photorec is that it will recover any files it can find indiscriminately - which means thousands of files from Windows and the lost recovery partition.

With regard to retrieving Windows 7, your recovery partition is lost. However, did you remember to create a set of recovery DVDs when you first bought the machine as instructed in the Acer manual? If not, contact Acer. They will probably be prepared to sell you a set. I emphasise sell. They will not give them away. Of course, this will only restore Windows 7 to its default factory settings - i.e., none of your installed apps or data. Also, the Acer DVDs - at least with my model laptop - only restore the Windows C: partition. They don't re-create the restore partition.

---

### Post by Quackers on 2011-01-13
Welcome coffeecat :-) I think you've used testdisk before :-) Your help will be invaluable! I'm going snookering soon, but will be back later.

---

### Post by daverobzippy on 2011-01-13
the problem I am having is getting testdisk or photorec to run in ubuntu. today is the first time I have seen this os.
I am trying a few windows programmes running them in wine if that makes any sense.
If someone would be able to break down how to run test disk and photorec into small chunks that would be great. when I try to run them in the terminal using the commands listed in the instructions all i get is errors.

I appreciate windows 7 is gone but there are some photos and videos i would like back.

Somewhere I have the original recovery discs which are for vista which is what this laptop came installed with, windows 7 was a free upgrade but i have no idea if i still have those installation discs

thanks again guys

---

### Post by smurphy_it on 2011-01-13
The likelihood of getting your system back with Windows 7 is grim.  You can try some of the application pointed out to you.  I believe another one is Active@ Partition Recovery.  However, looking at their website doesn't offer much assistance if you wiped the "system partition".

Looks like you are down to 1 partition now, so you can't boot into another partition to do any kind of restore.

You might have to go purchase a Windows O/S and install on your laptop.


I wish you the best of luck.

---

### Post by daverobzippy on 2011-01-13
Got test disk and photorec to run , using windows versions run with wine?
They show two disks one 12gb and one 82 gb, god knows where the rest of the 250 hdd is at.
when i ran photorec it generated a list of windows files and folders but I don't know what to do next.
remember I am a novice to computers and shouldn't of messed in the first place but if there is a chance the information is still recovorable i will keep going.

any more advice would be welcome

---

### Post by Mark Phelps on 2011-01-13
You keep talking about running things in Wine -- which is confusing.

You would run testdisk or Photorec in Ubuntu -- and point them to the partition you want to analyze and recover. 

IF this is the same partition in which you current have Ubuntu installed, that won't work.

---

