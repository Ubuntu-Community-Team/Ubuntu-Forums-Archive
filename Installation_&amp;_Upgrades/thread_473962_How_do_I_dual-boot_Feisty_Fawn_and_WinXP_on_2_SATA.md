---
title: "How do I dual-boot Feisty Fawn and WinXP on 2 SATA HDDs ?"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Rock_Lee_NuX on 2007-06-14
Hello everyone,

The reason I'm posting is that it is the _**1st time I'm going to install Ubuntu**_ (specifically I downloaded v7.0.4 Feisty Fawn) and **dual boot with WinXP** on my computer and I just wanted to see if the initial procedure I want to implement is the correct one.

My computer hardware setup:

-  MSI, MS-7260, Version 1.0
-  AT/AT COMPATIBLE
-  **AMD Athlon(tm) 64 X2 Dual Core Processor 3800+**, Windsor, Socket AM2
-  Physical Memory **(RAM) 2048 MB** Total
-  Seagate ST3160812SV, **160 GBytes, IDE SATA-II**, Disk C: 34 GB Available, 149 GB Total, NTFS 3.1
-  Seagate ST3160812SV, **160 GBytes, IDE SATA-II,** Disk E: 137 GB Available, 149 GB Total, NTFS 3.1
-  DVD, LG Electronics, HL-DT-ST DVDRAM GSA-4167B, IDE ATAPI

As you see I have **2 SATA HDDs** (no RAID setup) from which on the 1st I have installed Windows XP Pro SP2 and on the 2nd Windows Vista RC1. I've only used Vista about 10 times, I've got rid off it's boot loader using VistaBootPRO 3.2 and now I can boot into my WinXP without choosing through the boot loader.

So, now I want to install Ubuntu on the 2nd HD where I have Vista with NTFS. What I also want is to keep GRUB on the 2nd HD and not on the 1st one where WinXP is installed.

Ok, call me a noob :D but I think it will be safer this way, plus I don't want to get myself into removing the 1st HD physically from the computer, install Feisty Fawn and then install it back again. Quoting member Gn2 "...7.04 has an "Advanced" button at the Grub installation stage, which when pressed gives the option to enter a different location for Grub to be written to." at this [post ]("http://ubuntuforums.org/showthread.php?t=275728") I am happy to see that I can do what I want.

_In short, what I'm going to do now is insert the Ubuntu 7.0.4 Feisty Fawn "64-bit PC (AMD64) alternate install CD" boot from it and following the instructions I will format the 2nd HD and install GRUB on it through this "Advanced" button._

I've never installed Ubuntu anywhere, I'm not familiar with the procedure after I boot from the install CD, I don't want to miss this "Advanced" button and I don't exactly know what I'm supposed to write to the grub menu.lst after the install so that I will be able to choose the WinXP partition whenever I want. Furthermore, should I uninstall VistaBootPRO from my WinXP partition in order to avoid any complications? If yes when exactly, before or after the Ubuntu install?

If anyone could give advice/tips and/or some screenshots from the install procedure and tell me if what I mentioned so far is correct, I would be grateful.

Thanks in advance to everyone! 

...And may the force be with you :KS

---

### Post by mrphantastic on 2007-06-14
Aight, I don't know if i can help you perfeclty, but I think i've got you well covered.  so, my first question is...you are basically wanting to run WinXP AND Ubuntu 7.04 together both on Separate HDD's as a Dual-boot WITHOUT any type of Vista at all, right?

---

### Post by confused57 on 2007-06-14
This guide has instructions for setting up grub to boot Windows on a 2nd hard drive:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
The guide mentions disconnecting your Window's drive, but you shouldn't have to if you:
Before you boot the live cd to install, enter your bios setup and set the drive you're going to be installing Ubuntu to boot before your Window's drive...grub should recognize this drive as (hd0) and install grub to the mbr...you shouldn't have any trouble spotting the Advanced options button on where to install grub...you can select to install on /dev/sdb(if this is your Ubuntu drive), just to be sure.

Added: Before you install Ubuntu, you might want to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7 Mb), and SGD is capable of booting Windows or Ubuntu and restore the IPL of either to the mbr

---

### Post by mrphantastic on 2007-06-14
Oh, lordy...confused57...I found it  A LOT easier than stuff like that, lol, i'm just waiting for Rock_Lee_NuX to gimme a heads up, but yeah, that could help him out....looks tuff tho....

---

### Post by confused57 on 2007-06-14
> **mrphantastic said:**
> Oh, lordy...confused57...I found it  A LOT easier than stuff like that, lol, i'm just waiting for Rock_Lee_NuX to gimme a heads up, but yeah, that could help him out....looks tuff tho....
He doesn't want to install grub to his Windows drive's mbr and the toughest part is setting his bios to boot his Ubuntu drive to boot first...it's much easier than it might be perceived to be...at least he has different options that he can consider.  In fact, the Ubuntu installer should recognize his Window's install and automatically add an entry to boot his Window's drive...

---

### Post by mrphantastic on 2007-06-14
hey, good pt, i was just talkin' about using that guide and all of the terminal commands n stuff...lol.  (i'm not the greatest when it comes to lack of a GUI...)  he will have it easy with two hard drives tho, your right :)

---

### Post by confused57 on 2007-06-14
> **mrphantastic said:**
> hey, good pt, i was just talkin' about using that guide and all of the terminal commands n stuff...lol.  (i'm not the greatest when it comes to lack of a GUI...)  he will have it easy with two hard drives tho, your right :)
As an afterthought, I realized I didn't really need to provide the link for adding a Window's entry, since he's not disconnecting his Window's drive.  He really needs to change the bios boot order to boot the Ubuntu drive first, otherwise grub would recognize this drive as (hd1) and even if he installed grub to the Ubuntu drive's mbr, he would still have to modify his root partition in his menu.lst from (hd1) to (hd0), in order to boot first to his Ubuntu drive...and would also have to change his Window's entry to add the mapping commands.
Hopefully, our mono-on-mono discussion will help the OP to make an informed decision.

---

### Post by mrphantastic on 2007-06-14
If not, i PM'd him and sed i would email him to send him screenshots if he needed, I don't mind taking a long time, instead of showing a guide...not that your guide isn't awesome, it's ballin'...I looked over it and was nothing short of thoroughly impressed.   But i just love troubleshooting, when i get the chance...i'm a pc dweeb like that...

---

### Post by Rock_Lee_NuX on 2007-06-14
All I can say is that I stand amazed and in awe :o with the lighting-fast replys I got from you guys. I am reading through your posts and hope to understand them...

I am grateful... :KS

---

### Post by Rock_Lee_NuX on 2007-06-14
> **mrphantastic said:**
> Aight, I don't know if i can help you perfeclty, but I think i've got you well covered.  so, my first question is...you are basically wanting to run WinXP AND Ubuntu 7.04 together both on Separate HDD's as a Dual-boot WITHOUT any type of Vista at all, right?

Thank you for your PM mrphantastic and YES to your question, that is exactly what I want to do.

---

### Post by Rock_Lee_NuX on 2007-06-14
> **confused57 said:**
> As an afterthought, I realized I didn't really need to provide the link for adding a Window's entry, since he's not disconnecting his Window's drive.  He really needs to change the bios boot order to boot the Ubuntu drive first, otherwise grub would recognize this drive as (hd1) and even if he installed grub to the Ubuntu drive's mbr, he would still have to modify his root partition in his menu.lst from (hd1) to (hd0), in order to boot first to his Ubuntu drive...and would also have to change his Window's entry to add the mapping commands.
Hopefully, our mono-on-mono discussion will help the OP to make an informed decision.
So what I have to do by going through your instructions is:

1) Go to BIOS and change the boot sequence as follows:
 i) 1st boot device: DVD (to boot from the Alt. Install CD right after I exit the BIOS)
 ii) 2nd boot device: 2nd SATA drive (which has Vista installed)

2) EXIT BIOS and boot from Ubuntu install CD to proceed with the installation

3) On the Advanced options button I choose to install GRUB on /dev/sdb ? (even though I changed the boot sequence order on step 1 the 2nd SATA drive should appear as /dev/sdb and not /dev/sda, right ?)

4) If all things go well when the install completes and the system reboots, I should be presented with 2 choices, one to boot WinXP and one to boot Ubuntu ? No need to edit grub menu.lst ?

---

### Post by confused57 on 2007-06-14
Yes, I believe you have a workable plan.

> 3) On the Advanced options button I choose to install GRUB on /dev/sdb ? (even though I changed the boot sequence order on step 1 the 2nd SATA drive should appear as /dev/sdb and not /dev/sda, right ?)

When you do the partitioning, make a note of how the partitioner identifies your Ubuntu hard drive, i.e. /dev/sdb, this is where you'll install grub, using the Advanced option.

Good luck with the install...although you shouldn't have any problems.

---

### Post by mrphantastic on 2007-06-14
Ok, i'll get to working, let me see if i can figure out how to set it up the right way.  Because, correct me if i'm wrong, but as confused57 and i were talking about, you do not want the mbr from windows affected, do you?  So we will have to use the little advanced setup button at the end of the linux installation to setup a different location other than hd0.  I'll try to catch you when you're on.  But, i shall PM you my email.  That way you can get me easier to ask questions and/or share screenshots, etc.  Good luck!

---

### Post by Rock_Lee_NuX on 2007-06-15
Thank you confused57 for pointing out details that I may have overlooked during my endeavor :D

---

### Post by badmancaymanian on 2007-06-19
I am just wondering if you got it to work. I am trying to do the same thing.

---

### Post by Rock_Lee_NuX on 2007-06-24
> **badmancaymanian said:**
> I am just wondering if you got it to work. I am trying to do the same thing.

@ *badmancaymanian*,

Well the good news is that I am writing this post from the newly installed **(installation finished at about 20:00, 24 June 2007**) Feisty Fawn on my computer. The bad news is that there are some glitches which I hope are reversible and with the help of the vigorous ubuntu community I'll be able to overcome in no time :D


@ *confused57*

I managed to install Feisty Fawn without destroying the windows partition on the first SATA drive, but the problem is that I think that somewhere I must have made a mistake (can't figure out where) and now I am booting in Ubuntu with the help of Super Grub Disk CD, by editing the line which says (hd1,0) to (hd0,0). Problem... how did this happen ??? :(


@ *mrphantastic*

I am grateful for your help and the guide that you sent me which helped me to understand some things about the installation of Ubuntu, but... I used the Alternate Install CD and there was no GUI there ;) ...just text... As I said earlier thank God that I didn't destroy the Windows partition because I almost did... Phew!!! I just read your e-mail and I'll get back to you :D

---

### Post by Rock_Lee_NuX on 2007-06-24
I'll get back with the details of the installation tomorrow (I hope)... have to go to sleep now... Work starts at 09:00 and I have less that 5 hours of sleep. :KS:KS:KS

---

### Post by Rock_Lee_NuX on 2007-06-25
Well now here is the procedure I followed with:
i) my two identical 160 GB Seagate SATA drives,
ii) AMD Athlon 64 X2 3800+,
iii) 64-bit PC (AMD64) alternate install CD (because I've read that you may upgrade to the next Ubuntu release rather than installing it again with it),
iv) WinXP installed on the 1st SATA drive, 
v) WinVista on 2nd SATA drive (but I got reed of its boot-loader using VistaBootPRO and was able to boot WinXP normally again, but didn't format the drive).

Installation procedure:
1) Changed the boot order through BIOS. So 1st boot device is the DVD-ROM and 2nd the 2nd SATA drive which had Vista in it.

2) Inserted the Ubuntu 64-bit PC (AMD64) alternate install CD and proceeded with the installation.

3) In the "PARTITION DISKS" step I almost destroyed my healthy WinXP installation on the 1st drive, because they are identical I couldn't tell which was the one containing the Vista install. So, I thought (OK, I never before made an installation of Ubuntu, and the best part is that I used the text based Alternate Install CD, I AM A NOOB :)) that after the changing of the boot order in BIOS the 1st SATA drive was called "sdb" and the 2nd SATA drive "sda". But it was exactly the opposite, meaning that 1st drive (WinXP) was "sda" and 2nd drive was "sdb"... Thank God, that at this point I decided to go to WinXP and partition the 2nd drive with 2 partitions in order to distinguish them when I would reach once again the "PARTITION DISKS" step.

4) So, knowing that "sdb" is the 2nd (Vista) drive, I used "partman" to partition it into the following partitions :
#1 Primary 60 GB for Feisty Fawn installation (ext3), mount point "/"
#6 Logical 3 GB swap
#5 Logical 97 GB (fat32) for sharing with WinXP, mount point "/windows"

5) After the partitioning I finally reached the "difficult for a noob" part of where to place Grub. I chose NO to installing Grub on the MBR and after that I had my screen filled with fatal errors on Grub installation saying Unable to install GRUB in "sdb" and "/dev/sdb" and many other combinations that I tried. Well the tricky part was that I was using QUOTES. Call me a noob but I typed it as the example was saying with QUOTES (hey, it didn't say anywhere to remove the QUOTES). Well after I typed /dev/sdb (2nd SATA drive) the installation finished normally..........

6) Except that when the computer rebooted the Ubuntu drive would not boot... *Big frustration* here :(

7) The good thing was that I had followed [herman's pre-install guide]("http://users.bigpond.net.au/hermanzone/") and made a SGD CD. So I booted from it and went to find out what was the problem. Note, that WinXP was not harmed and when I changed the boot order of the SATA drives through BIOS I was able to boot normally with WinXP.... PHEWWWW.... *relief*

8) After using SGD CD I found that Ubuntu Feisty Fawn was installed OK, but when I went to edit the boot line of Feisty it said (hd1,0). When I change it to (hd0,0) Feisty boots normally... A BIG YEEEEEAAAAH for SGD and [adrian15]("http://forjamari.linex.org/users/adrian15/") at this point...!!! At last I could see Ubuntu Feisty Fawn installed on my PC !!!

9) So now I am stuck, because I don't know how to permanately fix the boot option for Ubuntu, without having to use SGD (also I can't understand what did I do wrong and at what point).

10) I am able to see WinXP's drive contents, but I can't find anywhere the FAT32 partition that I made on Ubuntu's SATA drive and also I can't see some other things like properties of Ubuntu's partition. I am writing this post through WinXP, when I boot into Feisty I'll write more details.

So... Please help :KS:KS:KS

Noob's Log...
25 June 2007 AD, 23:47...
Save file in progress...
Saved...

---

### Post by confused57 on 2007-06-25
> 9) So now I am stuck, because I don't know how to permanately fix the boot option for Ubuntu, without having to use SGD (also I can't understand what did I do wrong and at what point).

What you'll need to do is boot into Ubuntu with SGD and edit root in your menu.lst, you can do this by opening a terminal(Applications---Accessories---Terminal), enter(a line at a time, press "enter" after each line):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```
the first line changes to the grub directory, the 2nd line creates a backup of your menu.lst...then to edit:
```
gksudo gedit menu.lst
```
change your root from (hd1,0) to (hd0,0) and change the line beginning with #groot to (hd0,0):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

Sounds like quite an adventure installing Ubuntu and Windows came through it "unscathed"...glad you were able to get Ubuntu installed & working.

You may not have done anything wrong, grub may possibly have incorrectly guessed  from your bios settings which was actually the first hard drive...that's why I suggested entering /dev/sdb as the location to install grub.

---

### Post by Rock_Lee_NuX on 2007-06-26
> **confused57 said:**
> What you'll need to do is boot into Ubuntu with SGD and edit root in your menu.lst, you can do this by opening a terminal(Applications---Accessories---Terminal), enter(a line at a time, press "enter" after each line):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```
the first line changes to the grub directory, the 2nd line creates a backup of your menu.lst...then to edit:
```
gksudo gedit menu.lst
```
change your root from (hd1,0) to (hd0,0) and change the line beginning with #groot to (hd0,0):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

I'm sorry *confused57*, but I'm not familiar with Grub editing as with everything in ubuntu, so  here is my menu.lst in case you get something out of it... 

```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=fbed4ac7-98f7-4515-b578-62f14663efe5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fbed4ac7-98f7-4515-b578-62f14663efe5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fbed4ac7-98f7-4515-b578-62f14663efe5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fbed4ac7-98f7-4515-b578-62f14663efe5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fbed4ac7-98f7-4515-b578-62f14663efe5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

```

When you say to change "root from (hd1,0) to (hd0,0)" you mean every line that I see beginning with "root (hd1,0)" after the part that says "## ## End Default Options ##" ?

Also can you please tell where did the fat32 partition went? :confused:

Furthermore I don't know what to do with the entry of "Windows Vista/Longhorn (loader)". Should I just delete it from menu.lst to get reed of it ?

PS: Thanks for helping me out with this. I'm also searching in other posts to find what to do and not bother you all the time.

---

### Post by confused57 on 2007-06-26
It's no bother, I'm glad to help a new user...most everyone just starting out were apprehensive about making changes through the terminal.
Yes you're correct, change the line with root in all of your Ubuntu entries:
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fbed4ac7-98f7-4515-b578-62f14663efe5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

then find the groot line, change it to (hd0,0):
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
```

quit & save

If you make a mistake, which you won't, you created a backup if you followed the instructions in my last reply...to restore the backup:
```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```

---

### Post by Rock_Lee_NuX on 2007-06-28
Hi again, I've just made the changes to" menu.lst" and besides changing Bubuntu's root to (hd0,0) and groot to (hd0,0), I also changed Windows Vista/Longhorn (loader) root to (hd1,0). Hope I did well with that and now I'm going to reboot :D ... *prays* everything to go well...

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
chainloader	+1
```

---

### Post by Rock_Lee_NuX on 2007-06-29
[COLOR="SeaGreen"]Hoorayyy!!![/COLOR] :D

Ubuntu now boots normally after changing root and groot to (hd0,0).

I also tried to boot the entry that says Windows Vista/Longhorn (loader) with root (hd1,0), but nothing happens, it just reboots the computer. Must be the remaining boot loader of Vista which I had installed previously on the now Ubuntu drive. Should I just delete it from menu.lst ???

Still not able to see the fat32 partition on /sdb or how to boot /sda which has WinXP... But now there is much work to be done :) ...Find out the way to install Greek spellcheck on OpenOffice, learn how to use terminal commands, find a way to watch YouTube vids... in general how ubuntu works, meaning many things.

A BIG THANK YOU to **mrphantastic** and **confused57** for helping me out with the installation... May God bless you!

---

### Post by confused57 on 2007-06-29
> **Rock_Lee_NuX said:**
> [COLOR="SeaGreen"]Hoorayyy!!![/COLOR] :D

Ubuntu now boots normally after changing root and groot to (hd0,0).

I also tried to boot the entry that says Windows Vista/Longhorn (loader) with root (hd1,0), but nothing happens, it just reboots the computer. Must be the remaining boot loader of Vista which I had installed previously on the now Ubuntu drive. Should I just delete it from menu.lst ???

Still not able to see the fat32 partition on /sdb or how to boot /sda which has WinXP... But now there is much work to be done :) ...Find out the way to install Greek spellcheck on OpenOffice, learn how to use terminal commands, find a way to watch YouTube vids... in general how ubuntu works, meaning many things.

A BIG THANK YOU to **mrphantastic** and **confused57** for helping me out with the installation... May God bless you!
Thanks for the update...glad it worked.
You might try an entry similar to this to boot Vista on your other hard drive:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader	+1
```

---

### Post by Rock_Lee_NuX on 2007-06-29
All riiiiiight!!! :D

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader	+1
```

It worked like a charm and now I am able to boot WinXP which is on /sda... Yeaaay!!! 

I should now rename the title to Windows XP so it wil not be confusing... or maybe better yet I will rename it to "Earlier version of Windows" LOL :P

Thanks **confused57** for your invaluable help in setting up **grub** correctly. And I really hope that this thread helps someone else too. Maybe I'll upload the photos I've taken with my cell phone's camera of the installation procedure on Flickr and post the link here :D

You are great help and I hope you don't mind me if I ask for your help some other time... :)

---

### Post by confused57 on 2007-06-29
Thought the Window's grub entry would work, sure is easier to boot your OSes via grub.  Screenshots of your installation would really help a lot of new users wanting to set up a dual boot, especially anyone with multiple hard drives.
   I'm always willing to assist with any issues you may have, that my limited knowledge allows...good to hear everything's booting OK.

---

