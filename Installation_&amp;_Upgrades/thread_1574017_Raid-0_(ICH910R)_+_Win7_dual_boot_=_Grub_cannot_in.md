---
title: "Raid-0 (ICH9/10R) + Win7 dual boot = Grub cannot install"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by devoluti0n on 2010-09-13
Hi mates.
First, I'm sorry for my bad english, I'll try to do my best.
As I didn't have helping answers from the french community I decided to come here :).

I'm having serious troubles to install ubuntu-10.04.1.
My raid is an hardware raid with intel chipset.

Note that win7 is already installed and working with my raid.
I made some space from windows, to install Ubuntu (40gb).

First, I run the installer, everything seems to be fine.
I choose to install Ubuntu were there is the most space free (sorry, I'm not sure about the real terms used there).

Then my partition with the vista loader appears. So the installer can see my raid, and should work fine (everything is detected correctly).

But once I'm in the end of the installation (around 95%), a pop-up appears, and tells me that Grub can't install in /dev/sda and it's a fatal error.

I can choose an another destination, but it doesn't seems to work.

What did I miss ? I hope you will find an answer, thanks in advance ! :)

---

### Post by ronparent on 2010-09-13
Grub cannot install to /dev/sda2 if it is one of the disks in raid and it is fatal only if you don't fix it. You need to reinstall grub as given in the following: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Some comments to help. In /dev/mapper you will find listed all the symbolic links - the raid followed by all its individual partitions (ignore control). The partition you are trying to mount from the live cd is the symbolic link for the raid partition you installed to - ie /dev/mapper/<yourinstallpartitionRAID#>. The location you are trying to place the grub boot loader on is the raid name. 

Post if you need more information. Good luck.

---

### Post by devoluti0n on 2010-09-13
Thank you for your answer, but I'm totally lost. I'm actually installing Linux for the first time so my knowledge is very small.

-Do I need to install it from the live CD as I did before ? And then, when the error show up, I select the option to not install Grub. This is it ?
-Then I have to install it manually as written in your link ?

And what I don't understand in your message, is this part : 
> In /dev/mapper you will find listed all the symbolic links - the raid followed by all its individual partitions (ignore control) Theses links are links to my individuals hdd arn't they ?
So this mapping is the symbolic name of my raid, isn't it ?

> The partition you are trying to mount from the live cd is the symbolic  link for the raid partition you installed to - ie  /dev/mapper/<yourinstallpartitionRAID#>

> The location you are trying to place the grub boot loader on is the raid nameWhat do you mean ? That I'm not aiming the raid by choosing "/dev/mapper/<MyInstallpartitionRAID#>" but only his symbolic name ?

If so, how can I make it aim the raid correctly ?

Thanks for your help, and again, I'm really sorry for my bad english =).

---

### Post by ronparent on 2010-09-13
Go to this site: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

There you will find a downloadable and executable Boot Info Script. Follow the instructions on the site to run it and post the results here. It will give us enough information about your system so that we can better tell you how to fix it.  

In windows you would never expect to work directly with you raid. Win 7 especially recognizes it and automatically installs the drivers so that you can use your disks in a raid. In linux, instead of a driver, a program called dmraid fill the same purpose. With 10.04 on the process becomes more automatic. Unfortunately there are still some things you have to do to overcome some of the shortcomings that still exists. This requires you to learn more about how raid works in your system.

One of these shortcomings is that the 10.04.1 installer often doesn't properly install the grub 2 bootloader which you need to select and load any program on you computer. This is fixable and what we have to fix. The results from running the boot info script will provide enough information so that we can guide you in fixing it. Have you read any part of the  grub2 documentation I pointed you to?

---

### Post by devoluti0n on 2010-09-14
Okay, I'm back and ready to try all this.
I'm booting to my linux live cd right now and executing this script.
I'll post my results once I'll have reinstalled ubuntu.

---

### Post by devoluti0n on 2010-09-14
Here is the RESULTS.txt content :
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sdc

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

mapper/isw_bafdiffaia_Red: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8462 MB, 8462008320 bytes
255 heads, 63 sectors/track, 1028 cylinders, total 16527360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    16,527,359    16,527,297   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_bafdiffaia_Red1 08F44145F44135EA                       ntfs       Réservé au système         
/dev/mapper/isw_bafdiffaia_Red2 F2A6429AA6425F6B                       ntfs                                     
/dev/mapper/isw_bafdiffaia_Red 51f72bcf-1e26-ca80-c1a0-ede2371d3b6b   linux_raid_member                               
/dev/mapper/isw_bafdiffaia_Red5 574bf494-7397-4964-9721-cb792f76eaa5   ext4                                     
/dev/mapper/isw_bafdiffaia_Red6 51f72bcf-1e26-ca80-c1a0-ede2371d3b6b   linux_raid_member                               
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        4E39-62B5                              vfat       MYLINUXLIVE                   
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_bafdiffaia_Red
isw_bafdiffaia_Red1
isw_bafdiffaia_Red2
isw_bafdiffaia_Red3
isw_bafdiffaia_Red5
isw_bafdiffaia_Red6

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on mapper/isw_bafdiffaia_Red

00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1c fe  |.v..N..n...fas..|
000000a0  4e 11 75 0c 80 7e 00 80  0f 84 8a 00 b2 80 eb 84  |N.u..~..........|
000000b0  55 32 e4 8a 56 00 cd 13  5d eb 9e 81 3e fe 7d 55  |U2..V...]...>.}U|
000000c0  aa 75 6e ff 76 00 e8 8d  00 75 17 fa b0 d1 e6 64  |.un.v....u.....d|
000000d0  e8 83 00 b0 df e6 60 e8  7c 00 b0 ff e6 64 e8 75  |......`.|....d.u|
000000e0  00 fb b8 00 bb cd 1a 66  23 c0 75 3b 66 81 fb 54  |.......f#.u;f..T|
000000f0  43 50 41 75 32 81 f9 02  01 72 2c 66 68 07 bb 00  |CPAu2....r,fh...|
00000100  00 66 68 00 02 00 00 66  68 08 00 00 00 66 53 66  |.fh....fh....fSf|
00000110  53 66 55 66 68 00 00 00  00 66 68 00 7c 00 00 66  |SfUfh....fh.|..f|
00000120  61 68 00 00 07 cd 1a 5a  32 f6 ea 00 7c 00 00 cd  |ah.....Z2...|...|
00000130  18 a0 b7 07 eb 08 a0 b6  07 eb 03 a0 b5 07 32 e4  |..............2.|
00000140  05 00 07 8b f0 ac 3c 00  74 09 bb 07 00 b4 0e cd  |......<.t.......|
00000150  10 eb f2 f4 eb fd 2b c9  e4 64 eb 00 24 02 e0 f8  |......+..d..$...|
00000160  24 02 c3 49 6e 76 61 6c  69 64 20 70 61 72 74 69  |$..Invalid parti|
00000170  74 69 6f 6e 20 74 61 62  6c 65 00 45 72 72 6f 72  |tion table.Error|
00000180  20 6c 6f 61 64 69 6e 67  20 6f 70 65 72 61 74 69  | loading operati|
00000190  6e 67 20 73 79 73 74 65  6d 00 4d 69 73 73 69 6e  |ng system.Missin|
000001a0  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
000001b0  65 6d 00 00 00 63 7b 9a  42 ce d1 c7 00 00 80 20  |em...c{.B...... |
000001c0  21 00 07 df 13 0c 00 08  00 00 00 20 03 00 00 df  |!.......... ....|
000001d0  14 0c 07 fe ff ff 00 28  03 00 00 48 53 35 00 fe  |.......(...HS5..|
000001e0  ff ff 05 fe ff ff fe 71  56 35 02 18 e2 04 00 00  |.......qV5......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Hoping you can help me with it :)
Oh and I forget to say that the 8gb partition is my usb key, on which I'm running the actual live ubuntu.
It seems to be the sdc drive.
I'm afraid we can only see boot information from this key. Or maybe I'm (certainly ?) wrong.

Edit 2 : In Gparted, it only see /dev/sda  - /dev/sdb and /dev/sdc.
Which are : My raid hdd1 and hdd2, and my ubuntu usb live key. No raid is detected here.

Edit 3 : Okay, this is what I tried :
- sudo mount /dev/mapper/isw_bafdiffaia_Red5 /mnt
- sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_bafdiffaia_Red5

But here is the output of this last command :
> You have a memory leak (not released memory pool):
 [0x253c1e0]
You have a memory leak (not released memory pool):
 [0x24941e0]
You have a memory leak (not released memory pool):
 [0x1585be0]
You have a memory leak (not released memory pool):
 [0x19ccbe0]
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
You have a memory leak (not released memory pool):
 [0x1c65c00If we forget the memory leak cause we don't really care here, it suggests to isntall Grub to the MBR, how can we do that please ?

I also tried with : "sudo grub-setup -d /media/574bf494-7397-4964-9721-cb792f76eaa5/boot/grub /dev/mapper/isw_bafdiffaia_Red5"
Same error as before.

So I used the --force argument.
Then if I want to use : sudo update-grub , it says : cannot find a device for / (is /dev mounted?)
same for : sudo grub-mkconfig -o /media/574bf494-7397-4964-9721-cb792f76eaa5/boot/grub/grub.cfg
And I'm sure it is mounted (/dev/mapper/isw_bafdiffaia_Red5 is mounted)

---

### Post by ronparent on 2010-09-14
The correct command should have been:

sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_bafdiffaia_Red

Remember, the boot leader has to be written to the name that represent the entire array.

You just about got it on your own - congratulation. With this one fix you ought to be able to boot. Don't forget to mount your partition first.

---

### Post by devoluti0n on 2010-09-14
Thanks man, I'm giving a try :).

---

### Post by devoluti0n on 2010-09-14
"installation finished". This mean that it worked like a charm this way

But I still can't write :

"sudo update-grub" : 

> ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
I tried to remount it :
> 
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_bafdiffaia_Red5 /mnt
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).



---

### Post by ronparent on 2010-09-14
You should run up-date grub booted to your hard disk. Or, maybe, try 'sudo update-grub /mnt'?

---

### Post by devoluti0n on 2010-09-14
> **ronparent said:**
> You should run up-date grub booted to your hard disk. Or, maybe, try 'sudo update-grub /mnt'?

sudo update-grub /mnt doesn't work, I already tried.

Maybe it's because my English is bad, but I don't understand the first part of your sentence, :(, sorry.
Now when my computer boot, I have a Grub prompt, and that's it. I don't know what to do with it. it's because there is no os list to load.

GOT IT !!! :D

Here is what I did : 
I rebooted (not sure if it was necessary)

then I typed :

> Mount your partition[FONT=monospace]
[/FONT]sudo mount --bind /dev /mnt/dev[FONT=monospace]
[/FONT]sudo mount --bind /proc /mnt/proc[FONT=monospace]
[/FONT]sudo mount --bind /sys /mnt/sys[FONT=monospace]
[/FONT]sudo chroot /mnt[FONT=monospace]
[/FONT]dpkg-reconfigure grub-pc


Then I followed what was asked me on this new screen. I didn't change anything in it (except that I choose my raid in the list) .
Then I rebooted, and voilà, all my partitions are now bootable.

You deserve the golden medal of the year for your patience. Thanks a lot :).

---

### Post by ronparent on 2010-09-14
Great to hear it has worked out for you. Have fun.

---

### Post by Fix99 on 2011-05-15
Dear all,  I  have  the  exactly  same problem, I had  a 9.10 Ubuntu on my red0 machine  with raid0 Jmicron HW controller. I upgrade  to  10.04LTS  and  the  machine  don't boot.
I try all the tests prposed  by  devoluti0n &  ronparent grub 2 install works until  where  I  have  to install:
 sudo grub-install --root-directory=/media/UUID_nb  /media/UUID_nb
here  it answer  invalid  location .....:confused:
The  script works  bu I can't see the  result.....:confused:



Could  you  help me ?

Sorry my poor english.

---

