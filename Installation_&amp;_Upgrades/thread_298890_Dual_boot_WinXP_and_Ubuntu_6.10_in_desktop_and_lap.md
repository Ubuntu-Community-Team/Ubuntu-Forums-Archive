---
title: "Dual boot WinXP and Ubuntu 6.10 in desktop and laptop using NTLDR"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by WOT on 2006-11-13
Hi guys,

I’ve encountered some problems with dual-boot installation of WinXP and Ubuntu in my desktop and laptop PCs. I searched a bit in internet and this forum, haven’t found any information useful yet so I really hope that you guys can give me a hand on that.

I know, I know, why bother Windows at all as some of you might ask. No offence to you “REAL LINUXERS” :p  , I’m a newbie and just started to learn the way around, so I decide to use NTLDR as boot loader in case something goes wrong then I done have to reinstall windows, which is a pain in the ***.:p 

I’ll give the details below of how I did it and what the problems are. I have to ask for your patience since it might be a tedious description. Any suggestion is welcome. Many thanks in advance. :D 

1. Desktop

I’ve got 2 disks, 160G each, set as following:

First disk:

1st partition K: hidden partition in format FAT32, 3.6G, where recovery files are located. Strangely enough, boot.ini is there too instead of in C: disk. Default setting. I’ve changed nothing since I bought the PC.
2nd partition C: windows XP, NTF partition, 100G.
3rd partition D: NTF, 56G.  For data backup.

Second disk:

1st partition: 30G, ext3, as /
2nd partition: 30G, ext3, as /home
3rd partition: 38G, FAT32, as /media/winlinux, for share files between these 2 systems.
4th partition: 2G, as swap
5th partition: 60G, NTF. Extra space for windows.

I have windows in C and Ubuntu (6.10 DVD) installed in 2nd disk. During the Grub installation, I changed default “hd (0)” to “hd(1)”. Hope that’s correct. (or should I type “/dev/sdb1” or something like that? ) 

anyway, I boot into windows, use “bootpart” to make a “ubuntu.bin” and put it into 1st partition K in 1st disk, then manually edit boot.ini, add “K:\ubuntu.bin=”Ubuntu 6.10”” at the end. (According to the guide I found in internet, bootpart should do this job for me. But I checked my boot.ini, no change, have to manually edit it. Don’t know why. :-( )

restart PC and I DO see the NTLDR screen and I’m able to choose Window or Ubuntu. 

However, when I choose Ubuntu, I got an error message saying that the “hal.dll” file in system32 is missing or damaged and asked me to reinstall it. I checked the file in windows\system32, it’s there, safe and sound. 

I tried to locate ubuntu.bin in different places and edit boot.ini accordingly but none of them worked. 

Have I done something wrong during installation? Where? So how should I do to solve this problem WITHOUT REINSTALL WINDOWS? By the way, I can boot into window perfectly. 

2. laptop.

Only 1 physical disks, 100G, in my Dell Inspiron 9300.

Disk set as:

1st partition C: winXP, 50G
2nd partition D: NTF, 20G,
3rd partition E: 10G, FAT32, for share files as /media/winlinux
4th partition: 15G, ext3 as /
5th partition: 3G, ext3 as /home
6th partition: 2G swap

Due to the problem I’ve had in desktop, I need to ask before I install ubuntu into my laptop. During the installation step of Grub, default hd(0), I guess that means Grub will be write into MBR, so what should I type instead? Hd(0,4)? Or /dev/sda7? Guess 4th partition is sda7. 

Once again, I’m open to any advice or suggestion. Thanks a lot, guys.  


1. Desktop

I’ve got 2 disks, 160G each, set as following:

First disk:

1st partition K: hidden partition in format FAT32, 3.6G, where recovery files are located. Strangely enough, boot.ini is there too instead of in C: disk. Default setting. I’ve changed nothing since I bought the PC.
2nd partition C: windows XP, NTF partition, 100G.
3rd partition D: NTF, 56G.  For data backup.

Second disk:

1st partition: 30G, ext3, as /
2nd partition: 30G, ext3, as /home
3rd partition: 38G, FAT32, as /media/winlinux, for share files between these 2 systems.
4th partition: 2G, as swap
5th partition: 60G, NTF. Extra space for windows.

I have windows in C and Ubuntu (6.10 DVD) installed in 2nd disk. During the Grub installation, I changed default “hd(0)” to “hd(1)”. Hope that’s correct. (or should I type “/dev/sdb1” or something like that? ) anyway, I boot into windows, use “bootpart” to make a “ubuntu.bin” and put it into 1st partition K in 1st disk, then manually edit boot.ini, add “K:\ubuntu.bin=”Ubuntu 6.10”” at the end. (According to the guide I found in internet, bootpart should do this job for me. But I checked my boot.ini, no change, have to manually edit it. Don’t know why. :-( ) restart PC and I DO see the NTLDR screen and I’m able to choose Window or Ubuntu. 

However, when I choose Ubuntu, I got an error message saying that the “hal.dll” file in system32 is missing or damaged and asked me to reinstall it. I checked the file in windows\system32, it’s there, safe and sound. 

I tried to locate ubuntu.bin in different places and edit boot.ini accordingly but none of them worked. 

Have I done something wrong during installation? Where? So how should I do to solve this problem WITHOUT REINSTALL WINDOWS? By the way, I can boot into window perfectly. 

2. laptop.

Only 1 physical disks, 100G, in my Dell Inspiron 9300.

Disk set as:

1st partition C: winXP, 50G
2nd partition D: NTF, 20G,
3rd partition E: 10G, FAT32, for share files as /media/winlinux
4th partition: 15G, ext3 as /
5th partition: 3G, ext3 as /home
6th partition: 2G swap

Due to the problem I’ve had in desktop, I need to ask before I install ubuntu into my laptop. During the installation step of Grub, default hd(0), I guess that means Grub will be write into MBR, so what should I type instead? Hd(0,4)? Or /dev/sda7? Guess 4th partition is sda7. 

Once again, I’m open to any advice or suggestion. Thanks a lot, guys.

---

### Post by Herman on 2006-11-13
Why not give WinGrub a try? [http://grub4dos.sourceforge.net/](http://grub4dos.sourceforge.net/)

You just download the installer for it and double-click on it to install.
In 'Base Setup, Choose to install it to drive C.
Go 'Tools'-->'install Grub',--> system drive C boot, select radio button for boot from boot.ini.

Then insert the following line in boot.ini, C:\GRLDR="Start Grub"
```
C:\GRLDR="Start Grub"

```
You will not be able to boot Ubuntu with WinGrub without first hashing out or deleting the 'savedefault' commands in your operating system entries in /boot/grub/menu.lst, but as soon as you do that it will work great. ;) 

It's an older version of Grub, but at least you will still have all your Grub functions and it is very reliable. You can even delete OS's and add new ones and WinGrub will automatically find them and boot. You will still be using Grub, but it will be based in your Windows partition.
You still need Grub in your Ubuntu partition for it to work, (it won't work if you only have Lilo, but that wouldn't apply to many people nowadays).

Regards, Herman

---

### Post by doremi on 2007-01-18
> **Herman said:**
> 
You will not be able to boot Ubuntu with WinGrub without first hashing out or deleting the 'savedefault' commands in your operating system entries in /boot/grub/menu.lst, but as soon as you do that it will work great. ;) 
Hi, can you explain a bit how to do that? 

Also through this way if I want to stop using Ubuntu I just delete the entry in boot.ini and the comp will auto boot into windows on restart?

Also can I put grub on the ubuntu partition with the livecd version or do i need the alternate install version?

---

### Post by Herman on 2007-02-02
>  Also can I put grub on the ubuntu partition with the livecd version or do i need the alternate install version? Hello doremi,
I have read other posters here in Ubuntu Forums saying that you can now direct the 'Desktop' CD installations where you want Grub to be installed. It is in the next window after partitioning I think, there is a line about half way down the window that says 'install Grub to:' (followed by a small rectangular button '(hd0)' printed in it. You can click on that button to get a slighly bigger text box you can type into and specify where you want Grub installed.
> Also through this way if I want to stop using Ubuntu I just delete the entry in boot.ini and the comp will auto boot into windows on restart?
 In a word, Yes. 
...As long as you are careful with what you are doing with boot.ini, it's kind of a finicky file to edit. You can lose you boot if you make a mistake. I recommend having a Windows boot floppy disk on hand, here's one you can make yourself. [Click Here]("http://support.microsoft.com/kb/305595/EN-US/") It has it's own copy of NTLDR NTDetect and boot.ini files on the floppy disk. Since the floppy disk is FAT32, you can edit the floppy disk's boot.ini from Linux as needed to boot an otherwise unbootable Windows installation, in case you make any errors in your hard disk installed boot.ini.
> Quote:
                                                                      Originally Posted by **Herman**                     [[IMG]http://ubuntuforums.org/images/uf/buttons/viewpost.gif[/IMG]]("http://www.ubuntuforums.org/showthread.php?p=1752990#post1752990")                 
                 *You will not be able to boot Ubuntu with WinGrub without first hashing out or deleting the 'savedefault' commands in your operating system entries in /boot/grub/menu.lst, but as soon as you do that it will work great. :wink:*
                                 
Hi, can you explain a bit how to do that?  Sure, here, click on this link following: [GRUB Boot Loader Page]("http://users.bigpond.net.au/hermanzone/p15.htm")
That page will explain to you, with illustrations, about all I know about editing Ubuntu's /boot/grub/menu.lst file, in the simplest possible terms so everyone can understand it, (I hope). :)
Now, to be specific, you find your Linux (Ubuntu) entries near the bottom of your /boot/grub/menu.lst, and they will look a bit like this, (below)...
```
## ## End Default Options ##
                                              
 title        Ubuntu, kernel 2.6.15-25-386
 root        (hd0,1)
 kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
 initrd        /boot/initrd.img-2.6.15-25-386
 savedefault
 boot
                                                            
  title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
  root        (hd0,1)
  kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
  initrd        /boot/initrd.img-2.6.15-25-386
  boot
                                                            

  title        Ubuntu, memtest86+
  root        (hd0,1)
  kernel        /boot/memtest86+.bin 
  boot

 ### END DEBIAN AUTOMAGIC KERNELS LIST
                                                            
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
                                                            
                                                            
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
``` Now, what you need to do to make your system bootable by WinGrub, is to 'hash out' the lines with the 'savedefault' command. A hash mark looks like this: #
The hash mark, placed before the line makes the computer ignore that line, and a line like that is known as a 'comment'. (You can type anything there you want, comments and things you want to remember about the program maybe).
This is needed for WinGrub, becuase it uses an older version of Grub than Ubuntu, and does not recognize the 'savedefault' command, so that makes WinGrub freeze up.
By 'hashing out', or 'commenting' the 'savedefault' commands, WinGrub will skip those lines, and will be abale to boot up any operating system in the Ubuntu's Grub menu. For example, your Ubuntu /boot/grub/menu.lst file's operating system entries should now look something like this,
```
## ## End Default Options ##
                                                            
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
# savedefault
boot
                                                            
title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot
                                                            

                                                            
title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
                                                            
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
                                                            
                                                            
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
# savedefault
makeactive
chainloader    +1
``` Now, you can boot with WinGrub. See the hash marks in front of the 'saveddefault commands? That's all you need to do.

I hope that helps, sorry about the late reply, I just got home this week from a working holiday (driving tractor-trailers for a vacation). 
Regards, Herman :)

---

