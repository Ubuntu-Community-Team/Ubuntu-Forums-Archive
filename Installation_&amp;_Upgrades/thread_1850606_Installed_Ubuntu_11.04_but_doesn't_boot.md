---
title: "Installed Ubuntu 11.04 but doesn't boot?"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by Sandy000 on 2011-09-26
I'm brand new to Ubuntu so please excuse me for not having a clue what I'm doing.
I installed Ubuntu from a cd and it seemed t;o install fine. (Although I do believe I am having hard disk issues)
When I restarted the system it does not boot, it just goes to a black screen with a blinking cursor?
Any help is appreciated. Thanks :)

---

### Post by Hakunka-Matata on 2011-09-26
Welcome,
The blinking cursor on first boot after install is a well known issue, it can be fixed.
What system are you using to participate in these forums?
What release Ubuntu did you install?
You don't get a grub menu likely when you boot, because it's a single OS computer?, no dual boot?
Try hitting the shift key repeatedly starting when BIOS finishes doing all it's stuff, see if you can get a grub menu, select the (Recovery) system if possible, see what happens.

---

### Post by raja.genupula on 2011-09-27
Hi man 
I have got a fix your issue 
follow this link 

[http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html](http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html)

all the best man .

---

### Post by Sandy000 on 2011-09-27
Hello Hakunka-Matata
I was using the computer that had the problem yesterday to post here.
I can load Ubuntu on the CD. 
I installed the 11.04. 
No grub menu. I had a problem with Windows XP and it has been erased. 
(Cannot be reinstalled from recovery disks)
So I am trying to work with Ubuntu only.
I've tried the shift thing (read it in another post) nothing happens.
I will press the recovery key to check that out next and reply back. 
Thank you for your help. :) 
 
Thanks for the link raja.genupula.
Being a newbie I would prefer to see if H-M can help me first. ;)
[IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG] 8 Hours Ago #[**[COLOR=#000000]2[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=11288797&postcount=2") [[SIZE=5][COLOR=#000000]Hakunka-Matata[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=735950")

---

### Post by Sandy000 on 2011-09-27
Ok after I hit f10 for recovery I get....
 
"GNU GRUB Version 1.99~rc1-13ubuntu 3
Minimal BASH - like line editing is Supported. For the first word, TAB
lists possible command completions. 
Anywhere else TAB lists possible device or file completions.
 
grub>"
 
(Now it comes up to that. Control Alt Delete now doesn't work so had to shut off via the button to wait for reply ;) )

---

### Post by Hakunka-Matata on 2011-09-27
OK, let's try this:
boot normally, once you get to the blinking cursor, hit down arrow once, then hit ENTER.  That might boot into the recovery kernel,  follow your nose if you get that far, repair something or just use the system

**addition:**  I'm not sure if you have a video/graphics problem, or if grub needs to be re-installed... this (above) step should shed some light on that, then we'll do 'what ever is appropriate'

---

### Post by Sandy000 on 2011-09-27
It doesn't come up to the screen with only the blinking cursor any more.
It now comes up to the page with the GNU GRUB
The arrow key and then enter just makes grub> repeat its self. 
I did tab enter t;o see the commands and noticed boot was in there so I tried that and received
"error: no loaded kernel" 
I'm on the machine in question right now using the install cd, that is loading fine. 
(Just a little slow) 
Are there settings we can check?

---

### Post by Hakunka-Matata on 2011-09-27
if you're using liveCD now, please run this code and post the results.
```
sudo fdisk -l && sudo sfdisk -luS
``` please

---

### Post by Sandy000 on 2011-09-27
Here's what I got...


```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a037

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30279   243214336   83  Linux
/dev/sda2           30280       30402      982017    5  Extended
/dev/sda5           30280       30402      982016   82  Linux swap / Solaris

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1          2048 486430719  486428672  83  Linux
/dev/sda2     486432766 488396799    1964034   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     486432768 488396799    1964032  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

---

### Post by Blasphemist on 2011-09-27
The first 3 posts of this thread walk you though troubleshooting this for pretty much all causes. Most likely it is a video issue. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

It starts with some information and then goes into the troubleshooting flowchart.

---

### Post by Hakunka-Matata on 2011-09-27
OK, thanks.  Let's look at the boot process:
download, boot_info_script.sh (see signature)
run it and post the contents of the RESULTS.txt file that it will produce.  
Please.

---

### Post by Sandy000 on 2011-09-27
Hope I did this right...

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   486,430,719   486,428,672  83 Linux
/dev/sda2         486,432,766   488,396,799     1,964,034   5 Extended
/dev/sda5         486,432,768   488,396,799     1,964,032  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        817a43cb-ecfe-405e-9880-ac7f49de86fc   ext4       
/dev/sda5        2fca82cc-bf83-4cbf-8464-b032b48c72ec   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=817a43cb-ecfe-405e-9880-ac7f49de86fc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2fca82cc-bf83-4cbf-8464-b032b48c72ec none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 180.135231018 = 193.418731520  boot/grub/core.img                             1
 180.133281708 = 193.416638464  boot/vmlinuz-2.6.38-8-generic                  1
 180.133281708 = 193.416638464  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  74 83 58 7a b4 a0 22 81  cf 42 1b 4c 29 8d dd 15  |t.Xz.."..B.L)...|
00000010  db a1 bf cb 70 02 76 30  87 a5 5c 5c 38 5a 56 b1  |....p.v0..\\8ZV.|
00000020  1f a9 13 2a 8e 98 5a 1c  9b 5c 71 06 3a f0 9b 90  |...*..Z..\q.:...|
00000030  4c af 58 a9 64 1e 7b b5  e2 3c f8 05 15 97 20 6f  |L.X.d.{..<.... o|
00000040  21 16 2b 15 c7 de aa e8  a9 bc 7a 0c fb 98 4a 3e  |!.+.......z...J>|
00000050  b1 b3 ba e0 d8 69 4f 67  75 f9 b1 8f a1 4f 79 57  |.....iOgu....OyW|
00000060  2a 97 8e 5d ab b8 ce 76  6a 91 f7 9f 15 1b 78 2d  |*..]...vj.....x-|
00000070  1c 31 3d fc 51 37 71 c4  84 9f 7a ac dc a0 cc b8  |.1=.Q7q...z.....|
00000080  cf 5a d9 12 75 68 81 b7  ef fe e5 a1 46 95 ed 98  |.Z..uh......F...|
00000090  6f a7 92 4e 3b 75 ca 47  4d 2b 23 c2 53 1a c7 57  |o..N;u.GM+#.S..W|
000000a0  36 08 27 9d 23 a6 cd 1f  dd 5b 79 c4 74 e4 a3 8e  |6.'.#....[y.t...|
000000b0  90 a4 34 ee 0a 0b 7f fc  e8 91 ca 38 a4 36 aa 4c  |..4........8.6.L|
000000c0  46 4d 12 90 da f2 e3 01  90 77 fa f8 91 ca 76 90  |FM.......w....v.|
000000d0  0f ae ac 45 b9 23 2a 23  d8 72 03 0d 9f fc b8 51  |...E.#*#.r.....Q|
000000e0  65 03 35 9b 71 d2 c7 39  48 1d df a9 11 f0 79 e4  |e.5.q..9H.....y.|
000000f0  8a 50 17 01 af 73 6d af  2b 9f 7c 9c 5f d9 33 fc  |.P...sm.+.|._.3.|
00000100  cb 8f bb 89 eb 58 77 c5  95 09 28 d7 57 79 44 b6  |.....Xw...(.WyD.|
00000110  45 09 3b 6e 05 4f f2 64  ae c3 06 f1 f8 f1 29 95  |E.;n.O.d......).|
00000120  db 39 f5 8c 86 d4 c6 33  0a b5 e8 12 34 9f ad 1c  |.9.....3....4...|
00000130  09 0b b3 2a 2f 29 55 c7  1f a9 b4 21 d7 d9 a8 38  |...*/)U....!...8|
00000140  e3 92 e3 39 f0 8f 71 8d  5f ab 3c 8f 5c 0b 51 ff  |...9..q._.<.\.Q.|
00000150  49 f7 ad a8 74 22 75 6d  e5 7e b6 b3 9f fb aa b3  |I...t"um.~......|
00000160  fa fe f1 aa c2 04 f5 d8  f1 78 25 41 5d bc 03 3b  |.........x%A]..;|
00000170  9b fa c5 f1 15 68 4b 5c  e3 53 6c 0d 2b 3d fc ca  |.....hK\.Sl.+=..|
00000180  f1 46 95 a5 c8 fb 27 94  42 fd 76 49 69 76 c2 5a  |.F....'.B.vIiv.Z|
00000190  a9 40 a7 51 65 67 95 76  cb 38 85 7c 77 9c 42 3c  |.@.Qeg.v.8.|w.B<|
000001a0  cd 8d de 13 37 88 ca 13  b5 90 14 34 ae 2a dc af  |....7......4.*..|
000001b0  4c 3f d1 08 75 a6 f3 40  35 ec 0c 99 48 6b 00 fe  |L?..u..@5...Hk..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by Hakunka-Matata on 2011-09-27
Yes, you did it right.

[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

I suggest you do this procedure to reinstall grub2.
where ever it asks for sdXY use: sda1, and for sdX, use sda
skip step# 4, do step# 5, because you do have Grub 1.99

don't forget to do the sudo update-grub after reboot.

---

### Post by Sandy000 on 2011-09-27
No change after following the steps. :(

Tried to do sudo update-grub and got an error

```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.
```

---

### Post by oldfred on 2011-09-27
Your boot script is missing grub.cfg or the menu.

You cannot run the update-grub from a liveCD.

You can try manually booting or chroot into your system to repair it.

Manual boot.

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,1) or sda1
sh:grub>ls (hd0,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,1)/vmlinuz root=/dev/sda1
sh:grub>initrd (hd0,1)/initrd.img
sh:grub>boot

If that boots then run the 
sudo update-grub

Chroot:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Hakunka-Matata on 2011-09-27
ok, here's the first link I find talking about that particular error text, 

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009)

I'm going to keep looking a bit, but someone may well see that problem and jump it with the answer.  Betcha it isn't the first time it showed up?  Are you lucky?, or what?

**EDIT:  Thanks to oldfred**, the fix has likely been found, disregard the above, caveat: the link *is *about the error message that is generated by 'sudo update-grub'

---

### Post by Hakunka-Matata on 2011-09-27
> **oldfred said:**
> Your boot script is missing grub.cfg or the menu.

You cannot run the update-grub from a liveCD.

You can try manually booting or chroot into your system to repair it.

Manual boot.

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,1) or sda1
sh:grub>ls (hd0,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,1)/vmlinuz root=/dev/sda1
sh:grub>initrd (hd0,1)/initrd.img
sh:grub>boot

If that boots then run the 
sudo update-grub

Chroot:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Thanks oldfred, why am I not surprised?  Is the fact that /boot/grub/grub.cfg is not present in sda1, the reason this whole scenario presents?

---

### Post by Sandy000 on 2011-09-27
Thanks guys. :)
Can you please dummy the steps I need to take down for me? :p
I need the exact steps to take and where to put the info. Thank you 

Do I type this stuff on the grub page?
```
sh:grub>ls
#If on (hd0,1) or sda1
sh:grub>ls (hd0,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,1)/vmlinuz root=/dev/sda1
sh:grub>initrd (hd0,1)/initrd.img
sh:grub>boot
```

---

### Post by Hakunka-Matata on 2011-09-27
yes, that's right, from the **grub>** prompt

---

### Post by Sandy000 on 2011-09-28
Tried both the Chroot method and the manual boot.
I didn't notice any change after the Chroot.
The manual boot didn't work. Unfortunately I couldn't copy and paste so may have typed something wrong. I'll try again today. Thanks

---

### Post by Sandy000 on 2011-09-28
The manual boot doesn't work for me. 

First I don't see sh: grub>
My screen only reads grub>
Am I inputing the info in the right place? Do I have to type something to bring up the sh: grub> ?
Do I type sh: grub> after grub>?

Here's what I typed and the results....
```

grub>ls #If on (hd0,1) or sda1

(hd0)  (hd0,msdos5) (hd0,msdos1) (fd0)

grub>ls (hd0,1)/ #Should show the links vmlinuz & initrd.img

No such disk

grub>linux (hd0,1)/vmlinuz root=/dev/sda1

missing ')'

grub>initrd (hd0,1)/initrd.img

you need to load the kernel first

grub>boot

no loaded kernel 
```

Sorry if I'm doing something wrong, this is new to me. Thanks

---

### Post by oldfred on 2011-09-28
That it is grub not sh grub is ok.

everything after a # is a comment, perhaps grub's command line does not recognize comments, perhaps try without # & comment.
But the kernel line should have worked & I do not understand missing ) error?

Similar commands again do not type comment:

set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

If this does not work we can try chrooting into your install and updating.

---

### Post by Sandy000 on 2011-09-28
Thanks for the quick reply Oldfred. 
I will give it a try. :)

---

### Post by Sandy000 on 2011-09-28
I'm back. 
First try...

```
set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod

error: missing ')'
```

I had a space before the 1 and took it out on the next try and got rid of that error message.

```
set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro

Unknown command 'linux/vmlinuz'.

initrd /initrd.img

unknown command 'initrd/initrd.img


boot

no loaded kernel
```

I notice there looks like you have a space after linux and initrd so will try that next. ;)

---

### Post by Blasphemist on 2011-09-28
So lets step back a moment and go a step at a time. From the manual.
> grub> prompt: GRUB 2 loaded modules but was unable to find the grub.cfg file.

So lets see just what the grub environment is.
```
set
```
That will tell us what the initial state is. Let us know.
```
ls
```
Let's just make sure it is as it was. You got two drive,partition combinations. (hd0,1 and hd0,5)
Let's see what is found on both. This command is just list. So,
```
ls (hd,1)/
```
```
ls (hd,5)/
```
```
ls (hd,1)/boot
```
```
ls (hd,5)/boot
```
```
ls (hd,1)/boot/grub
```
```
ls (hd,5)/boot/grub
```
So now we'll know what is at root, in the /boot directory and in /boot/grub, on both partitions.

If you see /boot/grub/grub.cfg on one of the partitions, use this command next.
```
configfile (hdX,Y)/boot/grub/grub.cfg
```
If the configuration file is located, the GRUB 2 menu should appear and you should be able to choose a selection and boot. If the configuration file is not found, a message will be generated and you must enter the boot commands manually.

Let's stop there and see what has happened. Fred had you doing the next part and it is in the manual page but let's see what this much has told us.

---

### Post by Sandy000 on 2011-09-28
Hi Blasphemist
I will try your suggestions next. Thanks :)

Tried both sets of commands again, and got pretty much the same results on both...


In the first set an error found after
```
grub>initrd (hd0,1)
```
error: file not found

In the second set error was found after
```
initrd /initrd.img
```
error: file not found

Sounds like both are referring to the same file?

Then when I do the boot command, it runs through a page or two very quickly and seems to lock the keyboard with the caps lock and scroll lock flashing. Have to push the button to shut down.

Any way I noted some of the writing there....
(There were numbers before the writing but too many to note)
> 
VFS: Cannot open root device "Sda1" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Pid: 1, comm: Swapper Not tainted 2.6.38-8-generic #42-Ubuntu

Call Trace:
?panic+0x5c/0x157
?mount_block_root+0x1x2/0x25b
?handle_signal +0x130/0x1d0
?sys_mknod+0x2c/0x30
?mount_root+0x59/0x5f
?prepare_namespace+0x14e/0x192
?sys_access+0x25/0x30
?kernel_init +0x1b9/0x1c8
?kernel_init + 0x0/0x1c8
?kernel_thread_helper + 0x6/0x10

I'll wait to see if any of that sheds light on a problem before starting the steps in the last post. 
Thanks :)

---

### Post by oldfred on 2011-09-28
It has to know where root is at. So either the set root = line or on each line you need the (hd0,1) entry. There is a space after the first command and then no spaces. Often best to just copy & paste.

---

### Post by Sandy000 on 2011-09-28
Wish I could copy and paste but if I copy here and then I have to shut down to get to the grub with no disk, don't think there is a way to make the paste work? 

I'll go try it again and also do the steps Blasphemist suggested. 

Thanks, Please don't give up on me yet guys. :)

---

### Post by Hakunka-Matata on 2011-09-28
Boot Info Summary (post# 12) does not show a grub.cfg file in sda1, nor does it list it at the end where it listed the files loaded by grub and their sector locations on disk.  
Am I wrong to think attempting to boot from the grub>  prompt is futile, as there is no grub.cfg file to begin with.  
LiveCD boot, and do the chroot grub reinstall would be a good candidate for fixing this problem at this stage, no?

---

### Post by oldfred on 2011-09-28
Manual boot may work as you are just typing in the commands that are in the grub.cfg file. 

But chroot and full repair may be better.

Two other ways:


Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

and instructions on chroot.
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

chroot with screen shots:
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by Sandy000 on 2011-09-28
Ok Results first....

     Code:
     set

?5
Color_highlight=black/white
Color_normal=white/black
Pager=
Prefix=(hd0,1)/boot/grub
root=hd0,1

That will tell us what the initial state is. Let us know.
     Code:
     ls

(hd0) (hd0,msdos5) (hd0,msdos1) (fd0)

Let's just make sure it is as it was. You got two drive,partition combinations. (hd0,1 and hd0,5)
Let's see what is found on both. This command is just list. So,
     Code:
     ls (hd,1)/

No such disk

Ran as ls (hd0,1)
Partition hd0,1: Filesystem type ext 2 - Last modification time
2011-09-28 00:32:16 Wednesday, UUID 817a43cb-ecfe-405e-9880-ac7f49de86fc-
Partition start at 2048 - Total size 486428672 sectors

     Code:
     ls (hd,5)/
No such Disk

Ran as ls (hd0,5) 
Partition hd0,5: Not a known filesystem- 
Partition start at 486432768 Total size  1964032 sectors

     Code:
     ls (hd,1)/boot
changed to ls (hd0,1)/boot
System map- 2.6.38-8-generic abi-2.6.38-8-generic
Config_2.6.38-8-generic memtest86+.bin memtest86+_multiboot.bin.
Vmcoreinfo-2.6.38-8-generic vmlinuz-2.6.38-8-generic

     Code:
     ls (hd,5)/boot
no such disk

changed to ls (hd0,5)/boot
Unknown file system

     Code:
     ls (hd,1)/boot/grub
too much too list

     Code:
     ls (hd,5)/boot/grub
unknown file system

So now we'll know what is at root, in the /boot directory and in /boot/grub, on both partitions.

If you see /boot/grub/grub.cfg on one of the partitions, use this command next.

**Couldn't tell if cfg was there, couldn't read entire page, went too fast so ran below command any way...**
     Code:
     configfile (hdX,Y)/boot/grub/grub.cfg 
**Just says grub> aftewards**




Ok so I looked around a bit once I brought the system up on the disk. 
I can see there is a file called 249 GB File which has to be the installed file. 
It's too large to be the disk file. 

I clicked on the initrd.img file because that was the file that was supposed to be missing in the commands. 
This is the message I got...>  "The Link "initrd.img is Broken Move it to Trash?
This link cannot be used because its target "boot/initrd.img-2.6.38-8-generic doesn't exist."What was surprising is that I also looked for the grub.cfg file and found it in the 249 GB file?

---

### Post by Hakunka-Matata on 2011-09-28
> Manual boot may work as you are just typing in the commands that are in the grub.cfg file. 
That makes sense, thanks for clearing up any doubts about that.

---

### Post by oldfred on 2011-09-28
Ahh, but manual boot will not work if the files you are trying to boot are broken. I was trying to use the link which is updated with each new kernel and is a good short cut to type in. But if link is broken then the install has issues.

Can chroot into install and do repairs. Do not copy # or any comments after #

To chroot:
This is one set of commands:
sudo -i
mount /dev/sda1 /mnt
for i in dev proc sys usr; do mount --bind /$i /mnt/$i; done
cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot  /mnt

Chroot into system and run these commands:
#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda

More info:
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by Blasphemist on 2011-09-28
I've been out a while Sandy and now is about the end of the day here (MDT). That last message had a lot in it so do let us know how it is going. I'll be back on tmo.

---

### Post by oldfred on 2011-09-28
I will not be back until later tomorrow (Chicago time). Supposed to golf in the AM if weather is ok.

While we like to fix things and have spent days helping other do that, the other choice is just to reinstall. If you use manual install, you can often reinstall in about an hour. But if you have un-backed up data reinstall is not a choice until your data is recovered. (I am usually disappointed with those who come back and say they just reinstalled and it works. ;)

---

### Post by Sandy000 on 2011-09-29
Hi guys,
I've been offline all day til now as well so just getting to the replies. 
I will go try the suggestions Thanks :)

---

### Post by Sandy000 on 2011-09-29
Well I have bad news and I have good news.

Bad News: 
I tried the steps above and ended up so I couldn't even get the grub to come up, so I tried them again.
Only to get an error message that my disk was full something like 450GB since my hard drive is only 250GB something seemed way off. 

Good News: I decided to do a reinstall using the disk. (Erasing the other install.)
It took 20 minutes and here I am. :) 

Sorry Oldfred I gave it a good try before doing the reinstall. 


Thanks to all of you for your help.

---

### Post by Hakunka-Matata on 2011-09-29
Congratulations, Glad you did 'what ever it took':
Hopefully you feel the experience was worth it!, and welcome back to ubuntu.

---

### Post by oldfred on 2011-09-29
Glad it worked. Reinstall is ok if that works and you have no data not backed up. 

With Ubuntu sometimes reinstall is too easy. We will never learn how to fix it if everyone backs up well and just reinstalls. (I can reinstall, reload all programs, and restore data in about an hour.).:)

---

### Post by Sandy000 on 2011-09-30
> **Hakunka-Matata said:**
> Congratulations, Glad you did 'what ever it took':
Hopefully you feel the experience was worth it!, and welcome back to ubuntu.
 
Thanks Hakunka-Matata :)
Yes I do think the experience was worth it. I learned a lot in the process.
I hadn't even heard of a grub before. And I also learned how to use the terminal a bit. 
I think I will take the classes that I see listed on one of the pages here when I have the time. I enjoy learning. Thanks again for you help. :)

---

### Post by Sandy000 on 2011-09-30
> **oldfred said:**
> Glad it worked. Reinstall is ok if that works and you have no data not backed up. 
 
With Ubuntu sometimes reinstall is too easy. We will never learn how to fix it if everyone backs up well and just reinstalls. (I can reinstall, reload all programs, and restore data in about an hour.).:)
 
 
Thanks Oldfred. I actuallly didn't have any data because I lost everything when Windows Xp went crazy. I never did figure out what caused that so I was nervous that whatever it was might have been messing up Ubuntu as well. I'm very glad to have it up and running. :)
 
I see your point on trying to fix the issue first, probably part of the reason it didn't work is I'm a complete newbie so I had to learn everything from step one. 
I'm sure I made many mistakes. 
I feel I've picked up some knowledge though and will keep on learning more. 
Thanks agan for you help. :)

---

