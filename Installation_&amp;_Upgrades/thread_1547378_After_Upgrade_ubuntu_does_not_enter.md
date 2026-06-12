---
title: "After Upgrade ubuntu does not enter"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by gonsena on 2010-08-06
Hello friends this is my first thread, as I am new on the "linux" use i have not much idea about the codes and those stuff, although i am tiryng to learn day by day stuff.
At the begining it was hard to make de change from Windows to Linux, but then i could arrange myself to it.
I was using ubuntu 9.04 and after a while I decided to updated to 10.4, it download everything perfectly and updated (suposely) but when I reboot it appeared a screen and after that i could never enter to it again.

I let you here the text it appears and then the things I have tried.

root=UUID=654e334b-1964-46b6-a334-c760187277a5 ro quiet spalsh
Give up waiting for root device. Common problems
-Boor args (cat /proc/cmdline)
-check rootdelay = (did the system wait long enaugh?
-Misssing modules (cat/proc/modules; ls /dev)

Alert! /dev/disk/by-uuid/654e334b-1964-46b6-a334-c760187277a5 Does not exist. Dropping to a shell!


BusyBox v 1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)
Enter ´help´ for a list of nuilt in commands

(initramfs)





OK, this is what it appears, i have checked a few options to correcit, none of them succeed, so now im makeing a post so if anyone can help me directly.

I wait for an answer, by the way, i got the instalation cd (live cd) as i read it can be used or not.
HELP PLEASEE!!! :S

---

### Post by Rubi1200 on 2010-08-06
Hi and welcome to the forums :)
 
If I understand, you updated from 9.04 to 10.04 directly?
 
The correct way to upgrade is from 9.04 to 9.10 and then from 9.10 to 10.04
 
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
 
Since you have the LiveCD, please use it to boot the computer choosing to try Ubuntu in live mode. Do not choose to install.
 
Then click on the link at the bottom of my post and follow the instructions there.
 
Post the results back here and we will try and help you resolve this.
 
Good luck!

---

### Post by gonsena on 2010-08-06
Hi, thanks for the quick answer. 
I am doing the correct upgrade (or reading) 
the actual version i got on my pc is(given with the live cd):

    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 120.0 GB, 120060444672 bytes
255 cabezas, 63 sectores/pista, 14596 cilindros, 234493056 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x00f000f0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   230,002,604   230,002,542  83 Linux
/dev/sda2         230,002,605   234,484,739     4,482,135   5 Extended
/dev/sda5         230,002,668   234,484,739     4,482,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        654e334b-1964-46b6-a334-c760187277a5   ext3                                     
/dev/sda5        aa964837-89d3-4480-8162-5b72fe79fd76   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr2         /media/RuFiAnY_hot....   udf        (ro,nosuid,nodev,uhelper=hal,uid=999)
/dev/sda1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=654e334b-1964-46b6-a334-c760187277a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=654e334b-1964-46b6-a334-c760187277a5

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=true

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        654e334b-1964-46b6-a334-c760187277a5
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=654e334b-1964-46b6-a334-c760187277a5 ro quiet splash
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        654e334b-1964-46b6-a334-c760187277a5
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=654e334b-1964-46b6-a334-c760187277a5 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid        654e334b-1964-46b6-a334-c760187277a5
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=654e334b-1964-46b6-a334-c760187277a5 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        654e334b-1964-46b6-a334-c760187277a5
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=654e334b-1964-46b6-a334-c760187277a5 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic
uuid        654e334b-1964-46b6-a334-c760187277a5
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=654e334b-1964-46b6-a334-c760187277a5 ro quiet splash acpi=force
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid        654e334b-1964-46b6-a334-c760187277a5
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=654e334b-1964-46b6-a334-c760187277a5 ro  single acpi=force
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        654e334b-1964-46b6-a334-c760187277a5
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=654e334b-1964-46b6-a334-c760187277a5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=aa964837-89d3-4480-8162-5b72fe79fd76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  98.7GB: boot/grub/menu.lst
  98.7GB: boot/grub/stage2
  98.7GB: boot/initrd.img-2.6.28-19-generic
  98.7GB: boot/initrd.img-2.6.31-22-generic
  98.7GB: boot/initrd.img-2.6.32-24-generic
  98.7GB: boot/vmlinuz-2.6.28-19-generic
  98.7GB: boot/vmlinuz-2.6.31-22-generic
  98.7GB: boot/vmlinuz-2.6.32-24-generic
  98.7GB: initrd.img
  98.7GB: initrd.img.old
  98.7GB: vmlinuz
  98.7GB: vmlinuz.old

This is all that appeared.

---

### Post by Rubi1200 on 2010-08-08
One problem I see here is this:

 > Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.The latest version 10.04 uses GRUB2, but you have GRUB-legacy on the MBR (which is why you need to upgrade from 9.04, which uses GRUB-legacy, to 9.10, which uses GRUB2, before moving to 10.04, which also uses GRUB2).

I would suggest that either you go for a complete fresh install of 10.04 (unless there are files you must have) OR reinstall GRUB2 to the MBR.

Here is a guide for reinstalling GRUB2:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

Hope this helps.

---

### Post by ingeva on 2010-08-08
> **Rubi1200 said:**
> One problem I see here is this:

 The latest version 10.04 uses GRUB2, but you have GRUB-legacy on the MBR (which is why you need to upgrade from 9.04, which uses GRUB-legacy, to 9.10, which uses GRUB2, before moving to 10.04, which also uses GRUB2).

I would suggest that either you go for a complete fresh install of 10.04 (unless there are files you must have) OR reinstall GRUB2 to the MBR.

Here is a guide for reinstalling GRUB2:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Hope this helps.
I recognize this problem. It is caused by the system not finding the HDs. It is as if they don't exist.  I have a computer manufactured in 2004 (2 IDEs, 2 SATA), and it has this problem but the newer one from 2008 has two SATA disks (4 controllers) and does not have the same problem at all.
I think the trouble is a combination of BIOS and drivers. Maybe it's possible to get this resolved, but I have not found any solution to this date. For me, the only solutions seems to be to go back to the original 9.10, i.e. without the kernel upgrades (at least the last one, 2.6.31-22.).

---

### Post by gonsena on 2010-08-09
Hello, can I make a "DISupgrade"?? in fact my computer is from the old days, and maybe the bios is the problem.
The thing is that I have files i don want to erase, so formatting the pc it would be my latest choice...

Also I tried the other option that rubi gave me. 
It goes wrong by something like this:

```
ubuntu@ubuntu:~$ sudo grub-setup -d /media/disk/boot/grub /dev/sda1
sudo: grub-setup: command not found
ubuntu@ubuntu:~$ sudo grub-setup -d /media/disk/boot/grub -m /media/XXXXX/boot/grub/device.map /dev/sda
sudo: grub-setup: command not found
ubuntu@ubuntu:~$ 

```


Hope this have a solution!!!
I will wait for further instructions, as im now stucked.
Thank you.

---

### Post by Rubi1200 on 2010-08-09
Hi gonsena,
I am unsure why you decided to use Method 2??

Anyway, from the LiveCD try again using these commands and let's see if it works.

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Reboot and then run

```
sudo update-grub
```

Let us know if this helps.

---

### Post by gonsena on 2010-08-09
Hello Rubi, i tried both methods, but had no success with nither of them.
Now i tried the one you just posted.
Error again...
This is what it appears.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 ya está montado o /mnt está ocupado
mount: según mtab, /dev/sda1 ya está montado en /mnt
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

> mount: /dev/sda1 ya está montado o /mnt está ocupado
mount: según mtab, /dev/sda1 ya está montado en /mnt
This says it is occupied or already mounted.

Hope this helps.
Waiting for an answer. :D

---

### Post by Rubi1200 on 2010-08-09
First, go to System > Administration > GParted and make sure all partitions are umounted.
If you see a key icon next to a partition it is mounted. For the swap partition right-click and choose Swapoff. Exit GParted.

Open a terminal and try running the commands again, but make sure you enter the command only once. Press enter and wait for the prompt, then run the second command.

If you get no error messages, reboot the computer and when you are in Ubuntu then run the ```
sudo update-grub
``` command (not on the LiveCD)

If the second command does not work then try this:

```
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

Then reboot and run the update command.

Let me know what happens please.

---

### Post by gonsena on 2010-08-09
> **Rubi1200 said:**
> Hi gonsena,
I am unsure why you decided to use Method 2??

Anyway, from the LiveCD try again using these commands and let's see if it works.

```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```Reboot and then run

```
sudo update-grub
```Let us know if this helps.

Hi Rubi, I am trying my best...
this is what happend. 
when i mount the /dev/sda1 it works perfectly, 
but then it ask for the root to the directory, and after unmounting the disk the root it is just / and gives me an error.

I took some SS maybe im doing it wrong...
[ATTACH]165980[/ATTACH]
[ATTACH]165981[/ATTACH]

Please dont get mad :P im just 2 new in this matter :D:D

P.S. in the code : 
sudo grub-install --root-directory=/mnt/ /dev/sda 
I tried /, /mnt/ /mnt/boot, //mnt, /mnt/boot/grub.

---

### Post by Rubi1200 on 2010-08-10
Hi gonsena,
listen, one way or another we are going to help you sort this out. In the worst case scenario, you will have to do a reinstall of the whole system.

But first, I am getting the felling that you are not copying and pasting the commands into the terminal or you are trying to open other files?

Please, try this _exactly_ as I have it:

From the LiveCD go to a terminal and copy and paste this code:

```
sudo mount /dev/sda1 /mnt
```then hit Enter. Don't do anything else, just let the command run.

Then, at the next prompt copy and paste this command and hit Enter:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```If this does not work or you get error messages after it runs then try this code:

```
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
```Only try this if the previous command did not work.

Again, do not open anything else or try other commands.

If there are error messages, let us know.

Now, if the commands worked, meaning they completed and there were no error messages, restart the computer; don't forget to take the CD or USB out first.

If all is well you should now be able to use Ubuntu on the hard-drive.

Then, go to the terminal and run this:

```
sudo update-grub
```Ok?

Now, if for some reason what I said above did not work, use the LiveCD again and run the bootscript again; maybe we need to see the new results.

Don't worry; hang in there and we will try and help.

---

### Post by gonsena on 2010-08-10
Hi rubi, i have done this steps just copying and pasting the codes.
Unfortunately it still gives an error...

(first I check the gparticion o see if there was no key)  

This is the result.
I took another SS so it makes it easy.
[ATTACH]166090[/ATTACH]

Hope this helps to help me :D

---

### Post by Rubi1200 on 2010-08-10
Are you able to now boot into Ubuntu normally without the CD?

Try it and see what happens. 

If it works then run this from the regular Ubuntu:

```
sudo update-grub
```Let me know.

---

### Post by gonsena on 2010-08-10
nope, it still appears the same problem...
I tried 2 times and now im on the live CD again...

---

### Post by Rubi1200 on 2010-08-10
> **gonsena said:**
> nope, it still appears the same problem...
I tried 2 times and now im on the live CD again...
Ok, go to the terminal and copy and paste this:

```
 sudo -i
```then when you have the root shell type this:

```
grub
```and then

```
find /boot/grub/stage1
```Post the results back here please.

EDIT: very important; gonsena what version live cd are you using?

---

### Post by dougalkerr on 2010-08-10
You could try things this way. Please run the LiveCD and make copies of files you did not want to erase so that you can use them again after you get the system working again.

Once you have saved the files and any other important data (you might lose it all when you try to reinstall any operating system), then choose to install the system from the Icon on the Desktop or from the Item in the Menu list if you don't have a desktop icon.

When you get to a fresh install screen follow all the instructions till the partition editor and choose 'Manual' then delete the Linux partition that was created before and create it again with what ever disc size you want from the available space you have and give the Mount Point the name of / and with the default file structure type of ext3 or ext4 if this is already highlighted.
accept the changes and continue with the installation.
This way will allow you to have a fresh installation of the system you want and with the correct GRUB boot manager too.

The system should recognize your Windows installation too (if you have not deleted it) and you should then be able to choose once again between systems.

Good luck.

Dougal.

---

### Post by gonsena on 2010-08-11
Hi [dougalkerr]("http://ubuntuforums.org/member.php?u=732249"), It worked!! i reinstall the ubuntu 9.04 and now it works perfectly, just like before!!

Thank you very much!!!:):):)

Thanks Rubi also for the help!!

---

### Post by Rubi1200 on 2010-08-11
> **gonsena said:**
> Hi [dougalkerr]("http://ubuntuforums.org/member.php?u=732249"), It worked!! i reinstall the ubuntu 9.04 and now it works perfectly, just like before!!

Thank you very much!!!:):):)

Thanks Rubi also for the help!!

You are more than welcome :)

Just some friendly advice; next time you are thinking of upgrading ask here first. You could probably have avoided all this trouble if you had done so.

Anyway, good luck and enjoy!

---

### Post by gonsena on 2010-08-11
Yes, i just didn´t post just because i thought it was silly questions :D:D jeje
just 1 more thing, how can i add mi disk (the hard drive that was partiones as /) in PLACES? it desappear and the gpartition is not on system aplications

---

