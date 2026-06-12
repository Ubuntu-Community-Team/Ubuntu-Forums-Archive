---
title: "Installation can't find previous OS installed."
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by Rishap Sharma on 2010-08-12
I had been using ubuntu for quite a while.
But alas :(, I had to switch to WinXp when I started learning VS using its IDE.I installed Windows over Ubuntu wiping its grub.
I hoped I will repair grub when I would need to.
Now when I boot from Live CD to install grub it can't find the installation present.
Moreover,when I try to make a fresh installation it can't find any Operating System in the HDD and asks to format WHOLE.. hard disk to make partition table and continue installation.
Please help.:D
Thanks in advance!

---

### Post by MAFoElffen on 2010-08-12
> **Rishap Sharma said:**
> I had been using ubuntu for quite a while.
But alas :(, I had to switch to WinXp when I started learning VS using its IDE.I installed Windows over Ubuntu wiping its grub.
I hoped I will repair grub when I would need to.
Now when I boot from Live CD to install grub it can't find the installation present.
Moreover,when I try to make a fresh installation it can't find any Operating System in the HDD and asks to format WHOLE.. hard disk to make partition table and continue installation.
Please help.:D
Thanks in advance!
I'm trying to unsterstand this- I'm trying to follow.  You described that you either "had" or "now have" a multi-boot PC  with Ubuntu and Windows XP...  and somehow Windows XP installed over the first sector of the Hard disk right?

Let me get an understanding of that first... That affects what you need to do from there.  Also, how was your machine setup "before" that problem?

---

### Post by Rishap Sharma on 2010-08-13
Thanks first for replying.

Yes.
You have got it right.
I earlier had Ubuntu only.Then I installed Windows over it(in other disk drive,wiping grub loader).
Used Windows for a month and half.
Tried to boot from Live CD hoping it will be easy(I would just need to reinstall Grub2 Legacy! ) to start dual boot.
But alas,previous installed Ubuntu was nowhere to be found.
Fresh installation doesn't find any OS in computer(thought I m still using Windows) and no Partition table and tells me :
"HDD doesn't have any OS installed and you have two options 
1. Use complete HDD as one disk for Ubuntu
2. Make new partition table."
Both case will involve complete format.
I would like that Ubuntu installation somehow detects my previous installed Windows partition table and show me the earlier made ext4 disk ,so that I can continue with my installation and save my data both.
I hope I have explained myself better this time :D
Thank you very much again for sparing some time to reply.
Please reply soon,I want my hands on Ubuntu as soon as possible.

---

### Post by MAFoElffen on 2010-08-13
So... Sounds like you overwrote your previous install of Ubuntu...

Startup Windows and use the Disk Manager to resize/move your NTFS partition back one sector.  Grub is going to need this sector to install it's boot.  Windows OS'es like to run in the lower half of the disk.  Leave available space after that partition for Ubuntu to install.

If you boot up on a Gparted LiveCD (easiest way by my experience), add a ext4 partition (for (Ubuntu to install into) and a linux-swap partition (for Ubuntu to use for it's swap).  When you install, the install script will then see these existing partitions to use.  You nay have to go to manual mode to select them, but they will be "seen."

You can also add/change the partitions in manual mode from the install script , but that's confusing/harder to some people...  Either way, gparted does see the ntfs partition there.

The Ubuntu install script will then see and use those partitions... and have room to install and configure GRUB2 when it gets to that part of the install script.

Tell me how it goes.

Added in EDIT: Oh, I forgot... The "findos" routine in the grub-config script should find your Windows OS and add it to the GRUB2 menu (during that part of the install).  

Important note in the Grub config step- When asked where you want to install grub to, select the root of the device (example- sda or hd0), not a partition (example- sda1 or hd0,1).  If you do it wrong, you'll end up corrupting the boot sector of your Windows partition with the Grub boot loader...

---

### Post by Rishap Sharma on 2010-08-13
> **MAFoElffen said:**
> So... Sounds like you overwrote your previous install of Ubuntu...

Startup Windows and use the Disk Manager to resize/move your NTFS partition back one sector.  Grub is going to need this sector to install it's boot.  Windows OS'es like to run in the lower half of the disk.  Leave available space after that partition for Ubuntu to install.

If you boot up on a Gparted LiveCD (easiest way by my experience), add a ext4 partition (for (Ubuntu to install into) and a linux-swap partition (for Ubuntu to use for it's swap).  When you install, the install script will then see these existing partitions to use.  You nay have to go to manual mode to select them, but they will be "seen."

You can also add/change the partitions in manual mode from the install script , but that's confusing/harder to some people...  Either way, gparted does see the ntfs partition there.

The Ubuntu install script will then see and use those partitions... and have room to install and configure GRUB2 when it gets to that part of the install script.

Tell me how it goes.

Added in EDIT: Oh, I forgot... The "findos" routine in the grub-config script should find your Windows OS and add it to the GRUB2 menu (during that part of the install).  

Important note in the Grub config step- When asked where you want to install grub to, select the root of the device (example- sda or hd0), not a partition (example- sda1 or hd0,1).  If you do it wrong, you'll end up corrupting the boot sector of your Windows partition with the Grub boot loader...

Thank you for the reply.
I am sorry but being a novice I could not understand well what you guided me to.
What do you mean by "NTFS partition back one sector"?
Do you mean that I need to have a partition right next to my Windows partition for ubuntu? That means adjacent to C:\ in my case.
Moreover "findos" is not working as there is no grub installed !!!
I tried to use g-parted from the Live CD but it shows all of my Hard Disk 465 GB unallocated.

I am really thankful that you are responding but... 
Please reply soon.

I would like to add that I have four partitions for windows (other than Win OS) but in ubuntu Live CD it is showing only two.
But when it is atleast showing me a option to mount some drive that implies it knows I have drives .Having drives should have made install scipt to recognize OS (or atleast partitions size) but it is not like that ! :(

---

### Post by oldfred on 2010-08-14
Just to confirm what is installed where, from LiveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Rishap Sharma on 2010-08-14
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda9: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf284f284

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   767,039,489   767,039,427   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5                 189    40,001,849    40,001,661  85 Linux extended
/dev/sda6          40,001,913    83,891,429    43,889,517   7 HPFS/NTFS
/dev/sda7         137,885,965   347,598,404   209,712,440   7 HPFS/NTFS
/dev/sda8         347,598,468   557,310,914   209,712,447   7 HPFS/NTFS
/dev/sda9         557,310,978   767,039,489   209,728,512   7 HPFS/NTFS
/dev/sda2    *     83,891,493   137,885,894    53,994,402   7 HPFS/NTFS
/dev/sda3         767,039,490   976,751,999   209,712,510   7 HPFS/NTFS

/dev/sda1 overlaps with /dev/sda2

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        9A2C58482C582215                       ntfs       Windows                       
/dev/sda3        7C5CCE015CCDB664                       ntfs       Softwares                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sda7


Unknown BootLoader  on sda8


Unknown BootLoader  on sda9



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda8: No such file or directory
hexdump: /dev/sda8: No such file or directory
hexdump: /dev/sda9: No such file or directory
hexdump: /dev/sda9: No such file or directory
```I am happy to see that the script recognized my partitions ( all of them) and OS too.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
Description of my Partitions :
 hd2 : using for windows;
hd3,hd9,hd8,hd7 : using to store data on Windows OS
hd5 : earlier installed Ubuntu on this partition (now grub wiped out by windows ) and now neither recognizing in "Places Menu" and nor mounting.
hd6 : Backup for Windows 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Please tell me what next I should do?
Thanks for sparing time to reply.

---

### Post by oldfred on 2010-08-14
The script was not able to parse all the partitions because of this:

/dev/sda1                  63   767,039,489   767,039,427   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5                 189    40,001,849    40,001,661  85 Linux extended

You can have only one extended partition and partitions cannot overlap. I would try testdisk which is one most recovery CDs or can be downloaded into the Ubuntu liveCD:

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by MAFoElffen on 2010-08-14
How was this hard disk setup before you installed Windows XP and when you installed XP- how diid you install (your intention or plan/what you where intending to do)?  It looks like you possibly "were" trying to keep both OS'es on... but somewhere in the process the partition table got corrupted.

Well, there's a lot more going on here than that, but this is what I see staring out at me:  
- The start of sda1 is at 63 and ends at the "same ending point" as sda9= a very big overlap...  The script says it overlaps with sda2, but it actually overlaps with sda2, sda6, sda7, sda8 and sda9!!!
```

=============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf284f284

Partition  Boot         Start           End          Size  Id System

/dev/sda1                [COLOR=Lime]  63[/COLOR]   [COLOR=Red]767,039,489[/COLOR]   767,039,427   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5                 189    40,001,849    40,001,661  85 Linux extended
/dev/sda6          40,001,913    83,891,429    43,889,517   7 HPFS/NTFS
/dev/sda7         137,885,965   347,598,404   209,712,440   7 HPFS/NTFS
/dev/sda8         347,598,468   557,310,914   209,712,447   7 HPFS/NTFS
/dev/sda9         557,310,978   [COLOR=Red]767,039,489[/COLOR]   209,728,512   7 HPFS/NTFS
/dev/sda2    *     83,891,493   137,885,894    53,994,402   7 HPFS/NTFS
/dev/sda3         767,039,490   976,751,999   209,712,510   7 HPFS/NTFS

/dev/sda1 overlaps with /dev/sda2

```It seems to report sda2 and sda3 as okay for XP... The script reports that you have 6 boot loaders on this disk?  sda2 is XP,  sda5 was the old Ubuntu partition.  I'm thinking that the other four it see's as "unknown" are that maybe when you defined the partitions for [COLOR=Red]sda6, sda7, sda8 and sda9[/COLOR] as active/primary partitions and not really actual boot loaders...  Is this right?
```

Unknown BootLoader  on sda5    [COLOR=Lime]<-- Im' guessing this was where Ubuntu's sys was loaded(?)[/COLOR]
Unknown BootLoader  on sda6                [COLOR=Red]<------+---  Are these set as primary partitions?[/COLOR]
Unknown BootLoader  on sda7                [COLOR=Red]<------+[/COLOR]
Unknown BootLoader  on sda8                [COLOR=Red]<------+[/COLOR]
Unknown BootLoader  on sda9                [COLOR=Red]<------+[/COLOR]

```I editted this:
```
Description of my Partitions :
 sda2 : using for windows;
sdad3,sda9,sda8,sda7 : using to store data on Windows OS
sda5 : earlier installed Ubuntu on this partition (now grub wiped out by  windows ) and now neither recognizing in "Places Menu" and nor mounting.
sda6 : Backup for Windows 

```Curious- Was sda1 the old linux-swap?

Well then... Can you answer those questions?  Theres is an easy plan and a hard plan to fix this based on your answers.  I'll wait for them...

---

### Post by MAFoElffen on 2010-08-14
@ oldfred- Looks like we saw the same thing at the same time!  Do you see the other abnormallities there or am I reading too much into that?  I'm wondering if he also has more than 4 primary partitions...

---

### Post by oldfred on 2010-08-14
There seems to be a lot of overlap, hopefully testdisk can sort it out.

I am not too concerned out unknown boot loaders. When the start of the  partition or boot sector contains unerased data the script sees that as a boot loader. It may be just old data from when partitions were moved.

---

### Post by presence1960 on 2010-08-14
I am concerned about the overlapping of partitions and the message that sda1 which is an extended partition links to another extended partition. If your windows on sda2 boots fine I would boot from the ubuntu Live CD. Boot to the desktop and use gparted to delete sda5 thru sda9- one at a time. Then delete sda1. When that is completed examine the graphic representation of your hard disk and make sure the only two partitions are sda2 & sda3. They should have a green border around them which signifies the NTFS file system. Everything else should be grey and labeled unallocated

If the only two partitions that exist on your hard disk are those two then reinstall ubuntu. Personally I prefer to set up the partitions prior to the install but that is not necessary as you can choose to install Ubuntu to the unallocated space.

Your partition table is really fouled up. Hopefully you can remove the offending partitions and install ubuntu without having to wipe your hard disk. I know testdisk may be of help here but I am not well versed with testdisk. Maybe meierfra will see this and chime in. He is really good with this kind of stuff.

---

### Post by presence1960 on 2010-08-14
Before trying to remove sda5 thru sda9, then sda1, try this:

Boot from the ubuntu live cd. Boot to the desktop. Open a terminal and run ```
sudo e2fsck /dev/sda -y -f -v -c
```

See if that fixes the problem.

---

### Post by Rishap Sharma on 2010-08-15
Thank you for replying.

I had earlier three partitions for different OS : WinXP,Win7,Ubuntu (having 20,25,20 GB storage space).
Then as the internet in Win7 was showing problems I inserted the WinXP installation disk and chose the Win7 drive for format and install of WinXP (fresh).
Then I formatted the earlier WinXP drive. Hoping that I would be able to merge this 20 GB space into WinXP and Ubuntu( 10 GB each)and for that I used "Acronis Disk director".
Then I did some things(I can't remember) to make 4 partitions as 100 GB each and 25 GB WinXP ,20 GB Backup for windows and Ubuntu hidden(Grub Wiped)..
This is it! :)

I know I should have been more cautious while partitioning !! 
But...now even when I try to "Install Ubuntu inside Windows" it does fine.But when computer reboots it shows me two options to boot into " Windows XP " and "Ubuntu"
Hitting enter leads me to black screen having :
```

GNU GRUB Version 1.98 -Ubuntu 5
Minimal Bash-like line editing is supported.For the first word ,TAB lists possible commands completions.

>GRUB 
```

---

### Post by Rishap Sharma on 2010-08-15
Yes I used a drive as swap space for my Ubuntu..
And unfortunately I chose that to be windows drive..
Then windows didn't booted and I had to retort to install that again in the same drive.

---

