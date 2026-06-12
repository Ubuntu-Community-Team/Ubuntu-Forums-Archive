---
title: "HELP - Kernel Update broke Edgy"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by Talako on 2007-02-10
Howdy,
    Thank god I decided to dual boot for this stuff.
I just updated the kernel, and I have seen that u guys are having difficulties, but it seems that you can all get into at least recovery mode. When I boot, it gives me an error that it
cannot mount the partition, an error 17 I think. I will try rebooting and write down the error after I post this. Has anyone encountered this problem? has anyone fixed it? I have an Edgy LiveCD, so i guess i can repair it from there, but i'm not sure.
Please help
Talako

---

### Post by shane2peru on 2007-02-10
> **Talako said:**
> Howdy,
    Thank god I decided to dual boot for this stuff.
I just updated the kernel, and I have seen that u guys are having difficulties, but it seems that you can all get into at least recovery mode. When I boot, it gives me an error that it
cannot mount the partition, an error 17 I think. I will try rebooting and write down the error after I post this. Has anyone encountered this problem? has anyone fixed it? I have an Edgy LiveCD, so i guess i can repair it from there, but i'm not sure.
Please help
Talako

I have the same issue!!!  This does not make me happy as I just (a few months ago) deleted windows!  I cannot get into my system, and the Super Grub Disk couldn't fix this issue.  I have a dapper live cd and am going to try and fix this, but this is really a sorry display of the Ubuntu that I know.  I'm needless to say not happy about this!

Shane

---

### Post by dabl on 2007-02-10
The kernel update seems to have broken the driver for my Logitech Quickcam.  Other USB devices seem to be OK (scanner and printer), but Camorama (which was working fine yesterday) now comes up with an error "Could not connect to video device (/dev/videoO).  Anyone else?  Any theories how to fix?

---

### Post by Talako on 2007-02-10
OK, rebooted, here's what the error message is:

Booting 'Ubuntu, kernel 2.6.17-11-386'
root (hd0,0)
   Filesystem type unknown, partition type 0x82
kernel /boot/vmlinuz-2.6.17-11-386 root=/dev/evms/hda4 ro quiet splash

error 17: cannot mount selected partition

press any key to continue...

"Where's the any key?" <-lol

then it goes into GRUB and lists all of the kernel verisons and XP, which is what i'm in now.

Shane: It isn't so bad, just relax and deal, sh** happens, and we cope, just take it easy and there'll be a solution 99% of the time. I'm not thrilled about this either, no offense, but trying to find a scapegoat only wastes our time.

---

### Post by shane2peru on 2007-02-10
Ok, I got my Ubuntu fixed.  However this still doesn't make me happy.  I can't believe I had to re-install grub to get it to work.  I booted a Live CD, open a terminal, mounted my boot partition, (hda1) which is the main part of my filesystem.  I mounted it like this ```
sudo mkdir /media/hda1
```  then ```
sudo mount /dev/hda1 /media/hda1
```then ```
sudo chroot /media/hda1
```
You will have to replace the hda1 with whatever your partition number is, or wherever you want to install grub.  I don't have a dual boot process, please double check where you are wanting to install grub, **DON'T JUST COPY AND PASTE ALL THESE COMMANDS IF YOU DON'T KNOW WHERE YOUR UBUNTU INSTALLATION IS!!!**  Next ```
sudo grub
```and in the grub window ```
find /boot/grub/stage1
```then```
root (hd0,0) 
```  that is where my Ubuntu is installed and where the booting is.  Next ```
setup (hd0)
```then```
quit
```  Rebooted and it worked like a champ.  Hope this helps.  

Shane

---

### Post by shane2peru on 2007-02-10
> **Talako said:**
> 
Shane: It isn't so bad, just relax and deal, **** happens, and we cope, just take it easy and there'll be a solution 99% of the time. I'm not thrilled about this either, no offense, but trying to find a scapegoat only wastes our time.
Well, it should work, and when this is my work machine, and I'm not dual booting, yes, it does ruffle my feathers a bit!  I'm not a newbie to this stuff, I dual-booted for over a year, and did many installs, re-installs.  When an update messes up my system that has been running fine for the past 3 months doesn't make me too happy, and I will really have to consider waiting on the next updates, until I have backed up my system, and that shouldn't be the case.  The updates should be fine, and not wreck the system.  Had I not been experienced, and installed grub a time or two, I probably would have been re-installing by now, and had to re-setup everything for the gazillionth time. Or restoring from my weekly backup.  I don't care to have to do those things.  Because an official update messed things up (I'm pretty careful about my repos!)

Shane

---

### Post by pay on 2007-02-10
> **Talako said:**
> OK, rebooted, here's what the error message is:

Booting 'Ubuntu, kernel 2.6.17-11-386'
root (hd0,0)
   Filesystem type unknown, partition type 0x82
kernel /boot/vmlinuz-2.6.17-11-386 root=/dev/evms/hda4 ro quiet splash

error 17: cannot mount selected partition
It seems to me that the kernel doesn't have support for your partition format. What filesystem are you using?

---

### Post by jlintz on 2007-02-10
sigh broke mine too

---

### Post by Talako on 2007-02-10
I am using ext3 for ubuntu and a shared partition, and fat32 for windows, I haven't messed with my filesystem, and I don't think it is a problem with GRUB. any ideas?

Shane: I probably should have kept my mouth shut, sorry.

---

### Post by Talako on 2007-02-10
I also can access the partitions from windows (I installed the driver for extX partitions) so that would lead me to believe that the filesystem is fine, but then what could it be?

---

### Post by shane2peru on 2007-02-10
> **Talako said:**
> I am using ext3 for ubuntu and a shared partition, and fat32 for windows, I haven't messed with my filesystem, and I don't think it is a problem with GRUB. any ideas?

Shane: I probably should have kept my mouth shut, sorry.

Talako,

No problem.  I do love Ubuntu, I was just a little disappointed in this update. 

    I'm thinking it is your grub.  I read another post where someone's grub was written incorrectly after the update (besides mine) Boot into the live CD and open a terminal, **Applications -> Accessories -> Terminal**  In the terminal you are going to need to type/paste this command, ```
sudo fdisk -l
```  Paste that results here.  After you paste that here, we should be able to walk you through this problem.  Also I noticed that your linux partition is hda4, so in the terminal, we need to type/paste this ```
sudo mkdir /media/hda4
``` then ```
sudo mount /dev/hda4 /media/hda4
```  and then finally ```
cat /boot/grub/menu.lst
``` and paste that results here as well, just the first one and the last one.

hopefully we can get you up and running.

Shane

---

### Post by Talako on 2007-02-11
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         255     2048256   82  Linux swap / Solaris
/dev/hda2   *        2678        5227    20482875    c  W95 FAT32 (LBA)
/dev/hda3            5228       14593    75232395   83  Linux
/dev/hda4             256        2677    19454715   83  Linux

Partition table entries are not in disk order

```
hda1 is my swap, hda2 is XP (not sure y its listed as 95, but not really an issue), hda3 is a shared partition, hda4 is Ubuntu
```

ubuntu@ubuntu:~$ cat /media/hda4/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color light-blue/black blue/dark-grey

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
# kopt=root=UUID=36c14f25-2b46-4c67-b355-c0ed8faeb47a ro
# kopt_2_6=root=/dev/evms/hda4 ro

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

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=/dev/evms/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=/dev/evms/hda4 ro single
initrd          /boot/initrd.img-2.6.17-11-386
boot

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda4 ro single
initrd          /boot/initrd.img-2.6.17-10-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/evms/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/evms/hda4 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/evms/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/evms/hda4 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Windows XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

---

### Post by shane2peru on 2007-02-11
> **Talako said:**
> 
hda1 is my swap, hda2 is XP (not sure y its listed as 95, but not really an issue), hda3 is a shared partition, hda4 is Ubuntu
```

ubuntu@ubuntu:~$ cat /media/hda4/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color light-blue/black blue/dark-grey

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
# kopt=root=UUID=36c14f25-2b46-4c67-b355-c0ed8faeb47a ro
# kopt_2_6=root=/dev/evms/hda4 ro

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

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=/dev/evms/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=/dev/evms/hda4 ro single
initrd          /boot/initrd.img-2.6.17-11-386
boot

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda4 ro single
initrd          /boot/initrd.img-2.6.17-10-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/evms/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/evms/hda4 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/evms/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/evms/hda4 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Windows XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

Ok, this seems a little odd to me.  Your boot menu has this listed as /dev/evms/hda4  I don't understand what the evms part is.  Here is what we are going to do.  When you boot up and your grub comes up, scroll down to the **Ubuntu, kernel 2.6.17-10-386** and hit 'e' this will allow you to edit this command,  It is not a permanent edit, just for testing purposes.  Then scroll down to this line: **kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/evms/hda4 ro quiet splash**  and hit the 'e' key to edit this line.  Edit the line by deleting the **/evms** part, it should look like this: ([COLOR="Red"]kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda4 ro quiet splash[/COLOR])  and then hit 'b' (I think it is to boot if not read the directions at the bottom of the screen to figure out what key boots.)  If it boots up then we will need to edit the menu.lst.  You will need to write that part down so you can remember it.  If it boots look this thread back up and follow these instructions:

Open the terminal **Applications -> Accessories -> Terminal** and type/paste:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```  That backs up your menu.lst in case we accidentally mess it up.  Now:```
sudo gedit /boot/grub/menu.lst
```  Now we need to find all those lines that have **/evms** and delete that part, so it should look like this:
```
kernel          /boot/vmlinuz-2.6.xx-xx-xxx root=/dev/hda4 ro single
```  The x's will represent whatever number is there. Don't change that part.  Just delete the **/evms** part.  Let me know if this works for you.  The part above doesn't boot into Ubuntu, let me know what the error message you get is.  I really believe this is the problem.

Shane

---

### Post by joebaker on 2007-02-12
EVMS is the Enterprise Volume Management Service.  It agrigates the functions of LVM into a set of utilities for managing filesystems (resizing partitions & the filesystems, and BBR  Bad Block Relocation which is my favorite benefit of EVMS).`
[http://evms.sourceforge.net/]("http://evms.sourceforge.net/")

I'll wait for a couple days to perform this update.  I also have a unique filesystem environment.  I have a LVM on top of raid 0 (2 drives) where /boot is inside the LVM.  It was setup with the alternate install cd of Edgy 6.10.

I need to be sure that a Live CD can see inside this filesystem.

Why doesn't Ubuntu simply add the new kernel rather than replace the old one, adding a line to the boot loader for the old kernel then making the new kernel the default?

-Joe Baker

---

### Post by fisherman783 on 2007-02-12
> **Talako said:**
> 
hda1 is my swap, hda2 is XP (not sure y its listed as 95, but not really an issue), hda3 is a shared partition, hda4 is Ubuntu

The error 17 is because GRUB is trying to boot from your swap partition.  I discovered this after the kernel update screwed up *my* system in a similar fashion.

> **shane2peru said:**
> When you boot up and your grub comes up, scroll down to the **Ubuntu, kernel 2.6.17-10-386** and hit 'e' this will allow you to edit this command,  It is not a permanent edit, just for testing purposes.  Then scroll down to this line: **kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/evms/hda4 ro quiet splash**  and hit the 'e' key to edit this line.  Edit the line by deleting the **/evms** part, it should look like this: ([COLOR="Red"]kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda4 ro quiet splash[/COLOR])  and then hit 'b' (I think it is to boot if not read the directions at the bottom of the screen to figure out what key boots.) 

You will also need to edit the line that says "root hd(0,0)" to read "root hd(0,3)" because your Ubuntu installation is on the fourth partition.  Otherwise, you will probably just keep getting error 17s.  I don't know anything about that EVMS business but, if you're lucky, maybe the change I suggested will be the only edit you need to make in order to get running again...

---

### Post by Talako on 2007-02-12
OK, today I'm at work (IT intern), and I have all day to mess with my laptop (comp having the issues) I read all of the things u guys said, and tried them, here is what I found:
1. deleting the EVMS and changing the hda line allows ubuntu to boot
2. leaving the EVMS line and changing the hda line allows ubuntu to boot
(won't bother not changing hda line, ubuntu is not on swap)
So here is my question: wtf is the difference if I have EVMS in or not? is one better than the other? will that change when I try booting into the new kernel?
later
Talako

---

### Post by Talako on 2007-02-12
I just changed the hda line in kenel 11 and it booted
same is true if I delete EVMS

---

### Post by IgnorantGuru on 2007-02-12
> **dabl said:**
> The kernel update seems to have broken the driver for my Logitech Quickcam.  Other USB devices seem to be OK (scanner and printer), but Camorama (which was working fine yesterday) now comes up with an error "Could not connect to video device (/dev/videoO).  Anyone else?  Any theories how to fix?

I haven't tried upgrading the machine that has a logitech webcam so I can't tell you.  Do you know what module you are using for it?

The pwc module is broken in edgy - I had to compile it from source to get it to work.  I don't know if that relates to your problem but you can read about it here
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090)

Here's how I got it to work
```

apt-get install build-essential
uname -r     #find out what kernel
apt-get install linux-headers-2.6.17-10-386    # gets -10 kernel headers
	
# Download http://www.saillard.org/linux/pwc/files/pwc-10.0.12-rc1.tar.bz2
# and extract it, go into folder as root
	
make
modprobe -r pwc
cp pwc.ko /lib/modules/2.6.17-10-386/kernel/drivers/media/video/pwc/pwc.ko.saillard
cd /lib/modules/2.6.17-10-386/kernel/drivers/media/video/pwc
mv pwc.ko pwc.ko.ubuntu
ln -s pwc.ko.saillard pwc.ko
depmod -a
modprobe pwc

```

But like I said that was the older (-10) kernel.  Might solve your problem though.

---

### Post by shane2peru on 2007-02-12
> **joebaker said:**
> 

Why doesn't Ubuntu simply add the new kernel rather than replace the old one, adding a line to the boot loader for the old kernel then making the new kernel the default?

-Joe Baker

Joe,  It adds one in case it doesn't boot, you can stick with the old kernel, and not use the new one.  However if it re-writes your entire menu.lst wrong, it doesn't matter anyway.  But it is supposed to be a security thing I think, so you should be able to boot up one way or another.

> **fisherman783 said:**
> 
You will also need to edit the line that says "root hd(0,0)" to read "root hd(0,3)" because your Ubuntu installation is on the fourth partition.  Otherwise, you will probably just keep getting error 17s.  I don't know anything about that EVMS business but, if you're lucky, maybe the change I suggested will be the only edit you need to make in order to get running again...

Good point fisherman!  I guess I missed that.  I'm not dual booting, so I couldn't remember what it was supposed to look like.

> **Talako said:**
> OK, today I'm at work (IT intern), and I have all day to mess with my laptop (comp having the issues) I read all of the things u guys said, and tried them, here is what I found:
1. deleting the EVMS and changing the hda line allows ubuntu to boot
2. leaving the EVMS line and changing the hda line allows ubuntu to boot
(won't bother not changing hda line, ubuntu is not on swap)
So here is my question: wtf is the difference if I have EVMS in or not? is one better than the other? will that change when I try booting into the new kernel?
later
Talako

Glad you got it working.  I can't be of much help to you with the EVMS thing, I don't know anything about it.  I didn't even know that it stood for whatever it was that it stood for that Joe mentioned above.  I would check out the link he posted and read it if I were you, and do a search for evms on the forums to see what others say about it.  

Shane

---

### Post by Talako on 2007-02-12
OK, I guess I'll just leave the EVMS in unless I find that anything is wrong with it, so far, so good, Ubuntu is back. Thanks guys!
Talako

---

### Post by ekravche on 2007-02-12
> **dabl said:**
> The kernel update seems to have broken the driver for my Logitech Quickcam.  Other USB devices seem to be OK (scanner and printer), but Camorama (which was working fine yesterday) now comes up with an error "Could not connect to video device (/dev/videoO).  Anyone else?  Any theories how to fix?

I have the same problem, the only fix is to roll back to 2.6.17-10-generic

---

### Post by shane2peru on 2007-02-13
> **ekravche said:**
> I have the same problem, the only fix is to roll back to 2.6.17-10-generic

Hey maybe I should try my camera now, and see if it works!  It used to work, but with that kernel it didn't work.  Maybe now it will!  :lolflag: 

Shane

I did say that joking, but guess what, My Logitec Camera WORKS!!!

---

