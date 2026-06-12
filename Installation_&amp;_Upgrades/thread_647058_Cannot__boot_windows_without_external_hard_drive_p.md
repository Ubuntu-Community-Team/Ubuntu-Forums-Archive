---
title: "Cannot  boot windows without external hard drive plugged in"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by meierfra on 2007-12-21
This howto  addresses the following issue: You successfully installed Ubuntu onto an external hard drive. With the external drive plugged in, you can boot into Windows and Ubuntu from the Grub menu. But if the external drive is unplugged you get a Grub error during boot up. 
To fix the problem you will have to edit the file "menu.lst",  install grub to the external hard drive,  restore the MBR of the internal hard drive and change the boot order in  the Bios.  This HowTo will only work if you can set your Bios to boot from the external drive containing Ubuntu.
(If you are not able to boot into Ubuntu, scroll down to "Boot from LiveCD" in  this post)
 Here are the details:

Step 1 Edit menu.lst

Open a terminal (Applications->Accessories->Terminal) and type

```

cd /boot/grub

sudo cp menu.lst menu.lst.backup

gksudo gedit menu.lst
```
(the "l" in menu.lst is a  lower case L, not the number one)

This creates a backup of "menu.lst" and  opens it in a new window.
Look for the line 

#groot (hdx,y)

Here x and y are some numbers. Typically this would be "#groot (hd1,0)"

Change it to 

#groot (hd0,y)

So for example "#groot (hd1,0)" needs to be changed to "#groot (hd0,0)"

Next look for the Windows title. It should look something  like

title Some Version of Windows
root (hds,t)
savedefault
makeactive
chainloader +1

Here  s and t are some numbers. Change it to 

title Some  Version of Windows
root (hd1,t)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

So for example 

title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1

needs to be changed to 

title Windows XP
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1 

Save and close the file.

To complete Step 1, go back to the terminal and type
```
sudo update-grub 
```

Step 2:  Install Grub to the MBR of the external drive:

In the terminal type:
```
 sudo grub 
```

and at the "grub>" prompt

```
root (hdx,y)

setup (hdx)

quit
```

Here x and y are the same numbers as above (the orignal  numbers from "#groot (hdx,y)" in menu.lst)  So  for example if  menu.lst originally contained "#groot (hd1,0)", you need to do

```
sudo grub
root (hd1,0)
setup (hd1)
quit 
```

Step 3 Restore the MBR of the internal drive (You need to have a working Internet  connection for this step. For other options how to fix the MBR  see FixMBR in my signature):

If you do not  have the "universe" repositories enabled:
Go to Systems-> Administration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)
Click on Close (twice)

Next in a terminal type:

```

sudo apt-get update

sudo apt-get install ms-sys

sudo ms-sys -m /dev/sda 
```

Here /dev/sda needs to be replace by the actual   name for the hard drive containing your Windows partition. Typically it will be /dev/sda or /dev/hda. If you do not know  the correct  name, type "sudo fdisk -l" in a terminal (not at the grub prompt). Looking at the output you should be able to figure out the correct name.

Step 4  Change your boot order.

Reboot. At boot-up enter the Bio's Setup. (For example on a Dell you will have to press the "F2" key  immediately after the computer restarts.) 
 Set the boot order such that the external hard drive containing Ubuntu is first,  and the internal drive containing Windows is second.

That's it. Now if you boot with the external drive plugged in you should get the
grub menu. If the external drive is  unplugged you should boot directly into windows.

If you  run into problems or you have a question, reply to this thread and post the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

**  Boot from LiveCD **

If you are not able not boot into Ubuntu, you still can use this HowTo by booting from the Ubuntu LiveCD, but Step 1 needs some modification.

Step 1 from LiveCD:  

Go to Places->Computer. Double-click the icon for   your  Ubuntu partiton. (If you have a separate boot partition. double click the boot partition instead)  You should now have an icon for the Ubuntu partition with the label "disk" on you Desktop. (Although it might be "disk-1" or "disk-2" if it took you more than one try to find the Ubuntu Partition)

Open a terminal (Applications->Accessories->Terminal) and type

```
cd /media/disk/boot/grub
```
If the label for  the Ubuntu partition was disk-1, use  "cd /media/disk-1/boot/grub" instead.
If you have a separate boot partition, use  "cd /media/disk/grub".

```
sudo cp menu.lst menu.lst.backup

gksudo gedit menu.lst
```
(the "l" in menu.lst is a  lower case L, not the number one)

This creates a backup of "menu.lst" and  opens it in a new window.
Look for the lines

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hdx,y)

Of course the exact   "title" depends on your version of  Ubuntu.
Here x and y are some numbers. Typically this would be "root (hd1,0)"

Change 

root (hdx,y)

to   root (hd0,y)

So for example "root (hd1,0)" needs to be changed to "root (hd0,0)"

Save  and close  the file.

Since you were not able to boot into Ubuntu there is some chance that the "root (hdx,y") line in menu.lst was wrong. To verify that (hdx,y) actually is correct:

```
sudo grub 
```
and at the "grub>" prompt:
```
find /boot/grub/menu.lst 
```
(use "find /grub/menu.lst" if you have a separate boot partition)

This should return "(hdx,y)" (with x and y as above) 
If you have more than one version of linux on your computer, the output might list several (hd?,?). Just make sure that (hdx,y) is one of them.



If (hdx,y) was not listed, you have to  edit  "root (hd0,y)" in menu.lst so that "y" matches the output from "find /boot/grub/menu.lst". So if the output of  "find" was (hd3,4), use "root (hd0,4)"). Also in the rest of the instruction  always  use the output from "find" for "(hdx,y)".

To exit grub:
```
 quit
```

This completes Step 1 from the LiveCD.  Carry out Step 2-Step 4 from the  regular HowTo. This should allow you to boot into Ubuntu. Once you booted into Ubuntu, do Step 1 from the regular HowTo. Otherwise you won't be able to get in Windows  when the external drive is plugged in, and you will run into problems after the next kernel   update.

---

### Post by K.Mandla on 2007-12-25
Moved to Installation and Upgrades.

---

### Post by kylewhite on 2007-12-28
after i enter "sudo cp menu.lst menu.lst.backup" it responds ever so nicely by telling me "cp: cannot start "menu.1st": no such file or directory"

sorry im an ubuntu dummy

---

### Post by meierfra on 2007-12-28
kylewhite:  It's menu.lst  ("I' is a lowercase L, not a one)

---

### Post by meierfra on 2007-12-28
kylewhite:  If that did not solve the problem, post the output of 

"ls /boot/grub"

---

### Post by aaronblood10 on 2007-12-28
I followed the instructions, and it didn't change anything. I still need to have the external hard drive plugged in to boot to anything. I use Vista, so I modified the Vista/Longhorn section because that is what I would select at boot time to boot into windows.


> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       14333   104580096    7  HPFS/NTFS
/dev/sda4           14333       14594     2097152    f  W95 Ext'd (LBA)
/dev/sda5           14333       14594     2096128   dd  Unknown

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112414806   83  Linux
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout         10

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
# kopt=root=UUID=a5d125ae-60d9-47bf-8275-d9603d54632e ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a5d125ae-60d9-47bf-8275-d9603d54632e ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a5d125ae-60d9-47bf-8275-d9603d54632e ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista/Longhorn (loader)
root            (hd1,2)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title           Microsoft Windows XP Embedded
root            (hd0,4)
savedefault
makeactive
chainloader     +1



---

### Post by meierfra on 2007-12-28
> I followed the instructions, and it didn't change anything. I still need to have the external hard drive plugged in to boot to anything. I use Vista, so I modified the Vista/Longhorn section because that is what I would select at boot time to boot into windows.


Couple of question

 1) If  you set the bios to boot from the external drive, does the grub menu appear and are you able boot into Ubuntu and  Vista? 

2)  What happens when you boot with the external drive unplugged? Do you still get a grub error.

If the answer to 1) is yes,  then it seems that only Step 3 did go wrong and you just need to fix the MBR of your internal drive. Click on FixMBR in my signature.

---

### Post by aaronblood10 on 2007-12-28
If the external hard drive isn't plugged in then I get a grub error no matter what. If it is plugged in, then I can boot into Ubuntu or Windows.

---

### Post by meierfra on 2007-12-28
aaronblood10: Then you just need  to fix  the MBR. Click on FixMBR in my signature. It will give you a couple of more options to do that (other than the method in Step 3)


But I'm curious why Step 3) failed:

Did you get any error message  during step 3?   
Did you use  "sudo ms-sys -m /dev/sda" or did you replace "/dev/sda" by something else? 
Did you have a working internet connection?

---

### Post by aaronblood10 on 2007-12-28
Dang...I can't do the FixMBR until I get back from visiting home for Christmas where I have my installation CDs.
Answer to your questions:
No error message that I saw.
I used "sudo ms-sys -m /dev/sda"
Yes, my internet was working just fine.

---

### Post by meierfra on 2007-12-28
aaronblood10:  You might  try  Step 3) again.

Also there are other method's to fix the MBR. Just google.

---

### Post by aaronblood10 on 2007-12-28
Weird. I tried step 3 again, and it worked. I wonder what went wrong. I guess the world will never know.

---

### Post by meierfra on 2007-12-28
> Weird. I tried step 3 again, and it worked.

Good news. 

> I wonder what went wrong. I guess the world will never know.

Happens  all the time.   Could have been anything.

---

### Post by meierfra. on 2008-05-14
There is a small problem with  Step 3 in this  howto for Ubuntu 8.04 users:

ms-sys is not in the ubuntu 8.04 repositories. But it can be installed via a debian package:

[http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys")

For other ways to  carry out Step 3 click on FixMBR in my signature.

---

### Post by Apresmode on 2008-05-24
> **meierfra. said:**
> There is a small problem with  Step 3 in this  howto for Ubuntu 8.04 users:

ms-sys is not in the ubuntu 8.04 repositories. But it can be installed via a debian package:

[http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys")

For other ways to  carry out Step 3 click on FixMBR in my signature.

First of all, THANK YOU!  It seems that everywhere i looked had some partial version of this, but did not have everything that I actually needed.  So thanks for putting up such a complete how to.  You might want to add this bit about getting "ms-sys" into the guide if possible.  I searched forever for a way to solve the problem, and everything told me to just activate the universe repository, which i had done.  It wasn't until i found your guide and later comment that I was able to fix it.  

For those that have 8.04 and can't find "ms-sys", follow that link above and choose your download.  You will be given a list of mirrors.  Open up Software Sources, click on the Third-Party Software tab, and choose Add.  This opens up a place to enter the mirror site you found earlier.  Type in "deb http://<the mirror site address> etch main", and click Add.  I got an error and chose Close, but was still able to find "ms-sys" in the Synaptic Package Manager after all of that.  After following the rest of the instructions everything worked fine.  I hope that helps

---

### Post by Bruener on 2008-05-24
How do I know what type of architecture to download?

---

### Post by meierfra. on 2008-05-24
Just follow the advice of Apresmode in the post before yours. Then you can search for ms-sys in  the Synaptic Package Manager and only one package will appear.

---

### Post by Bruener on 2008-05-24
When I try to add the software source it gives me this error.

/code
GPG error: [http://packages.debian.org](http://packages.debian.org) etch Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://packages.debian.org/etch/i386/ms-sys/download/dists/etch/main/binary-i386/Packages.bz2](http://packages.debian.org/etch/i386/ms-sys/download/dists/etch/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.
/code

I am unable to find it in the package manager also and it gives the same error.

---

### Post by meierfra. on 2008-05-24
I got a similar message, but  the package still appeared in synaptic. Did you click on reload before you search for "ms-sys".  You might also try to directly download the package via the above link. Unless you have a 64bit processor, pick the i386 version.

Actually I recommend  removing  "debian etch main" from the sources list after you got "ms-sys" installed. I got  some broken package with "debian etch main" enabled (But they disappeared again when I disabled it.)

---

### Post by Bruener on 2008-05-24
The manual install did the trick. Im going to try th reboot now. Hopefully be back soon. =)

Windows loaded up w/o my ghetto portable HD powered on (i.e. internal in a portable case). Lets hope linux starts now. Brb.

---

### Post by Bruener on 2008-05-24
Hm, it seems that when I start my computer it always resets my internal HD to my first on boot order. Oh well, I can always just siwtch it on power up. Thanks a ton for fixing my boot up error. =)

---

### Post by meierfra. on 2008-05-24
> Oh well, I can always just siwtch it on power up.


If you have Windows XP  you could give [WinGrub ]("http://users.bigpond.net.au/hermanzone/p9.html") a try. 

And if you have Vista, try EasyBCD (see my signature)

---

### Post by Apresmode on 2008-05-24
> **meierfra. said:**
> I got a similar message, but  the package still appear in synaptic. Did you click on reload before you search for "ms-sys".  You might also try to directly download the package via the above link. Unless you have a 64bit processor, pick the i386 version.

Actually I recommend  removing  "debian etch main" from the sources list after you got "ms-sys" installed. I got  some broken package with "debian etch main" enabled (But they disappeared again then a disabled it.)

I removed that as well.  I am very new to Linux (about 3 days now) but saw that it seemed to be screwing some suff up.

---

### Post by txflatt on 2008-06-26
Help... I can't log into my windows now!

I installed Ubuntu onto a removable hard drive... 

map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet


************

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc3ecc3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004638af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6998    56211403+  83  Linux
/dev/sdb2            6999        7301     2433847+   5  Extended
/dev/sdb5            6999        7301     2433816   82  Linux swap / Solaris

---

### Post by drs305 on 2008-06-29
See this link:
[URL="http://ubuntuforums.org/showthread.php?p=3995006"]HowTo: Cannot boot windows without external hard drive plugged in
[/URL]

---

