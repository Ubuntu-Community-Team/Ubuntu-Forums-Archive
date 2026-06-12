---
title: "Multi Disk Booting Problem WinXP and Ubuntu 7.10"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by sparkymarlin on 2008-03-04
Hello, I have a question and I've looked over the forums here and googled the heck out of this thing with not much for results. 

I was sick of windows so I completely ditched it; Installed Ubuntu 7.10 on my Main hard drive.  A couple of weeks later I decided I should Install Windows XP Pro back on my Second Hard Drive (completely separate) and I did and that went fine, It said that it needed me to partition a small amount of space on my Ubuntu HD for some files, ok that was fine with me, it went though and everything was fine windows runs just like normal. 

My problem is that when restart my computer it auto-boots into Windows XP and I don't even get the option of going into Ubuntu and when I tried restarting and jamming F12 to get into my BIOS it just gave me a screen and asked what i wanted to boot off of.  It gave me a couple options none of them worked besides the Hard Disk, which auto-booted me into Windows XP.  

When I load my Live CD i can go into the computer and see my Ubuntu drive, I can click on it and go to Home>Ubuntu>Arrancar(User Name)>Desktop and all my stuff is still there. But I cannot for the life of me figure out how to get my computer to let me choose which OS I want.

Thank you in advance, and sorry for the long post. I hope I covered everything.  I'll check my post often to see if there is anything that I missed that anyone needs to see.

Thanks Again.

Brandon.

---

### Post by Th3Professor on 2008-03-04
Perhaps it'll work if you pick and choose the necessary steps (not all) out of this link:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by mikewhatever on 2008-03-04
Try this link --> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by sparkymarlin on 2008-03-04
Hello, me again. Below the quote is my update, The quote is for reference purposes. Thank you all.

> Now to reinstall GRUB. Open up Terminal (Applications, Accessories, Terminal) and type in:

sudo grub

GRUB - sudo grub

 

This will launch the GRUB application. Now type in:

find /boot/grub/stage1

GRUB - find grub

 

This will search for where GRUB has been installed, and you should get the result hd(0,0).

Change the active root to this location by typing in:

root (hd0,0)

 

Now we’re going to reinstall GRUB to the MBR rather than the Ubuntu partition.

If we were going to use the Windows XP bootloader then we’d reinstall GRUB to hd(0,0), but as we’re not, type in:

setup (hd0)

GRUB - reinstall grub to MBR

This restores GRUB to the MBR. Type in QUIT and then EXIT to get out of GRUB and Terminal respectively, then reboot the system. Ubuntu will load by default.

 
Modify the Boot Menu

What we need to do now is modify the GRUB boot menu to allow Windows XP to load. Boot the system into Ubuntu and go to Terminal. Type in:

sudo gedit /boot/grub/menu.lst

GRUB - MENU.LST

 

This loads the GRUB menu file (which is basically a text file) within GEdit.

Navigate down to the section which after “## ## End Default Options ##".

These are the individual menu items in the GRUB menu.

Ubuntu &amp; XP - GRUB MenuUbuntu & XP - GRUB Menu

 

To create a new entry, navigate down to the end of the list (although it can go anywhere really) and enter the following lines:

title Windows XP

root (hd0,1)

makeactivechainloader +1

GRUB - Windows XP boot option

 

This places an item in the boot menu to launch Windows XP from its own partition (hd0,1). 

Thank you for your replies. I did everything in the quote there and I am in Ubuntu now.  And I have a Boot menu working, but when I go down to Windows XP and hit enter, it doesn't do anything at all.  I have two seperate drives, one with a small partition on it and one with just XP.  So my windows XP is actually on /dev/hdb1 not /dev/hda2.  So i tried changing the part in the Gedit where it tells you to type in the...
> 
title Windows XP

root (hd0,1)

makeactivechainloader +1

and I changed it to read -- root (hd2,0) -- since my small parition shows up as /dev/hda2 so i assumed that changing the root to (hd2,0) would work, and it still doesn't, it says that no such partition exists.

Thanks for the help so far. :) It is greatly appreciated!

Brandon.

---

### Post by PmDematagoda on 2008-03-04
Could you please post the outputs of:-
```
sudo fdisk -l
```
and
```
cat /boot/grub/menu.lst
```

---

### Post by sparkymarlin on 2008-03-04
Here is the Information you asked for PmDematagoda.
> 
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37439451   83  Linux
/dev/sda2            4662        4865     1638630    7  HPFS/NTFS

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3649    29310561    7  HPFS/NTFS

And...
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
timeout         45

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
# kopt=root=UUID=ef51ddd4-9f73-4a46-a4ae-7a7557607f4f ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ef51ddd4-9f73-4a46-a4ae-7a7557607f4f ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ef51ddd4-9f73-4a46-a4ae-7a7557607f4f ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title           Windows XP
root            (hd2,0)
makeactivechainloader           +1

### END DEBIAN AUTOMAGIC KERNELS LIST


There you go. :) Thanks for the help.

Brandon.

---

### Post by mikewhatever on 2008-03-05
You Windows entry should look like this:
title Windows XP
root (hd1,0)
makeactive
chainloader +1

It's a good idea to move it to the very bottom of the file, because in debian kernel section, it will get deleted with every kernel update.

---

### Post by sparkymarlin on 2008-03-05
I just changed it to root (hd1,0) and I got into the boot menu and went down to Windows XP and hit enter, when I hit enter my screen sort of flashed quickly then just sat there at the boot menu. It still wouldn't boot into Windows. Ha-ha, just my luck, I have no idea whats going on.

Thank you for the responses and the help thus far!

Brandon.

---

### Post by froy02 on 2008-03-05
Windows would only work if it is on "C drive" so we have to fool windows thinking that it is in "C drive by mapping the drives as follows:

Your original windows entries:
title Windows XP
root (hd1,0)
makeactive
chainloader +1

Change it to these:
title Windows XP
root (hd1,0)
makeactive
map (hd1,0) (hd0,0)
map (hd0,0) (hd1,0)
chainloader +1

This is because windows is installed on your 2nd drive (per your post) which in 'windows speak' is 'D drive' so if we mapped it during grub loading windows would recognize it as 'C drive'.
After you make this change to your menu.lst make sure that the boot order is Ubuntu drive first.

---

### Post by mikewhatever on 2008-03-05
> **sparkymarlin said:**
> I just changed it to root (hd1,0) and I got into the boot menu and went down to Windows XP and hit enter, when I hit enter my screen sort of flashed quickly then just sat there at the boot menu. It still wouldn't boot into Windows. Ha-ha, just my luck, I have no idea whats going on.

Thank you for the responses and the help thus far!

Brandon.

Can you also post the output of <cat /boot/grub/device.map>.

---

### Post by sparkymarlin on 2008-03-05
> arrancar@Arrancar:~$ sudo cat /boot/grub/device.map
[sudo] password for arrancar:
(hd0)   /dev/sda
(hd1)   /dev/sdb

There is the output of that, and Froy02 i did what you said and i actually got a bit farther, it said starting up then it said "NTLDR Not Found; Press CRTL+ALT+DEL To Restart."

Thanks again guy :)

Brandon

---

### Post by froy02 on 2008-03-06
Okay try this then:
title Windows XP
root (hd1,0)
makeactive
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

The above would map the drives rather than the partitions.

---

### Post by sparkymarlin on 2008-03-06
Nope, i get the same error. NTLDR is missing. Thanks for the help Froy02, this is driving me nuts.

Brandon.

---

