---
title: "Stubborn Grub!!"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by onederer on 2006-11-06
I'm using Kubuntu, and I don't suppose that this makes any difference since I dealing with Grub.  My computer is an odd one.  WindowsXP refuses to install itself in /dev/sda0. It is installed in /dev/sdb0, and boots up with not problems with that configuration.

Now comes the problem. With whatever Linux Flavor distro that I tried to install, I was never able to access it after the installation was completed.  It took me a while to find out why. My conclusion is because Grub wants to install itself in the SATA drive /dev/sda0 where Kubuntu Linux is now installed.  And this configuration is usually the way that Windows/Linux is installed, but not in my system!  Is it because of the SATA drives? I don't know. I just haven't been able to place GRUB into the proper drive, and give it the proper directions to make it pick up Kubuntu once installed.  A good thing that I succeeded to Make MS$ the default OS, otherwise, I'd have nothing to boot to.

Now, the only way that I can access Kubuntu is by using the free Super Grub disk.](*,) However, this is not an easy thing to do, and sure takes a long time to accomplish.  Super Grub disk cannot on it's own get the system to boot up. I've learned to edit it to get the proper results. But I've not been able to install it on the proper hard drive, and use it to give me a menu as to which OS that I want to boot up.  Maybe I'm just too thick headed and too old to learn, but I sure do need help! I'll never be able to make a Linux convert out of my wife if I'm having this much trouble to be able to use a Linux distro.  She's kinda of a technophobic. If it don't work right the first time, she want's no part of it.

So, Kubuntu lives on SATA drive /dev/sda0, and Win$ is on /dev/sdb0. I believe that Grub is on /dev/sdb0 which is why the sequence is wrong; I never get to see Grub. How do I make it right?  I don't care if the Grub bootloader is on one of the hard drives or on a floppy, since I'm lucky enough to have a desktop that has a floppy drive.

I may not be able to come again to this web site soon. Could you please forward your response to: zonofabee(at)gmail.com

Cheers!:) :D

---

### Post by confused57 on 2006-11-06
In case you're able to get back to check for replies, you may just need to add an entry in grub to boot Windows, similar to the one found in this link:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by onederer on 2006-11-06
> **confused57 said:**
> In case you're able to get back to check for replies, you may just need to add an entry in grub to boot Windows, similar to the one found in this link:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
Hi,

This is not my problem now! My problem is to install Grub where it will be seen on boot up and to be able to select an OS. Right now, without the Super Grub Disk, I can't access Linux at all. Windows XP boots up ok. And the Super Grub Disk display has to be edited to be able to access Linux.
This is what I have to do:
<edit Grub>
grub> [COLOR="SeaGreen"]kernel (hd1,0)/boot/vmlinux[/COLOR] [COLOR="Magenta"]root=/dev/sda1[/COLOR] ro (this will tell me the version of vmlinuz, and this is what I will add at the final edit before I boot up)
grub> [COLOR="Red"]initrd(hd1,0)/boot/vmlinuz[/COLOR] (this will tell me what version of vmlinuz to use)

Once I've done this and after I've added the version number of vmlinuz, and initrd, I give it the "boot" command and Kubuntu starts up ok.

What I can't do is to get Grub to install itself in the proper manner so that I will automatically  see the boot manager when I turn on the machine. I don't want to keep on using the Super Grub Disk forever.   I haven't even considered including WindowsXP yet. And I suppose that if Grub is installed on a floppy, I won't have to include Windows, as long as Grub accesses Kubuntu. Windows boots up now, and no boot manager is seen.  Standard commands to install Grub DO NOT WORK IN this system! That would be too easy! This is why I'm asking for help to accomplish this.

---

### Post by confused57 on 2006-11-06
You might be able to install grub to floppy using this method:
[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

Have you tried using the live cd to install grub?:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

The previous link I gave you wouldn't work with your setup, since your Windows drive is on hd0 and Kubuntu on hd1, according to the entries you use to boot the kernel.  You'd need a different Windows entry in grub than the one in the link to boot Windows.

---

### Post by onederer on 2006-11-06
Hi, 

Please note that SATA drives are listed as /dev/sd?, and not as /dev/hd? This could possibly be the source of my problems because of the SATA controller?

I don't have standard hard drives installed in this system.  They both are SATA drives. I'm not that well versed in SATA drives, and their controller.

*My Windows is on hd1, and Kubuntu is on hd0*.  This is just the opposite that a system would normally be installed. Kubuntu occupies the first serial hard drive; WinXP is on the second hard drive. They each have their own separate hard drive.

And I did use the "live" cd to install Kubuntu. The installation was very normal, and apprantly trouble free. And when the installer asked me to install Grub, I let it do it in it's "nomal" way. But that way doesn't work.  I am still not worried about listing WindowsXP yet. But **I do want to see the boot loader** when the machine starts up, and I want to see Linux as a bootup option. Up to now, I don't have that pleasure.

The only thing that I can tell you is the list of commands that I wrote down, work. But it is temporary, and I have to manually enter those commands every time that I want to access Kubuntu. Now, how do I make it permanent, and what drive do I place it in? I assume that once that is accomplished, the Grub menu can be edited to include Windows?
This is what I don't understand at the moment, and have not been successful in accomplishing.

And thanks for the URL for the floppy disk info.

Cheers!

---

### Post by confused57 on 2006-11-06
> **onederer said:**
> Hi, 

Please note that SATA drives are listed as /dev/sd?, and not as /dev/hd? This could possibly be the source of my problems because of the SATA controller?

I don't have standard hard drives installed in this system.  They both are SATA drives. I'm not that well versed in SATA drives, and their controller.

*My Windows is on hd1, and Kubuntu is on hd0*.  This is just the opposite that a system would normally be installed. Kubuntu occupies the first serial hard drive; WinXP is on the second hard drive. They each have their own separate hard drive.

And I did use the "live" cd to install Kubuntu. The installation was very normal, and apprantly trouble free. And when the installer asked me to install Grub, I let it do it in it's "nomal" way. But that way doesn't work.  I am still not worried about listing WindowsXP yet. But **I do want to see the boot loader** when the machine starts up, and I want to see Linux as a bootup option. Up to now, I don't have that pleasure.

The only thing that I can tell you is the list of commands that I wrote down, work. But it is temporary, and I have to manually enter those commands every time that I want to access Kubuntu. Now, how do I make it permanent, and what drive do I place it in? I assume that once that is accomplished, the Grub menu can be edited to include Windows?
This is what I don't understand at the moment, and have not been successful in accomplishing.

And thanks for the URL for the floppy disk info.

Cheers!
Grub recognizes hard drives as hd0, hd1, hd2, etc...for example, hd0 is used for sda or hda, depending on whether you have SATA or IDE drives.  Your bios may designate the drives in a similar manner, hd0 & hd1, respectively, for the 1st & 2nd hard drives.

The reason I say Kubuntu is on hd1 is because of your entries used in booting, root (hd1,0) on /dev/sda1, therefore, it appears that your sda drive is recognized as hd1 in your /boot/grub/device.map file.  SATA drives can be a bit tricky, the device.map could have been set this way, if you had the Windows as the first hard drive to boot when you installed Kubuntu.

You've probably already done so, but have you tried booting the Kubuntu drive first by changing it in bios?  If so, is there an option to press "Esc" to enter the grub menu during bootup.

You might want to PM "Herman", a forum user who is much more experienced with grub than I...he may be able to help you.  Here's his website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by onederer on 2006-11-07
Thank you for the comeback.

I am aware of the designations of (hd,x) for Grub. I used the /dev/sd? for clarity, since I'm trying very hard to get the situation understood.

WinXP is definitely intalled on drive (hd1).  This has been verified by the patitioner that I used, and also when I checked it out using Windows. Also, the bios tells me the same. But apparantly, some of the information has been installed in the MBR of Windows (hd1).  This is where Grub picks it up after I edit the information, to boot up Kubuntu, using the Super Grub Disk.  My guess is that under normal conditions, Grub would be looking for that information from (hd0), but it is not there which would account why I don't see Grub when I start the machine. This forces me to edit Grub EVERY time that I start the machine. If you notice that the edited commands tells Grub where to find the initrd and the vmlinuz, and that is not in a common setup sequence. And yes, I tried to switch the drives using the bios, and got the machine to ask me for a bootup floppy, or a valid hard drive, since it couldn't find Windows. The Bios designates the hard drives the same way as Grub does.  But the mystery is why Windows can only be installed on the _second_ SATA hard drive. That drove me crazy for more than 2 weekS when I was trying to install WinXP in the first hard drive. XP kept on telling me that it couldn't install itself in an incompatible hard drive. The drive was already formatted to NTFS, but that made no difference. I succeeded to finally install XP, when out of sheer frustration, I tried to put it in the second hard drive, and succeeded to solve the mystery. It installed in that drive with flying colors! It worked, so I didn't question it.  That is, until I tried to install a Linux distro in the _FIRST_ hard drive. Nothing looked wrong for the installations, until I went to reboot, and found no bootloader manager. Windows booted ok, and I kept on thinking that I had corrupt installations, but that was not the case. The problem finally narrowed down to Grub, and it not being able to properly identify that machine's correct setup.

The only way that it works now, is with the current setup that I've already explained. Now it has to be translated into a permanent working setup, which I don't quite know how to do. Which is why I'm here.

I would like to clarify that I am NOT using the standard Grub boot menu. So editing as you suggested doesn't work in this case.  Grub doesn't exist in that machine as a usable application. I'm getting Grub from the Super Disk, and that disk keeps on telling me that it can't install Grub under existing conditions. I'm using that disk's built-in Grub editor to access Linux. Editing Grub is the only way that I can mold Grub to access Kubuntu. Super Grub Disk is a tool and should not have to be used in this fashion forever.

Oh, and thank you for Herman's URL.

Cheers!

---

### Post by adrian15 on 2006-11-07
I do not understand very much your boot situation but the way to go is the following one:

Boot installed Ubuntu with Super Grub Disk... run a terminal as root.
Inside a terminal type the following:
```

grub
grub> device (hd1) /dev/sda1
grub> device (hd0) /dev/sda2
grub> root (hd1,0)
grub> setup (hd0)
grub> quit

```

and you can reboot and check the changes.

I do not think you will need the map commands.

adrian15

---

### Post by bulldog on 2006-11-07
What I know about Sata disks.

They are atached at your MotherBoard by red kabels on sata1 /sata2 /sata3 /sata4.There's no such thing as master and slave like IDE drives had.
The way they are atached to your mobo makes one sda and the other sdb.

By simply reversing the kabels your problem should be solved.
However,you can set in your BIOS which hard disk should be the first to boot from.
So it's even simpeler to reverse your hard disk,you don't have to open your case.

---

### Post by onederer on 2006-11-07
Thank you Adrian.

I'll try what you wrote.  Does this agree with the edited commands that I have to use with the Super Grub Disk to access Linux?

Those command sequences are the only ones that I can use to access Kubuntu, and I have to use the version numbers for vmlinuz and initrd or it won't work. With the proper command sequence and version numbers, the bootup is normal, with the Kumbuntu splash screen coming up.

Do you know how to put it on a floppy disk? Or is the kernel too large for that now?  With the floppy I would only have to point the bootloader to where Linux is, and without the floppy, XP would normally bootup.

Right now, XP boots up (/dev/sdb). No evidence of a boot loader shows up. No evidence of an installed Linux is apparant. I only find Linux after a search using the Super Grub Disk. But the Super Disk cannot figure out the setup, and that WinXP is on the second SATA hard drive.  The command sequence that Super Disk automatically offers is wrong and doesn't work. This is when my editing the commands, provides the magic to make it boot Linux. This is not just Kumbuntu related. This problem existed when I tried installing other distros in this machine, also.  It all boils down to the boot loader providing the proper sequence of events, and for the bootloader to be installed in the correct hard drive(s)?, so it can be seen when the machine is started.

Cheers!

---

### Post by confused57 on 2006-11-07
adrian,
   I don't know, but shouldn't the 3rd line in your commands be?:

grub> device (hd0) /dev/sdb1

I don't have any experience with SATA drives, so I'm not sure.

---

### Post by onederer on 2006-11-07
Hi, 

Right now, the only thing that works is in this order:
grub> kernel (hd1,0)/boot/vmlinuz (add here the version number) root=/dev/sda1 ro (this points to where Linux is located
grub> initrd (hd1,0)/boot/vmlinuz (add here the version number)
grub> boot

This sequence is the only thing that I know of that works at the moment. If anyone else knows someting more, I'd be glad to try it out.  All I know, is that this works!

Cheers!

---

### Post by confused57 on 2006-11-07
Herman is active in the forums, and usually answers threads pertaining to grub...again, you could PM him just directing him to this thread.  He probably gets many PM requests for help and it would really be better if any suggestions he might have be posted to this thread...that way, if anyone else has a similar problem they might find an answer here.  I'm sure he wouldn't have time to give one-on-one PM help to a plethora of users with questions pertaining to grub.  If he hasn't seen this thread in a day or two, you might want to go ahead and send a PM.
Herman, hope you don't mind me directing people to you.

At least I bumped your thread...good luck.

---

### Post by Herman on 2006-11-12
Hello onederer,
Can you post a copy of the results you get from 'sudo fdisk -lu' please? You can use a Live CD for that or boot into your operating system for that, ```
sudo fdisk -lu
``` 

Also, it might be interesting to see what 'Parted thinks of your hard disks too, please post the output of 'sudo parted /dev/sda p'. and 'sudo parted  /dev/sdb  p',  ```
sudo  parted /dev/sda p
``` ```
sudo  parted /dev/sdb p 
```
Regards, Herman :D

---

### Post by onederer on 2006-11-12
Greetings Herman,

I hope that the following information will finally resolve the Grub problem.

> 
Here's the result of your first request:
onederer@SM-1:~$ sudo fdisk -lu
Password:

Disk /dev/sda: 200GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units= sectors of 1 * 512 = 512 bytes

   Device  Boot      Start         End       Blocks     Id  System
/dev/sda1  *         63           386620289 193310113+  83  Linux
/dev/sda2           386620290     390716864  2048287+   82  Linux swap/Solaris

Disk /dev/sdb: 203.9GB, 20328109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units= sectors of 1 * 512 = 512 Bytes

  Device   Boot       Start          End     Blocks       Id   System
/dev/sdb1  *          63         198267414  199133676     7   Hpfs/NTFS
onederer@SM-1:`$


> 
Here's the result of your second request:
onederer@SM-1~$ Sudo parted /dev/sda p
Password:
Disk geometry for /dev/sda: 0kB-200GB
Disk label type: msdos
Number  Start   End   Size   Type  File system   Flags
  1       32kB  198GB 198GB  Primry  Ext3        boot
  2      198GB  200GB 2097MB Primary linux-swap
Information: Don't forget to update /ect/fstab, if necessary   


> 
Here's the result of your last request:
onderer@SM-1:~$ sudo parted /dev/sdb p
Disk geometry for /dev/sdb: 0kB-204GB
Disk lable type: msdos

Number   Start   End   Size   Type   File system   Flags
  1       32kB   204GB 204GB  primary NTFS         boot
Information: Don't forget to update /etc/fstab, if necessary.


Cheers!

---

### Post by Herman on 2006-11-12
Thanks onederer,
You have a msdos disklabel on both disk, I don't know why Windows XP said your sda was an 'incompatible hard disk'. Your partitions begin in the right sectors too. Everything there looks okay to me. Thanks. :D

Now, let's take a look at your MBRs, eh? Can you post the output from these two commands for me please? (You don't have to type these yourself, you can just copy them off this post and paste them in your terminal in case you didn't know). If you do type them yourself, be sure you get them exact please.
```
sudo dd if=/dev/sda count=1 | hexdump -C
``````
sudo dd if=/dev/sdb count=1 | hexdump -C
```Those should tell me exactly what is on both of your MBRs.
Thanks, Herman :D

---

### Post by Herman on 2006-11-12
onederer,
I have to go now just for a few hours, but there's something else I was going to see if you would mind trying, ( it's easy). 
Does your computer have a message on the bottom of your monitor sometime during bootup telling you something like 'F12 for manual boot' or something along those lines?
For a lot of computers it's the 'F8' key I'm told. You can tap that key a few times while that message is displayed to get a menu offering you a chioce of bootable devices. You can choose to boot from floppy, cd or either hard disk, etc. Can you try to see if you can get your computer to see the MBR on hard disk number 1 that way? If Grub is installed in it, it should boot then maybe. I have a feeling you would have Grub in MBR alright, it's just a matter of getting your BIOS to see it.
Regards, Herman :D

---

### Post by onederer on 2006-11-13
Greetings Herman,

> **Herman said:**
> Thanks onederer,
You have a msdos disklabel on both disk, I don't know why Windows XP said your sda was an 'incompatible hard disk'. Your partitions begin in the right sectors too. Everything there looks okay to me. Thanks. :D

Now, let's take a look at your MBRs, eh? Can you post the output from these two commands for me please? (You don't have to type these yourself, you can just copy them off this post and paste them in your terminal in case you didn't know). If you do type them yourself, be sure you get them exact please.
```
sudo dd if=/dev/sda count=1 | hexdump -C
``````
sudo dd if=/dev/sdb count=1 | hexdump -C
```Those should tell me exactly what is on both of your MBRs.
Thanks, Herman :D

Here's the first drive (/dev/sda)

onederer@SM-1:~$ sudo dd if=/dev/sda count=1 | hexdump -C
Password:
1+0 records in
1+0 records out
512 bytes (512 B) copied, 4.7e-05 seconds, 10.9 MB/s
00000000  eb 48 90 8e d8 8e c0 8e  d0 bc 00 7c fb be 00 7c  |.H.........|...||
00000010  bf 00 06 b9 00 01 f3 a5  e9 00 8a be b2 07 38 0c  |..............8.|
00000020  74 3c bb 00 08 51 0f b6  0c ba 80 00 e8 ca 00 59  |t<...Q.........Y|
00000030  72 21 46 fe c5 81 c3 00  02 38 0c 75 e8 33 03 02  |r!F......8.u.3..|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  cd f2 a6 39 cf c9 80 01  |...........9....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 43 5b 0b 17 00 fe  |......?...C[....|
000001d0  ff ff 82 fe ff ff 82 5b  0b 17 3f 82 3e 00 00 00  |.......[..?.>...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
onederer@SM-1:~$

Here's the second drive (dev/sdb)

onederer@SM-1:~$ sudo dd if=/dev/sdb count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 5.1e-05 seconds, 10.0 MB/s
00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  01 3d 01 3d 00 00 80 01  |.....,Dc.=.=....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 d8 13 bd 17 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
onederer@SM-1:~$ 

As for your post below, I have to agree with you that perhaps the Bios doesn't see the boot-loader. Perhaps because WindowsXP is on the second drive. I'm not an expert, so I'm just speculating.  But I have to conclude that the Bios **does** see WinXP, and **does** boot it up.
At the moment, I'm just worn out with this BS.  It's been going on for too long. I want to go back to being a user once again, and not a Linux (Grub) mechanic.  And to top it off, I just lost Grub on my laptop. :evil: It happened when I tried to make Win** the default OS so my wife could use the machine. And what did I get? I got a Grub that shows all the partitions as HIDDEN! I used the Super Grub Disk, and was not able to recover Grub. It didn't even fix the MBR. And when I re-boot, that same Grub display with the "hidden" partitions shows up. However I was able to boot into Win** partition using the Super Grub Disk, but I can't get it to write a working menu over the bad display. It didn't even fix the 'hidden' to 'visible' problem. The setup on that machine is standard, in the sense that it is only one drive and Win** is the first OS, and Freespire is the second OS on the /dev/hda. You know? At this point, I don't like boot loaders very much!

That OS is Freespire. It was the only one that worked and made it possible to use the laptop wirelessly.  Kubuntu was not able to do that with the HP laptop. Otherwise they both work pretty much the same, seeing that they both are Debian derivatives.  

Oh, and thanks for sticking with me.  I sure need the help.:) 

Cheers!

---

### Post by bulldog on 2006-11-13
Hi onederer,
I stated it before but maybe you mist it.
I'll try to explain as easy as possible.

You have two Sata drives which are mixed up as you think because windows is installed on sdb.
This indicates to me that this should be sda,why it's listed as sdb,don't ask.
In this situation you could boot windows I guess.

Then you installed Ubuntu on the sda disk which should be sdb.
The big question is where is GRUB installed.
You stated you never have seen GRUB and I suppose you didn't change anything at your hardware as I proposed in an earlier post.
So the fact should be you boot direct into windows,because this was the default bootdisk and nothing has changed.

That should implicate that GRUB is installed on the other disk known as sda but should be sdb in fact.

Now to see GRUB at startup you should go into your BIOS and search for the boot order and change the disk which is listed as first into second and the second into first.
Most modern computers have the possibility to get to a start menu by hitting a button several times during boot time,it should be somewhere on the screen,mostly at the bottom [hit DEL to enter BIOS and hit ??? to enter boot menu]

This can also been used to try things out and to boot from your second disk.
But it should definitly be in your BIOS so change it there.

If you did find it and boot from the other disk you should see GRUB.
I can't guarantee ubuntu and windows will work,but that we can change,we first need to find GRUB.

Try this and give us an update.

If there's no GRUB on the other disk we can install it,but I should recommend to unplug your windows disk first,so GRUB has to install on the Ubuntu disk.
We can add your windows and all at a later point,that's not a big issue.
I'll give you the method to install GRUB from the live cd.

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
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

### Post by Herman on 2006-11-13
Thanks onederer,
Those 'dd' command outputs tell me definitely that you have Grub installed already in your sda MBR, and WIndows IPL in your sdb MBR, there is no doubt about that now.
It seems to me as if you are just having a problem getting your computer's BIOS to see which disk is which and boot the right MBR. I would tend to agree with bulldog, it seems as if you have some wires crossed somewhere, or some settings wrong in your BIOS. It doesn't seem to me to be Grub's fault. 

I'm really sorry you are having so many problems, sometimes bootloader problems even get me feeling pretty frustrated and a little cranky. In my case I usually cause the problems myself, for a challenge and to try to learn more. My wife does crossward puzzles, I like playing with bootloaders. I guess it's not much fun if you really want to get on with something else. You have my sympathy. I'll try to help you all I can.

You know, I think about three thousand people a week are installing Ubuntu these days, and I think most of them would be using Grub, so it's to be expected that a few will have problems. I don't think there are many problems compared with the number of new installations.

What kind of BIOS does your computer have and who plugged your hard disks in for you and did you try booting with the F8 or F12 keys to select the boot device (a different hard disk), manually? Most computer can do that nowadays, so I have read.

Thanks for keeping on trying,
Regards, Herman :D

---

### Post by Herman on 2006-11-15
This might help, for example, I have an Acer Aspire desktop, and when it's in the early stages of booting, it has a splash screen with a message on the bottom ' DEL to enter setup, F12: Boot Manual'.
So if I press 'F12', that gives me the menu I mentioned already about which device I want to boot.

Now, in addition to that, I also can press 'DEL' and enter 'Setup', which I prefer to call CMOS, lots of people just call it the BIOS. 
Whatever you call it, inside, there's a line you can select called 'Product Information'  When I have that line selected and hit 'Enter', I can see that I have an Acer Aspire T310, system S/N 04193333, Main Board ID E61ML, System BIOS version R01-B3, SMBIOS version 2.3, BIOS Release date Jan14, 2004.

Then, I pressed 'esc'to get back to the main menu, and scrolled down a couple of lines to 'Advanced Bios Features, and hit 'Enter'.
Now, in here, there is a line called 'Hard Disk Priority', I hit enter, and inside that is a list including, my first hard disk, my second hard disk, a USB disk I happen to have plugged in right now, and 'bootable add-in cards. I can move any of these up the list by highlighting one to select it, and pressing my + key.
That might be what you need to do to make your number 1 disk have the boot priority. It wouldn't hurt to go take a look and see what's going on in there, if you have something similar in your kind of CMOS.

Then I pressed ''esc' to get back to the CMOS menu, and a few lines down again is the regular boot device list, 'First Boot Device', Second Boot Device, 'Third Boot Device', Boot Other Device', etc, for which I can set 'Floppy', LS120','Hard Disk','CDROM,'ZIP100,'USB-FDD',USB-ZIP','USB-CDROM'. 
Usually, I just leave that set with Floppy for first boot device, CDROM as  second, and Hard Disk third.
Most people only know about and set this part of their BIOS, and overlook the  'Hard Disk Boot Priority' section I explained in the preceding paragraph. 

Is that any help?

Regards, Herman :D

---

### Post by onederer on 2006-11-17
Greetings Herman,

Even before I ever contacted the forum, I had tried all those things you suggested.  This is why I finally contacted the forum.
I had tried to manually swap the wires on the hard drives. All I got was an error message to insert a bootable disk, no system found.

I tried to use the Bios method to select which hard drive to boot.  I can do that with this Bios. Also, I got the same error message as above. This information, I had given somewhere back when I started this post, so things could be narrowed down. I was hoping that by my posting the set of commands that **do** work, would give you a clue as to what is going on. It seems that Windows will only install itself on just one SATA hard drive in this machine.

Sorry it took me so long to get back to you, but now I have dual problems with Grub on this machine, and on the HP laptop. Both of these I'm trying to resolve at the same time. 

There are times that I just have to throw my hands up in the air, and walk away before I blow up. I've spent too  many hours on this thing. I keep on wondering why I don't end up with simple standard setups. This goes for both machines.  If I had the money, I'd install some standard IDE hard drives.  Perhaps that would resolve the problem, and I'd use these two troublesome SATA drives as a Raid system.

Cheers!

---

### Post by bernied on 2006-11-17
Can we make this poor guy a grub floppy disk? 
It would only need one entry in the menu.lst.

Whilst I'm the same as Herman and would want to solve the 'problem', no matter how long it took me, I've never read so much pain from a forum entry. Like Herman, I also am very sorry that you have suffered so much Onederer. That's sorry in an empathic, not apologetic way.

I have used grub on a usb stick to boot linux on a laptop where I didn't want to touch the MBR. Surely if we make a grub floppy, with those commands that we know will work, dd the floppy image to a file, then send Onederer the file with the dd command to use to put it on the floppy, then that will solve it. It will only be 1.4MB after all. 

Now I say we, because I don't seem to have a functional floppy drive - do they just seize up if you don't use them? I'm off to read the grub manual...

---

### Post by bernied on 2006-11-17
I found a grub image, but I'm unable to put it on a floppy. If it is ok, all it should need is a menu.lst file with the commands that we know will work. Would anyone like to test this for Onederer? And maybe tidy up these instructions??

So you'd need to download this file and unzip it:
[http://gazonk.org/~eloj/files/grubbootimage.zip](http://gazonk.org/~eloj/files/grubbootimage.zip)

There is a single file in the archive, called grubbootimage.img
To put it onto a floppy, you would put an empty floppy in the drive and, in a linux terminal, use the commands:

umount /dev/fd0
dd if=/path/to/grubbootimage.zip of=/dev/fd0

(is sudo needed here?)

The menu.lst file on the floppy should look like this:

title ubuntu
kernel (hd1,0)/boot/vmlinux root=/dev/sda1 ro
initrd (hd1,0)/boot/vmlinuz
boot

The menu.lst file should be in the /boot/grub/ or maybe just /grub/ directory.

---

### Post by bulldog on 2006-11-17
> **onederer said:**
> Greetings Herman,

Even before I ever contacted the forum, I had tried all those things you suggested.  This is why I finally contacted the forum.
I had tried to manually swap the wires on the hard drives. All I got was an error message to insert a bootable disk, no system found.

I tried to use the Bios method to select which hard drive to boot.  I can do that with this Bios. Also, I got the same error message as above. This information, I had given somewhere back when I started this post, so things could be narrowed down. I was hoping that by my posting the set of commands that **do** work, would give you a clue as to what is going on. It seems that Windows will only install itself on just one SATA hard drive in this machine.

Sorry it took me so long to get back to you, but now I have dual problems with Grub on this machine, and on the HP laptop. Both of these I'm trying to resolve at the same time. 

There are times that I just have to throw my hands up in the air, and walk away before I blow up. I've spent too  many hours on this thing. I keep on wondering why I don't end up with simple standard setups. This goes for both machines.  If I had the money, I'd install some standard IDE hard drives.  Perhaps that would resolve the problem, and I'd use these two troublesome SATA drives as a Raid system.

Cheers!

If you can get GRUB on just one Sata disk then maybe replace the cable which it connect with the mobo.
If that not does anything you have to check your hard disk on errors.
Just switch the cabels from your both hdd's and see if the error is replaced to the other hdd.

---

### Post by Herman on 2006-11-17
Yes, I'm out of ideas for now, I'll keep thinking about it though, I was hoping that would have solved it. Hmm :confused:

I think bulldog seems to know best what to try next, it seems to me as if it is a BIOS or hardware issue, not Grub or Ubuntu. Maybe bulldog can help you more than I can.

In the meantime, I agree with bernied, even though you can use [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php")  it's not so convenient to have to use all the time. It would be nicer to be booting with a Grub disk made specially for your own computer.

This will make you a grub boot floppy with your own Grub menu in it, so it should perfectly suit your computer already, there will be no more setting up to do. You'll need to boot with Super Grub Disk just one more time to do this. These commands can be copied from here and pasted, so you won't have to type even one command. Just put a good floppy disk in your floppy drive, and open a terminal, and copy and paste these into it one at a time, pressing 'enter' after each one....
```
sudo mkfs /dev/fd0
``````
sudo mount /dev/fd0 /media/floppy0
``````
sudo mkdir -p /media/floppy0/boot
``````
sudo cp -r /boot/grub /media/floppy0/boot
``````
sudo umount /media/floppy0
``````
sudo grub
```Now you will have a grub prompt.```
grub> find /boot/grub/stage1
```You should receive a reply similar to the following,
> (fd0)
(hd0,1)```
grub>root (fd0)
``````
grub>setup (fd0)
``````
grub>quit
```That's it! Your Grub floppy is done! Try it out!

If you need to edit the menu.lst in the floppy disk, use this code:

```
sudo mount /dev/fd0 /media/floppy0
``````
sudo chmod -R 777 /media/floppy0
``````
sudo gedit /media/floppy0/boot/grub/menu.lst
``` You can [customize your new Grub menu]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst") if you like, 

Regards, Herman :D

---

### Post by onederer on 2006-11-20
Hi,

Thank you for your effort.  I'll be trying what you have suggested. But I won't be able to get back with you for the results until after Thanksgiving.  I do believe that a floppy disk would be the salvation to this problem. And I'm very thankful that I had to foresight to order a floppy drive when I ordered that system.  In Linux, that drive is still very useful.

It is still the hunting season here, and I'm trying to put in as much time as I can in the woods for putting meat on the table for the next year. So I have my plate-full at the moment with this system, the laptop, and slogging through the local soggy swamps to bag a deer. 

Cheers!8)

---

### Post by Herman on 2006-11-21
onederer, 
Good luck with your hunting! 
I'm glad this thread got me interested in making a Grub floppy disk, I am finding mine quite a lot of fun, actually.  I made this into a new how-to in my website too, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make")
I guess it is as close to solving your problem as we can get for now anyway. I agree, it is lucky you have a floppy disk drive, not everyone has those now.
I also have a how-to for making your own personal Grub CD, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD"). (In case someone else viewing this thread has a similar problem, but does not have a floppy disk drive.
Floppy disks are fun though, because they are easy to edit, but a CD needs to be reburned every time. I think it would be wise to make one or two extra Grub floppys, for spares though, because they are more easily damaged than a CD.

Regards, Herman :D

---

