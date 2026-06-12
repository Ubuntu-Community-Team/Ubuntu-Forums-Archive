---
title: "No windos XP after installing Ubuntu 8.04"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by Kron_Khal on 2008-08-31
Hello!

First, I want to say that installing Ubuntu just gave me a new PC. Amazingly fast browsing, easy to install programs, and a nice GUI. I was planning on buying a new PC for Vista, but no need now... :D Great job!

Now, the problem...

I installed Ubuntu to my PC. I decided to use the partition program built-in the Ubuntu CD. Selected the first "Guided" option, split the HDD in half and select Continue. Installation was all good. Restart the PC.

While I was reading the boot options when the PC restarted, it automatically started Ubuntu. installed related updates, and restart again. **When I tried to boot on Windows, I'm getting a black screen. No error message, no blue screen, nothing.**

Restarted and tried a BartPE CD I have, but it didn't boot neither.

I believe the problem is that Windows never did the "chkdsk" after the partition process (I have a 160 GB NTFS HDD), but I'm not sure. I have a Gateway Desktop PC, so I don't have the Windows installation CD to run the Recovery option.

I'm ready to use the "Recovery disks" shipped with the PC, but I know this can be fixed in some other way (all my docs are in a different partition, so no problem to re-installing WinXP).

This is what fdisk shows:

[COLOR="RoyalBlue"]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd979f11c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         419        4609    33664207+   7  HPFS/NTFS
/dev/sda2               1         418     3357553+   b  W95 FAT32
/dev/sda3            9259       19457    81923467+   7  HPFS/NTFS
/dev/sda4            4610        9258    37343092+   5  Extended
/dev/sda5            4610        9061    35760658+  83  Linux
/dev/sda6            9062        9258     1582371   82  Linux swap / Solaris

Partition table entries are not in disk order
[/COLOR]
Any help will be very appreciated!

P.S. I'm new to Ubuntu.

---

### Post by falcon61102 on 2008-08-31
Typically the main "recovery" disk for your computer is actually just your windows cd with a fancy label and maybe a new splash screen.  That should work as far as running chkdsk and possibly restoring your MBR if necessary.  Have you looked at your menu.lst to ensure the correct settings are there for windows?  If you could, post it here.  You can access it by typing the following in your terminal:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Kron_Khal on 2008-08-31
Thanks falcon61102 for the quick response!

The following is the result of the code you suggested:

[COLOR="RoyalBlue"]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=8669f062-ee53-4196-8931-df0029610172 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8669f062-ee53-4196-8931-df0029610172 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8669f062-ee53-4196-8931-df0029610172 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/COLOR]

Is it OK? Do I need to change anything?

---

### Post by falcon61102 on 2008-08-31
In the last section of code change:
```
root (hd0,1)
```
to:
```
root (hd0,2)
```

Then save and reboot.

When you restart, make sure you select the bottom line to boot your windows.

---

### Post by Kron_Khal on 2008-08-31
Done, but still not booting on Windows...

The following message appeared on the screen:

[COLOR="RoyalBlue"]Starting up...

NTLDR is missing
Press Ctrl+Alt+Del to restart
[/COLOR]
At least now we're getting a message... ;)

Question 1: What do you think the problem is?

Question 2: If I run the factory recovery disks, am I going to be able to boot Ubuntu again? Is it going to erase the GRUB?

Thanks.

---

### Post by Bucky Ball on 2008-08-31
Try this. Download, burn disc, boot from it.
[B]
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[/B]
Have a read there. That should get you up and running for now and teach you a bit more about how grub works.

---

### Post by falcon61102 on 2008-08-31
Ok, you may need to restore the windows MBR and then reinstall the GRUB.  You can either do that using the disks or try the Super GRUB Disk:
[www.supergrubdisk.org](www.supergrubdisk.org)

That's a small utility made for such tasks and generally works well.  

If you don't want to go through the process of downloading and using that, then boot up with your primary recovery disk and restore the Windows MBR.  Then boot up the Ubuntu LiveCD and reinstall the GRUB with:

```
sudo grub
root (hd0,4)
setup (hd0)
```

Then you should be good to go.  Just make sure that after you reinstall the GRUB, the changes that you made earlier are still reflected.

Here's a quick How-To that you can reference:
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

EDIT: Lol... I type too slow :)

---

### Post by Bucky Ball on 2008-08-31
Falcon - your signature is so true!

---

### Post by falcon61102 on 2008-08-31
Thanks.  Yeah, I thought it really fit for around here because that's pretty much how this place works.  Learn something one day and teach it the next.

---

### Post by fransy on 2008-09-02
Work around.....
XP doesn't boot.....2000 boots en gives you the posibility to delete and setup the harddisk partitions.
After it. reboot with xp and go.

Thanks for the reactions, it gave me the idea where to look.

---

### Post by Kron_Khal on 2008-09-02
Sorry for the delay in response but I wasn't able to test the procedures you suggested until tonight.

The following is a brief resume of what I tried:

I downloaded SGD and used it to restore Windows boot. Boot to XP was OK, and GRUB didn't appear. Then reboot and use SGD to restore GRUB... I received the message "SGD job done!" or whatever the message is. Reboot, and try Ubuntu: Works fine! Reboot and try XP: Not working... :(

Reboot with SGD CD and restore Windows boot (again). Windows XP boot normally (and again, no GRUB window at boot). Reboot with SGD, load Ubuntu and modify the GRUB (using a terminal application) with the code falcon61102 suggested. Reboot, got the GRUB back. Try Ubuntu: Works fine! Reboot, try XP: Nothing.

I'm booting to XP with SGD, but I'd like to make the GRUB work. Am I doing something wrong? What should I do next?

Thanks in advance for the help!

Kron Khal.

---

### Post by falcon61102 on 2008-09-02
Ok, the problem may be in your Boot.ini  Apparently NTLDR missing is the equivilant to the GRUB not knowing where your kernal is.  You should be able to access the Boot.ini from Ubuntu, it will be in the root directory of Windows, what would normally be your C:\ drive in windows.  If you could open that and copy it here, we may be able to help you edit it.

---

### Post by kaola_linux on 2008-09-02
I had the same problem also...Mine had UBUNTU 8.04 AMD64 installed first and I've tried to install xp...I had ubuntu on my first hard disk and xp on my second hard disk...I've tried Super Grub Disk but it will only make me boot on Linux after selecting the Auto something option there but after a restart, grub doesn't show up instead the windows bootloader...Anyone who has a kind heart help a newbie linux user like me?thanks in advance...

---

### Post by adrian15 on 2008-09-03
> **Kron_Khal said:**
> 
I downloaded SGD and used it to restore Windows boot. Boot to XP was OK, and GRUB didn't appear. Then reboot and use SGD to restore GRUB... I received the message "SGD job done!" or whatever the message is. Reboot, and try Ubuntu: Works fine! Reboot and try XP: Not working... :(

Here you are:
[http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Grub_solution](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Grub_solution)

adrian15

---

