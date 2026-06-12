---
title: "Dual Installation failed Error 21"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by EduardoAB on 2008-05-15
I hav to drives the master one C where W XP is installed and the slave one D that is used just for data storage.
I have just installed ubuntu 8.O4 in the former D drive and during the process I accepted that ubuntu be able of reading the C drive.  After that booting starts and stops almost immediatly showing the legend "GRUB loading Error 21". Besides, booting from the original XP is not possible. However, If I boot ubuntu from the CD I am able to read and write both drives.
Please, help me.

---

### Post by mikewhatever on 2008-05-15
Can you post the output of <sudo fdisk -l> command from the live cd.
That error usually means GRUB entries point to wrong places, so you'd probably need to edit grub's menu. That's not very hard and can also be done from the live cd.
Edit: Since you can access your Ubuntu partition from the live cd, also navigate to /boot/grub, find the file named menu.lst and post its contents.

---

### Post by dpict on 2008-05-15
Same problem here, windows on C and Ubuntu on F (2nd drive)
Here is menu.lst Thanks for the help!

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
# kopt=root=UUID=df177722-a29c-42bd-975b-3bc2fb458e84 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=df177722-a29c-42bd-975b-3bc2fb458e84 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=df177722-a29c-42bd-975b-3bc2fb458e84 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mikewhatever on 2008-05-15
> **dpict said:**
> Same problem here, windows on C and Ubuntu on F (2nd drive)
Here is menu.lst Thanks for the help!

You should also post <sudo fdisk -l> output. C and F notions don't mean much in non Windows world.

---

### Post by dpict on 2008-05-15
thank you very much

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed26ed26

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4110    33013543+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedd6aac1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       21630   173742943+   7  HPFS/NTFS
/dev/sdb2           21631       24321    21615457+   5  Extended
/dev/sdb5           21631       24203    20667591   83  Linux
/dev/sdb6           24204       24321      947803+  82  Linux swap / Solaris

---

### Post by Pumalite on 2008-05-15
Post a screenshot of gparted showing sda5

---

### Post by dpict on 2008-05-15
> Post a screenshot of gparted showing sda5
No clue what that means, but thanks

---

### Post by Pumalite on 2008-05-15
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post a screenshot (camera icon)

---

### Post by EduardoAB on 2008-05-16
> **mikewhatever said:**
> Can you post the output of <sudo fdisk -l> command from the live cd.
That error usually means GRUB entries point to wrong places, so you'd probably need to edit grub's menu. That's not very hard and can also be done from the live cd.
Edit: Since you can access your Ubuntu partition from the live cd, also navigate to /boot/grub, find the file named menu.lst and post its contents.Mike, sorry for the lack of experience but can you tell me how to perform the <sudo fdisk -l> command from the live cd?

---

### Post by Pumalite on 2008-05-16
Once you get to the Desktop, go to Applications>Accessories>Terminal
Copy and paste the command in the Terminal. Press 'Enter'
Copy and paste the output here.

---

### Post by Azrael90 on 2008-05-16
same error code here. i have my drives connected via a pci ide adapter. without ubuntu the highpoint technologies software detects both drives but after installing ubuntu it only detects the one drive with windows on it

---

### Post by Pumalite on 2008-05-16
Read this:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)
[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639)

---

### Post by Azrael90 on 2008-05-16
> **Pumalite said:**
> Read this:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)
[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639)

if this was meant to help my post I am not able to see the connection since there is no explanation how I can get it to detect the second drive

---

### Post by Pumalite on 2008-05-16
Do you have a SATA and an IDE?

---

### Post by Azrael90 on 2008-05-16
no both ide (my board only has sata connections) connected via pci it is not a real raid controller but something like it

---

### Post by Pumalite on 2008-05-16
Post:
sudo fdisk -l

---

### Post by Azrael90 on 2008-05-16
okay gonna take a minute since it is on another computer and I have no idea how to caopy it out of textmode

---

### Post by Pumalite on 2008-05-16
Save it in a CD or floppy and post here as text.

---

### Post by Azrael90 on 2008-05-16
> Platte /dev/hde: 200.0 GByte, 200049647616 Byte
255 Köpfe, 63 Sektoren/Spuren, 24321 Zylinder
Einheiten = Zylinder von 16065 x 512 = 8225280 Bytes
Disk identifier: 0x5fb75fb7

Gerät       Boot    Anfang    Ende    Blöcke      Id     System
/dev/hde1    *        1      24320  195350368+     7       HPFS/NTFS





Sorry some of the things are in german but i take it you know the structure   starting english version and i will edit it asap

---

### Post by Pumalite on 2008-05-16
Well; it shows only one hard drive with one partition and Windows in it. Go into BIOS and check if your other drive is seen there. Otherwise, go into your computer to check cables and connections. You can change them to different ports too.

---

### Post by Keith Fisher on 2008-05-16
Eduardo,

Did you have a previous installation of Linux/Ubuntu on that machine?

If you want to get back to Windows XP urgently then boot from a Windows XP Installation CD-ROM. You'll need to select the "Repair" option when prompted and use the console to fix the master boot record so that Windows can start again.

Google: "grub error 21 and fixmbr" for a lot of step-by-step instructions...

---

### Post by Azrael90 on 2008-05-16
drives are not shwon in bios but they never did. they only showed up in some software of highpoint technologies the company from the raid controller. connections triple checked already going to do it again

---

### Post by Azrael90 on 2008-05-16
in the config of the raid controller I can set from which hdd it should boot if i enable the ubuntu drive to boot from it does not detect a Os and tries to boot by cd. If I enable the drive with windows on it tries to load grub but says error 17

I am going to post the fdisk with both devices now

---

### Post by Azrael90 on 2008-05-16
```
Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinder
Units = cylinder of 16065 x 512 = 8225280 bytes
Disk identifier: 0xfb85fb85

Device   Boot Start   End    Blocks   Id System
/dev/hde1 *     1     18705 150247881 83 Linux 
/dev/hde2 *   18706   19457 6040440   5  Extended 
/dev/hde5 *   18706   19457 6040408+  82 Linux swap / Solaris



Disk /dev/hdg: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinder
Units = cylinder of 16065 x 512 = 8225280 bytes
Disk identifier: 0x5fb75fb7

Device Boot Start End      Blocks  Id    System
/dev/hdg1 * 1     24320 195350368+  7   HPFS/NTFS





```




Error on boot: Error 17 while loading GRUB.  So what can I do about it ?

---

### Post by Azrael90 on 2008-05-16
bump

---

### Post by Pumalite on 2008-05-16
Change the boot order of your drives in BIOS.

---

### Post by Azrael90 on 2008-05-16
when i activate the ubuntu drive to start first it says error 17 and when i put the other one at first it tries to boot from cd because it is not detecting an OS

---

### Post by Pumalite on 2008-05-16
These links are informative:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)
I'd advise you to put both OS's in your first drive and use the other for storage.

---

### Post by Azrael90 on 2008-05-16
> **Pumalite said:**
> 
I'd advise you to put both OS's in your first drive and use the other for storage.Okay I made a decision I am going to delete windows. Install windows and then install ubuntu on the same drive. I will leave some space for it from the beginning. Thanks for your time and help.

---

### Post by Pumalite on 2008-05-16
No. What do you have: XP or Vista?

---

### Post by Azrael90 on 2008-05-16
xp since vista seems to be worse than xp

---

### Post by Pumalite on 2008-05-16
Here is a good guide. Let Grub install to MBR and you'll have dual boot:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by Azrael90 on 2008-05-16
Thank you for your time and knowledge. I would rep you again if it would be possible^^

---

### Post by Pumalite on 2008-05-16
You are welcome. Good luck.

---

### Post by Azrael90 on 2008-05-16
i finished formating  but now NTLDR is missing and I cannot get it back through loading failsafe defaults. any idea ?


solved left a disk in there

---

### Post by Pumalite on 2008-05-16
ost:
sudo fdisk -l
cat /boot/menu.lst

---

### Post by Azrael90 on 2008-05-16
just finished installing ubuntu...no dualboot is shown and when i insert the ubuntu cd to start from the hard drive it just starts windows

---

### Post by Azrael90 on 2008-05-16
bump

---

### Post by Azrael90 on 2008-05-16
Windows is not detecting ubuntu so i cannot boot it

---

### Post by Pumalite on 2008-05-16
Do you see Grub?

---

### Post by Azrael90 on 2008-05-16
I am not seeing GRUB since I installed windows xp and ubuntu on the same hdd going to post what livecd says

---

### Post by Azrael90 on 2008-05-16
command: sudo fdisk -l
```

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinder
Units = cylinder of 16065 x 512 = 8225280 bytes
Disk identifier: 0xfb85fb85

Device   Boot Start   End    Blocks   Id System
/dev/hde1      1     10199 81923436    6 FAT16




Disk /dev/hdg: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinder
Units = cylinder of 16065 x 512 = 8225280 bytes
Disk identifier: 0x5fb75fb7

Device Boot Start End      Blocks  Id    System
/dev/hdg1 * 1      1    92156841    7   HPFS/NTFS
/dev/hdg2   1     11474 996030      82   Linux swap/ Solaris
/dev/hdg3   1     11598 102205530   83  Linux

```

---

### Post by Pumalite on 2008-05-16
Mount your partition:
sudo mkdir /media/sdg3
sudo mount -t ext3 /dev/sdg3 /media/sdg3
Post:
cat /media/sdg3/boot/grub/menu.lst

---

### Post by Azrael90 on 2008-05-16
> **Pumalite said:**
> Mount your partition:
sudo mkdir /media/sdg3
sudo mount -t ext3 /dev/sdg3 /media/sdg3
Post:
cat /media/sdg3/boot/grub/menu.lst

sudo mount -t ext3 /dev/sdg3 /media/sdg3
-> mount: special device /dev/sdg3 does not exist

cat /media/sdg3/boot/grub/menu.lst
-> No such file or directory

---

### Post by Pumalite on 2008-05-16
Try with sda3

---

### Post by Azrael90 on 2008-05-16
> **Pumalite said:**
> Try with sda3

if these are the things of fdisk stuff it should be hdg or am i wrong ? trying your solution now

---

### Post by Azrael90 on 2008-05-16
sudo mount -t ext3 /dev/sda3 /media/sda3
->mouint: special device /dev/sda3 dows not exist


you are aware that I am in the live cd ? I dont know if this will be working there

---

### Post by Pumalite on 2008-05-16
Something went wrong with your installation. Get Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post screenshot.

---

### Post by Azrael90 on 2008-05-16
what should i post exactly ? i have done some config like language but now says 
Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining


wtf?

---

### Post by Pumalite on 2008-05-16
Fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by Azrael90 on 2008-05-16
okay it says that sgd succeded and mbr is now the old one. windows i booting perfectly fine now but there is still no way to chose ubuntu

---

### Post by Azrael90 on 2008-05-16
I can actually boot ubuntu now with supergrub

---

### Post by Pumalite on 2008-05-16
Super Grub is great to have around. Now that you can boot to Ubuntu; post:
cat /boot/grub/menu.lst

---

### Post by Azrael90 on 2008-05-16
```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b9dc7e25-642b-4f6b-a9af-da6bcb2d685b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b9dc7e25-642b-4f6b-a9af-da6bcb2d685b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdg1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

---

### Post by Pumalite on 2008-05-16
Here we are facing the problem of what drive you are booting from. Your first drive should be (hd0), therefore, Ubuntu would be (hd0,2) and Windows (hd0,0). Try that if that is the drive where you installed your OS's.

---

### Post by Azrael90 on 2008-05-16
so I just edit the menu.lst ?

---

### Post by Pumalite on 2008-05-16
Right.

---

### Post by Azrael90 on 2008-05-16
I cannot edit it somehow . how can I get the admin rights ?

---

### Post by Pumalite on 2008-05-16
Backup your file first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Edit:
gksudo gedit /boot/grub/menu.lst
Make the changes
Save, exit, reboot.

---

### Post by dpict on 2008-05-16
Dont know if this will help but I changed the boot delay from 5sec to 10sec in the bios and the grub error went from 21 to 17. Other than that re-loading ubuntu now fresh.

---

### Post by Azrael90 on 2008-05-16
did not work. windows boot loader just ignores linux. Please don t take this wrong but I am very tired now since it is 1 am here. I am goint to sleep now. You have done a perfect job and I cannot describe how happy I am that that you helped me.

Have a good night

---

### Post by EduardoAB on 2008-05-16
Thanks. I´ll do that

---

### Post by EduardoAB on 2008-05-16
> **Pumalite said:**
> Once you get to the Desktop, go to Applications>Accessories>Terminal
Copy and paste the command in the Terminal. Press 'Enter'
Copy and paste the output here.

Here it goes

Toubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f889f88
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7b0d7b0
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2341    18804051   83  Linux
/dev/sdb2            2342        2434      747022+   5  Extended
/dev/sdb5            2342        2434      746991   82  Linux swap / Solaris

---

### Post by mikewhatever on 2008-05-17
EduardoAB, can you also post the content of menu.lst file. It's located on the Ubuntu partition in /boot/grub.

---

### Post by EduardoAB on 2008-05-17
Thank you. I will try it and let you know.

---

### Post by EduardoAB on 2008-05-17
> **mikewhatever said:**
> EduardoAB, can you also post the content of menu.lst file. It's located on the Ubuntu partition in /boot/grub.

Here it goes Mike.

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

# examples

# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro


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
# kopt=root=UUID=cd99e041-8036-4299-bcd9-4ba3718b35bf ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false



## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cd99e041-8036-4299-bcd9-4ba3718b35bf ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cd99e041-8036-4299-bcd9-4ba3718b35bf ro single
initrd		/boot/initrd.img-2.6.24-16-generic



title		Ubuntu 8.04, memtest86+
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by mikewhatever on 2008-05-17
The menu.lst looks good. The only other thing I can think of is that something is wrong with sda ~ hd0 and sdb ~ hd1 correlation. Can you post the contents of device.map file also located in /boot/grub.

---

### Post by EduardoAB on 2008-05-28
> **mikewhatever said:**
> The menu.lst looks good. The only other thing I can think of is that something is wrong with sda ~ hd0 and sdb ~ hd1 correlation. Can you post the contents of device.map file also located in /boot/grub.

Mike: the content of the device map file is:

(hdo)/dev/sda
(hd1)/dev/sdb

I hope it helps

---

### Post by EduardoAB on 2008-06-04
Mike: could you please hell me w. this problem?

---

### Post by EduardoAB on 2008-06-04
> **mikewhatever said:**
> The menu.lst looks good. The only other thing I can think of is that something is wrong with sda ~ hd0 and sdb ~ hd1 correlation. Can you post the contents of device.map file also located in /boot/grub.

Mike: the content of the device map file is:

(hdo)/dev/sda
(hd1)/dev/sdb

I hope it helps

---

### Post by Pumalite on 2008-06-04
No problem with your device.map

---

### Post by mikewhatever on 2008-06-06
Sorry for the delay, but I have no idea what's wrong.:confused:

---

