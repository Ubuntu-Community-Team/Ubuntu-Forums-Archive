---
title: "Dual boot Ubuntu Win, Win dont recognize partition"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Dojan5 on 2008-02-24
Hello!
Finally i got a functional CD with WinXP PRO.
I have Ubuntu 7.10 installed and i would want to Dual-Boot.
The problem is that the thing i use as a boot disk don't recognize the FAT32 Partition.
This i found very strange since it is a HUGE partition.
I do have the option to set-up my old 6gb harddrive with WinXP installed and try to install winXP on the new partition and blah.
But, as said, XP dont recognize the Partition and the boot is located in the RAM as C:
Please help
/
Joel

---

### Post by Pumalite on 2008-02-24
XP needs ntfs.

---

### Post by Dojan5 on 2008-02-24
Oh yaa...
And when using the XP CD it just continue to GRUB...
AND i have edited the boot thingy to boot first from CD then Floppy then HDD...
I seriously find this weird.
Thanks

---

### Post by Dojan5 on 2008-02-24
> **Pumalite said:**
> XP needs ntfs.

No it don't, or does it?
When i had Win98SE i had fat32 and then i installed XP on that.
But, i didnt have NTFS til i changed that later.
And then my second 1gb hdd still had Fat32....

---

### Post by Pumalite on 2008-02-24
You ideally should have XP installed first in sda1, Ubuntu last.

---

### Post by Dojan5 on 2008-02-24
> **Pumalite said:**
> You ideally should have XP installed first in sda1, Ubuntu last.

Great...
I have four partitions...
/dev/hda1 --- Linux Installation
/dev/hda2 --- Windows Partition (Round 93gb FAT32)
/dev/hda3 --- Linux Swap 15gb (:lolflag:)
/dev/hda4 --- Linux Home Directory

Hmm, i could move the partitions with GParted in Live CD, right?

=-=-EDIT-=-=
Nope, cant move it that way...
Hrrm, either it is reinstalling ubuntu on different partition or try and format the Fat32 partition and see if it recognize it as a NTFS...
Ill try the last since it is empty and i rather not re-install Ubuntu for something as Craposoft Windozer.

---

### Post by Pumalite on 2008-02-24
I agree; you are better off without Micro&%$

---

### Post by Dojan5 on 2008-02-24
Nope...
It didnt work...
I wish i didnt have the need for this DARN idiotic Windoze stuff like Visual Studio.
But, unfortunatley...
Anyhow, this is what happens, AND it is NTFS now.
Starts up:
Im checking whats going first, CD is as boot...
Restarts:
Black screen
Flicker
Black screen as with a command line thingy
GRUB Loading stage 1
Press ESC to show booting menu
countdown

Nothing...
Only Ubuntu, if i show the menu, Ubuntu Memtest and Failsafe
If not doing anything, Ubuntu boots....

Im beginning to wonder if installing Win98 first will solve my problem, i mean like using the XP cd when 98 is installed and install on desktop you get what i mean...
Thanks
> **Pumalite said:**
> I agree; you are better off without Micro&%$
Yaa, but i need to use DreamWeaver and Visual Studio and so on, i use a program called (X)HTML kit from Chami and im dependent on it.
And i have missed playing the Sims too XD, but it is still this thing called DreamWeaver and VisualStudio thats bugging me.
And the fact that i can only program Windoze apps is disturbing...

=_=_=_=EDIT=_=_=_=
Oh ya, i got an idea. LOL
In GParted theres a thing called manage flags.
If i set all the partitions EXCEPT the winsux partition as hidden it might work!

---

### Post by Dojan5 on 2008-02-24
Okay, tried almost everything.
One more thing.
1. Check if old flatcable still works, if so take old XP hdd and connect to cable, if everything works use the cd in WinCrap XP and install.
Might and might not work...
Too tired to try that today...
Thanks for helping me.

---

### Post by Pumalite on 2008-02-24
You are welcome.

---

### Post by Taum on 2008-02-24
I'm going through the same thing at the moment.  My Ubuntu (originally the only OS on this computer) is installed at hda1 and I went back and installed Win at hda2.  For a while, Win was the only OS that would boot, which had me afeared that I would lose my precious Ubuntu.

So, I used SuperGRUB Disk to be able to choose my boot OS, but then it couldn't recognize the Win partition!  So, it seems to me that I have Ubuntu or Win, not both.

---

### Post by Pumalite on 2008-02-24
You can have both. You just have to install them in the proper order.
There is a workaround, I'll try to find it.

---

### Post by Pumalite on 2008-02-24
Re: Dual booting Ubuntu/XP with Ubuntu already installed
Quote:
Originally Posted by MrZumma View Post
I need to install XP for an app that will not run under WINE and needs to transfer data to a PDA that can't be configured in an XP install created in VirtualBox.

I have two hard disks installed. One hard disk contains the Ubuntu Feisty install and the other disk is blank. I would like to install XP to the blank disk and have GRUB prompt me for which OS to load. I have not found a HowTo that explains how to do what I want to do. Only to install Unbuntu on an existing XP install.

Thanks for any direction/links/etc.!
This may give you an idea of how to set your system up:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
The principle should be the same...disconnect your Ubuntu drive, connect your other drive to the primary hard drive controller...install XP, then reconnect Ubuntu as primary boot drive & XP drive as secondary.
__________________

---

### Post by Taum on 2008-02-24
> **Pumalite said:**
> Re: Dual booting Ubuntu/XP with Ubuntu already installed
Quote:
Originally Posted by MrZumma View Post
I need to install XP for an app that will not run under WINE and needs to transfer data to a PDA that can't be configured in an XP install created in VirtualBox.

I have two hard disks installed. One hard disk contains the Ubuntu Feisty install and the other disk is blank. I would like to install XP to the blank disk and have GRUB prompt me for which OS to load. I have not found a HowTo that explains how to do what I want to do. Only to install Unbuntu on an existing XP install.

Thanks for any direction/links/etc.!
This may give you an idea of how to set your system up:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
The principle should be the same...disconnect your Ubuntu drive, connect your other drive to the primary hard drive controller...install XP, then reconnect Ubuntu as primary boot drive & XP drive as secondary.
__________________

Well, it's one hd with two partitions.  It's partitioned as Ubuntu on hd1 and Win on hd2.  In Ubuntu, I can see the Win partition and browse it, but I have no ability to boot to that partition.

Basically, I have no ability to choose which partition to boot from.  I've been searching ye olde forums for an answer, but I've had a lot of white rabbits so far.

---

### Post by Dojan5 on 2008-02-24
Hmm, my windows installation dont even start, but ill try the thing posted before.
But, there is a trick for installing Windows On a EEEpc (you know those mini super cute laptops :D) without a cd, where you copy the installation files to the hdd and something about installing Dos and so on. I think ill try that first...
I mean, if the files are on the partition they are getting installed on they have to recognize the partition.

---

### Post by Taum on 2008-02-24
> **Pumalite said:**
> You can have both. You just have to install them in the proper order.
There is a workaround, I'll try to find it.

You're absolutely right.  I've found that oh-so inconvenient built in flaw with Windows where if the boot partition isn't located within the first 1024 cylinders of the Hard Disk, it won't boot. So this baby gorilla will cry if it's not the first thing installed, which means I had to reformat my drive, put Windows on first, then Linux.  And it's up now.  Thanks!

---

### Post by Pumalite on 2008-02-24
Good luck.

---

### Post by Dojan5 on 2008-02-25
> **Taum said:**
> You're absolutely right. I've found that oh-so inconvenient built in flaw with Windows where if the boot partition isn't located within the first 1024 cylinders of the Hard Disk, it won't boot. So this baby gorilla will cry if it's not the first thing installed, which means I had to reformat my drive, put Windows on first, then Linux. And it's up now. Thanks!

I dont think you had to do that to be honest...
Look here: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

Anywho, this gave me a third idea, if the first one dont work ill try the same on my moms XP computer with hers and my HDD, but i could also remove the Windows Partition, move the Linux and create a new Windows Partition...
Cause id rather not reformat the HDD...
Thanks for giving me that great idea, then maybe the baby gorilla wont cry for me either.
/
Joel

---

### Post by Dojan5 on 2008-02-25
Okay, i got my Wincrap XP installed now. Now for the booting part.
First i removed the Wincrap Partition and then i moved the linux and made the  Wincrap partition first, now the computer recognize it.
But first, here is how i did:
1. Boot Ubuntu
2. Insert the XP cd
3. Copy the XP files to a folder perferably in home directory
4. Restart the computer and boot into live cd
5. Copy the XP cd files to the Windows Partition
6. (Optional) Google and find Smartdrv.exe OR find it on your Wincrap 98 cd
7. Get a Start Disk (I got mine from a XP by inserting the disk and left click on it, click format then check MS-DOS start disk and format it)
8. Run smartdrv.exe
9. Type in > cd I386
10. Run Setup.exe (If it dont find it run Install.exe)

Congrats!
Now reinstall GRUB to the MDR.
Hy the way, heres an article: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
How to dual-boot wincrap with ubuntu

---

### Post by Dojan5 on 2008-02-25
Just a minor HUGE problem now.
I cant boot into Crapodos Windoze XP...
I had to change my /boot/grub/menu.lst
So i did that and added:

title Microcrap Windoze XP
root (hd0,1)
makeactive
chainloader +1

But i think it is this hd0,1 that is the problem. Look at the attatchment to see how my hdd is put up...
So, how do i configure this entry so it fit my harddrive?

---

### Post by Pumalite on 2008-02-25
I'm not a Windows user, but I think XP needs ntfs and fat32 might not do.

---

### Post by Dojan5 on 2008-02-26
> **Pumalite said:**
> I'm not a Windows user, but I think XP needs ntfs and fat32 might not do.

The problem is that i cant install with NTFS since i copied over the files to the HDD and installed from the HDD since the computer dont catch the boot...
But i also discovered that i was missing a LOT of files.
So i am going to install Windoe98 and then install XP through that.
It has always worked, tho it means a lil more hassle...

---

### Post by Pumalite on 2008-02-26
Let us know how you come out.

---

### Post by Dojan5 on 2008-02-26
> **Pumalite said:**
> Let us know how you come out.

I will.
But, this morning, the weirdest thing ever happend to me when its about computers, (well except when my friend secretly installed a program to be able to speak throught the mic and makeing it sound like the computer talking, it sounded like microsoft sam :lolflag:)

But anyway, Ubuntu didnt recognize my Windows98SE cd :confused:
I got pretty sad since i coud have started the install before i leave for school, but... And the thing is that Macrosoft Windox XP (Mi moms computer) DO recognize it :confused::confused:
But if i make copy the cd files to my mp3 and then burn them into a folder in a cd the computer might recognize the files and i MAYBE will be able to copy the files to the HDD...
Ill keep ya updated, one more lesson (English :lolflag:) and im off to home, when school begins tho... (Off topic: I CANT belive that i have break from 11.45 AM to 2.05 PM i could go home a million times during that time)

---

### Post by Pumalite on 2008-02-26
Good luck Dojan.

---

### Post by Dojan5 on 2008-02-26
Thanks, but i encountered a problem.
I copied the Windows98 (Second Edition) installation files to the computer (Err the whole cd to be exact) and the installation ran smooth. And then i couldnt boot up.
So i used the Live CD and reinstalled grub
```
sudo grub
locate /boot/grub/menu.lst
some commando i dont remember
setup (hd0,0)
```
Before i couldnt boot Ubuntu, now i can.
But i cant boot Windows.
It says Disk Error
Please remove the disk and insert a proper boot media.

The thing is that i dont have any disk in the 3.5 Disk A:
So, any suggestions, the problem occur only when booting Windox98SE

---

### Post by Pumalite on 2008-02-26
Post:
cat /boot/grub/menu.lst
sudo fdisk -lu

---

### Post by Dojan5 on 2008-02-27
> **Pumalite said:**
> Post:
cat /boot/grub/menu.lst
sudo fdisk -lu

Exactly what dies fdisk do? And -lu?

---

### Post by Pumalite on 2008-02-27
It delivers a list of all the drives and partitions you have with all the details I need to help you.

---

### Post by Dojan5 on 2008-02-27
```
joel@kissedesigns:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=edb022d7-040c-4a08-9fc7-1a05e32aacf4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=edb022d7-040c-4a08-9fc7-1a05e32aacf4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=edb022d7-040c-4a08-9fc7-1a05e32aacf4 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title           Microsoft Windows XP
root            (hd0,1)
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST
joel@kissedesigns:~$ sudo fdisk .lu
[sudo] password for joel:

Cannot open .lu
joel@kissedesigns:~$ sudo fdisk -lu

Disk /dev/hda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar, totalt 312581808 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Diskidentifierare: 0x000b98f0

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1       195318270   215945729    10313730   83  Linux
/dev/hda2   *          63   195318269    97659103+   b  W95 FAT32
/dev/hda3       215945730   245248289    14651280   82  Linux växling / Solaris
/dev/hda4       245248290   312576704    33664207+  83  Linux

The posts in the partition table arent in order.
joel@kissedesigns:~$ 


```

Ok, heres the commands you asked me to run.
Hda2 is the one thats first...
Oh yaa, why does it say W95? I installed W98SE

---

### Post by Pumalite on 2008-02-27
Where is :
sudo fdisk -lu

---

### Post by Dojan5 on 2008-02-27
> **Pumalite said:**
> Where is :
sudo fdisk -lu
```
joel@kissedesigns:~$ sudo fdisk -lu

Disk /dev/hda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar, totalt 312581808 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Diskidentifierare: 0x000b98f0

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1       195318270   215945729    10313730   83  Linux
/dev/hda2   *          63   195318269    97659103+   b  W95 FAT32
/dev/hda3       215945730   245248289    14651280   82  Linux växling / Solaris
/dev/hda4       245248290   312576704    33664207+  83  Linux

The posts in the partition table arent in order.

```
It was in the bottom

---

### Post by Pumalite on 2008-02-27
Sorry Dojan, you have to install Windows first (hda1) and Ubuntuv last. There is some workaround, but I don't remember it. Maybe someone will come to the rescue.

---

### Post by Pumalite on 2008-02-27
I found it:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by Dojan5 on 2008-02-27
It can't boot from the XP cd, and that was the problem at the beginning... T-T
I guess ill have to reformat?
Awww. Maybe i can borrow my mothers burner and burn the stuff i have in the computer, i have around 8gb which is VERY important...
But i could always download them again i guess...
Ok...

Oh and yaa, i installed Win98...
It got all the system files but it wont boot.
It says
> Disk error.
Please remove the disk and insert a proper boot media.
You know what i think?
I think it recognize the Ubuntu Partitions (the swap the home or the core)

---

