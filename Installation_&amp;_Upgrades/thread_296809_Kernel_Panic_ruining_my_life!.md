---
title: "Kernel Panic ruining my life!"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Arjunus on 2006-11-10
I recently upgraded my ubuntu to the new edgy kernel. unfortunately after the common routinue of downloading the new upgrades and hitting restart my linux dies...

upon resart or booting up a host of lines comes up ending with the horrific line "kernel panic...". Now I am a total Noob at linux so could someone please explain to me how to fix it or when the patch to fix it wil come out. I found out through the forums that it has something to do with people's processors. I am currently running a Intel Celeron 2.5, people with certain AMDs also having problems. But my neighbour with Intel Pentium is running the new version smoothly.

I cant survive in windows much longer!!

---

### Post by James- on 2006-11-10
im having the same problem I upgraded my xubuntu with the apt-get dist-upgrade (did it twice) and apon reboot I get a KERNEL PANIC , unknown block

---

### Post by AgenT on 2006-11-15
Assuming that the kernel giving you problems is 2.6.17-10-generic (x86). Assuming your root partition / is on /dev/hda1.

NOTICE: Instructions below say to use su, if this fails, use sudo with the next line below the su command instead like so: sudo mkdir....

Boot your favorite Debian (based) LiveCD and start a terminal (Knoppix is always reliable):
```
su -
mkdir -p /media/ubuntu
mount /dev/hda1 /media/ubuntu
chroot /media/ubuntu
```Now do a test:
```
echo "bbb" < /dev/null
```If you do not receive an error, continue. If you do receive an error, something is wrong with your permissions. Make sure you were root before you executed chroot!
```
apt-get update
apt-get install --reinstall linux-image-2.6.17-10-generic
exit
cd /
umount /media/ubuntu
shutdown -r now
```Reinstalling the linux-image package not only reinstalls all the files, but also updates a lot of programs that may be causing the kernel panic.

---

### Post by kthakore on 2006-11-18
NO matter how many times I reinstall the kernel image it still doesn't work. 
The only difference is that my root drive handle was changed on the edy upgrade 

it was 

/dev/hda2

now it is

UUID=ffa7d5fe-a8b5-437e-8dc7-84a87a07cfe7 

I donno why but the fstab says it was change on upgrade to edgy. What can I do?

---

### Post by kthakore on 2006-11-18
AgenT when I Do reinstall the linux-image I get this error

```
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=ffa7d5fe-a8b5-437e-8dc7-84a87a07cfe7'
User hook script /sbin/update-grub failed at /var/lib/dpkg/info/linux-image-2.6.17-10-generic.postinst line 1201.

```

---

### Post by kthakore on 2006-11-19
here is my fstab file 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
# UUID=ffa7d5fe-a8b5-437e-8dc7-84a87a07cfe7 / ext3 defaults,errors=remount-ro 0 1
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
#/dev/hda1 -- converted during upgrade to edgy
# UUID=b52c59ad-cdeb-4fc6-922c-9f8bf1335cb3 /media/storage ext3 defaults 0 0
/dev/hda1 /media/storage ext3 defaults 0 0
/dev/hdc        /media/cdrom0   auto user,noauto     0       0

```

and here is my menu.lst file

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
# kopt=root=UUID=ffa7d5fe-a8b5-437e-8dc7-84a87a07cfe7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash elevator=cfq

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
title           Ubuntu, kernel 2.6.17-10-generic-custom
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=ffa7d5fe-a8b5-437e-8dc7-84a87a07cfe7 ro quiet splash elevator=cfq
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=ffa7d5fe-a8b5-437e-8dc7-84a87a07cfe7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=UUID=ffa7d5fe-a8b5-437e-8dc7-84a87a07cfe7 ro quiet splash elevator=cfq
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=UUID=ffa7d5fe-a8b5-437e-8dc7-84a87a07cfe7 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title           Ubuntu, kernel 2.6.15-27-686-custom
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


```

even when I get rid of the uuid and switch back to /dev/hda2 my kernel still has a panic saying it can't load the file system. Please help

---

### Post by AgenT on 2006-11-19
You have two kernels installed. Does the second one also give you a kernel panic? If not, when your system is loaded without trouble in this second kernel, can you give the output of this:
```
sudo fdisk -l /dev/hda
```(notice that this is a lowecase -L, not an uppercase i)

You also have 8 (not counting memtest) entries in your grub.conf, can you be very specific in mentioning which ones are giving you the error. Please test them all. Give your output by mentioning all the "title" tags that give you the error.

UPDATE: Those UUID strings *were* changed when you upgraded to Edgy. Starting with Edgy, fstab uses UUID instead of /dev/ because UUID provides much better tracking of your hardware. In short, if you were to replace a hard drive on /dev/hda with a new one, that new one would have the same entry (/dev/hda). Using UUID, this would NOT happen. The major advantage is that the system can keep much better track of hardware changes. This is similar to the USB problem that plauged Linux years ago (and still plagues Windows) until udev came along and made UUID-like USB entries popular.

---

### Post by kthakore on 2006-11-19
here is the uotput for fdisk

```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12748   102398278+  83  Linux
/dev/hda2           12749       18820    48773340   83  Linux
/dev/hda3           18821       19457     5116702+   5  Extended
/dev/hda5           18821       19457     5116671   82  Linux swap / Solaris

```

in the grub menu the ones with the -custom are kernel that work with /dev/hda2 and not its uuid conterpart. 

MY kernel 2.6.15-27-686 works with uuid enable in fstab
my kernel 2.6.15-27-686-custom works with /dev/hda2 enabled infstab
my kernel kernel 2.6.17-10-generic-custom doesn't work when /dev/hda2 is enable in fstab
my kernel 2.6.17-10-generic doesn't work when uuid is enabled in fstab

basically kernel 2.6.17-10-generic always gives me a kernel panic because it cannot read the fs, wether I use uuid or /dev/hda2

---

### Post by AgenT on 2006-11-19
> **kthakore said:**
> here is the uotput for fdisk

```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12748   102398278+  83  Linux
/dev/hda2           12749       18820    48773340   83  Linux
/dev/hda3           18821       19457     5116702+   5  Extended
/dev/hda5           18821       19457     5116671   82  Linux swap / Solaris

```in the grub menu the ones with the -custom are kernel that work with /dev/hda2 and not its uuid conterpart. 

MY kernel 2.6.15-27-686 works with uuid enable in fstab
my kernel 2.6.15-27-686-custom works with /dev/hda2 enabled infstab
my kernel kernel 2.6.17-10-generic-custom doesn't work when /dev/hda2 is enable in fstab
my kernel 2.6.17-10-generic doesn't work when uuid is enabled in fstab

basically kernel 2.6.17-10-generic always gives me a kernel panic because it cannot read the fs, wether I use uuid or /dev/hda2
Why are you booting off of /dev/hda2 and not /dev/hda1? /dev/hda1 is bootable, /dev/hda2 is not (look at your fdisk output).

From your fstab output, /dev/hda1 is suggested to be a mounted filesystem (why hda1?!) and hda2 the root filesystem (again, why not hda1??). Your fstab and fdisk output do not match up! If hda2 is really what needs to be booted, hda2 needs to be set as bootable.

---

### Post by kthakore on 2006-11-19
I was double booting with windows before which was on hda1 and ubuntu on hda2. I got rid of windows and made hda1 an ext3 nad because I wanted to keeping using my ubuntu install I didn't change the hdas. I want to boot from hda2 how do I make it bootable.

---

### Post by AgenT on 2006-11-19
> **kthakore said:**
> I was double booting with windows before which was on hda1 and ubuntu on hda2. I got rid of windows and made hda1 an ext3 nad because I wanted to keeping using my ubuntu install I didn't change the hdas. I want to boot from hda2 how do I make it bootable.
```
sudo fdisk /dev/hda
a (toggle bootable flag)
2 (select partition)
p (make sure /dev/hda2 has the boot flag now)
w (write and exit)
```

---

### Post by zgornel on 2006-11-19
To make it bootable go into GPartEd, right-click the partition, go to manage flags and select the "bootable" option. I'm curious if this works, mine is not bootable and I have no problem booting (grub in mbr).

---

### Post by kthakore on 2006-11-19
the hda2 is bootable now but the kernel still panics saying it cannot mount fs

```
 Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12748   102398278+  83  Linux
/dev/hda2   *       12749       18820    48773340   83  Linux
/dev/hda3           18821       19457     5116702+   5  Extended
/dev/hda5           18821       19457     5116671   82  Linux swap / Solaris

```

---

### Post by AgenT on 2006-11-19
> **kthakore said:**
> the hda2 is bootable now but the kernel still panics saying it cannot mount fs

```
 Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12748   102398278+  83  Linux
/dev/hda2   *       12749       18820    48773340   83  Linux
/dev/hda3           18821       19457     5116702+   5  Extended
/dev/hda5           18821       19457     5116671   82  Linux swap / Solaris

```
Have you tried reinstalling the kernel? Try:
```
sudo apt-get remove --purge linux-image-generic linux-image-2.6.17-10-generic
apt-get update
sudo apt-get install linux-image-generic
```What is the output of:
```
ls /usr/src/
ls /boot/
ls /lib/modules/
```

---

### Post by kthakore on 2006-11-19
I reinstall -generic

here is the 

/usr/src

```
ATI
fglrx-kernel-2.6.15-27-686_8.28.8-1+2.6.15-27.48_i386.deb
fglrx.tar.bz2
linux
linux-2.6.18.1.tar.bz2
linux-2.6.18.2
linux-2.6.18.2.tar.bz2
linux-headers-2.6.15-26
linux-headers-2.6.15-26-386
linux-headers-2.6.15-27
linux-headers-2.6.15-27-386
linux-headers-2.6.15-27-686
linux-headers-2.6.17-10
linux-headers-2.6.17-10-generic
linux-OLDVERSION.1159482325
linux-OLDVERSION.1159482644
linux-OLDVERSION.1160856218
linux-OLDVERSION.1162061243
linux-OLDVERSION.1162702795
linux-OLDVERSION.1162702941
linux-OLDVERSION.1163872893
modules
rpm

```

and  /boot/

```
abi-2.6.15-27-686         initrd.img-2.6.17-10-generic
abi-2.6.17-10-generic     memtest86+.bin
coffee.bmp                sarge.bmp
config-2.6.15-27-686      sid.bmp
config-2.6.17-10-generic  System.map-2.6.15-27-686
debian.bmp                System.map-2.6.17-10-generic
debianlilo.bmp            vmlinux-dbg-2.6.17-10-generic
grub                      vmlinuz-2.6.15-27-686
initrd.img-2.6.15-27-686  vmlinuz-2.6.17-10-generic

```


and ls/lib/modules
```
2.6.15-26-386  2.6.15-27-386  2.6.15-27-686  2.6.17-10-generic  fglrx

```

---

### Post by kthakore on 2006-11-19
and the reinstall didn't work it said a new error saying that compression not understood and that fs can't be mounted

---

### Post by AgenT on 2006-11-19
> **kthakore said:**
> and the reinstall didn't work it said a new error saying that compression not understood and that fs can't be mounted
You are upgrading from Debian? 

Are you upgrading/downgrading from another release (or distro)?

Where did you get 2.6.18 kernel? That is not in the Edgy repositories.

What is the output of:
```
cat /etc/apt/sources.list
```

---

### Post by kthakore on 2006-11-19
I am upgrading from ubuntu dapper. I was going to compile the 2.6.18 kernel myself from kernel.org.

---

### Post by AgenT on 2006-11-19
> **kthakore said:**
> I am upgrading from ubuntu dapper. I was going to compile the 2.6.18 kernel myself from kernel.org.
Why do you have those debian, sid, and sarge files in /boot/?

And you never actually have an exact error report. What is the exact error? What does it say? When exactly does it happen? Does the kernel get loaded at all? Does it happen when grub initiates the kernel?

And you never posted your sources.list output.

---

### Post by Andrew1963 on 2006-11-19
I am trying to install kubuntu onto my laptop - a Packard Bell EasyNote with a 1.2 GHz processor and 512M RAM.  It has a 50G disk, which is currently partitioned as follows:

hda1: hidden VFAT volume with Windoed Restore (8G)
hda2: NTFS with windows 2K Pro               (16G)
hda5: Linux swap                            (0.5G)
hda6: SuSE Linux /                            (8G)
hda7: /home                                  (14G)

My problem - with both Ubuntu and Kubuntu - is that when I reboot using the install CD it gets no further than the initial boot up when I select install.  I can't use any of the fixes listed, because I haven't even installed Ubuntu.Anyone got any solutions ?

Andrew

---

### Post by kthakore on 2006-11-19
```
Why do you have those debian, sid, and sarge files in /boot/?
```

donno. and what files indicate that

```

And you never actually have an exact error report. What is the exact error? What does it say? When exactly does it happen? Does the kernel get loaded at all? Does it happen when grub initiates the kernel?

```

it doesn't boot here is the error message

```

[17179574.02400]invalid compressed format (err=2)
[17179574.02400]kernel panic - not syncing:VFS:Unable to mount root fs known - block(0,0)

```

```
And you never posted your sources.list output.
```

oops srry here is the sources

```

## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu/ edgy main
deb-src http://archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ edgy restricted

deb http://archive.ubuntu.com/ubuntu/ edgy universe

deb http://archive.ubuntu.com/ubuntu/ edgy multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu/ edgy-security main
deb-src http://archive.ubuntu.com/ubuntu/ edgy-security restricted main multiverse universe #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ edgy-security restricted

deb http://archive.ubuntu.com/ubuntu/ edgy-security universe

deb http://archive.ubuntu.com/ubuntu/ edgy-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ edgy-updates restricted

deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe

deb http://archive.ubuntu.com/ubuntu/ edgy-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted

deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ edgy-backports universe

deb http://archive.ubuntu.com/ubuntu/ edgy-backports multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main

# PLF - Collection of Non-Free Proprietary Codecs & Applications
# deb http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free


# WINE - Windows API for Linux
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

# Skype - VoIP Software
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Opera - Web Browser
deb http://deb.opera.com/opera/ etch non-free


##############################
### Automatix Repositories ###
##############################

deb http://www.getautomatix.com/apt edgy main

## created by automatixrepo3
deb http://wine.lowvoice.nl/apt edgy main

deb http://www.beerorkid.com/compiz/ edgy main
deb http://xgl.compiz.info/ edgy main
deb-src http://xgl.compiz.info/ edgy main

## Beep Media Player with bmp

deb http://files.beep-media-player.org/packages/ubuntu edgy main universe

## Engage 
deb http://soulmachine.net/edgy/ unstable/

## gaim 2.0

deb http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse
deb http://ubuntu.beryl-project.org edgy main-edgy

## for xvid screencapture

deb http://www.jarre-de-the.net/computing/debian/ stable main


```

---

### Post by AgenT on 2006-11-19
> **Andrew1963 said:**
> I am trying to install kubuntu onto my laptop - a Packard Bell EasyNote with a 1.2 GHz processor and 512M RAM.  It has a 50G disk, which is currently partitioned as follows:

hda1: hidden VFAT volume with Windoed Restore (8G)
hda2: NTFS with windows 2K Pro               (16G)
hda5: Linux swap                            (0.5G)
hda6: SuSE Linux /                            (8G)
hda7: /home                                  (14G)

My problem - with both Ubuntu and Kubuntu - is that when I reboot using the install CD it gets no further than the initial boot up when I select install.  I can't use any of the fixes listed, because I haven't even installed Ubuntu.Anyone got any solutions ?

Andrew
Your problem has nothing to do with a kernel panic and this thread is about kthakore's problem. Please be kind to your fellow human beings and do not hijack threads. Instead, create a new thread about your problem. This will not only benefit others but also yourself as it will give you much more exposure to people that can help you.

---

### Post by AgenT on 2006-11-19
Just for your information: [noparse]```
[/noparse] tags should be used when entering code or commands, when quoting, use [noparse][quote][/noparse] tags.

> **kthakore said:**
> donno. and what files indicate thatIn /boot/ you have files named debian, sid and sarge.

[code]
[17179574.02400]invalid compressed format (err=2)
[17179574.02400]kernel panic - not syncing:VFS:Unable to mount root fs known - block(0,0)

```That helps a lot actually. Can you give the full output (in code tags)? Either there is some problem with your hardware and the kernel, your kernel related files are bad or grub is not correctly configured or installed.

> **kthakore said:**
> oops srry here is the sources
.....
That sources.list looks okay.

Before going into kernel and grub configurations, try this:
```
sudo apt-get -f install
sudo apt-get dist-upgrade
sudo apt-get upgrade
sudo apt-get kubuntu-desktop (if this is a kubuntu install)
sudo dpkg --configure -a
```If any of the above try to reconfigure or install anything, rerun all the above steps after every reconfigure or install.

Here is something that may help you out:
[http://kerneltrap.org/node/4677](http://kerneltrap.org/node/4677)

---

### Post by kthakore on 2006-11-19
Oh.. sorry about the quote thing. 

```
[17179574.02400]invalid compressed format (err=2)
[17179574.02400]kernel panic - not syncing:VFS:Unable to mount root fs known - block(0,0)
```

this is the only error I get and then my computer does nothing.

> Before going into kernel and grub configurations, try this:

what should I do in the configurations and how do I config the kernel?

and thank you very much for helping me so far, I really appreciate it.

---

### Post by AgenT on 2006-11-19
> **kthakore said:**
> this is the only error I get and then my computer does nothing.But there must be something happening before that, correct? What log file are you getting that error from? If you are copying from the screen, copy the output of these logs:
```
 debug
kern.log
messages
syslog
```Here what you can do: restart your computer and try booting into the kernel with a problem. Get an error. Wait about a minute and reboot into a working kernel. Now check all those logs and copy/paste the timeframe that happened from you turning on your computer until you receive the error. All logs have a time stamp.

To make all of this really easy, there is a log viewer: System -> Administration -> System Logs. You can highlight then Edit -> Copy and paste it into a file. Then paste your log output into this forum but include them in quote tags and post each one in separate tags so they are easier to view.

> **kthakore said:**
> what should I do in the configurations and how do I config the kernel? I do not understand what you are asking. Are you asking about the commands I suggested you try? Did you try them? Did anything happen? Or are you asking about my comment about configuring the kernel related files and grub?

---

### Post by kthakore on 2006-11-19
I did as you said but I can't seem to find and record of the kernel that isn't working in the logs you said. I reboot at 10:58 and was in the -generic kernel till 23:01 after that I restarted the computer with the working kernel.

here is debug from that time:

[http://pastebin.com/828603](http://pastebin.com/828603)

here is kern.log

[http://pastebin.com/828602](http://pastebin.com/828602)

here is messages

[http://pastebin.com/828600](http://pastebin.com/828600)

here is syslog

[http://pastebin.com/828599](http://pastebin.com/828599)


as for this 

> Are you asking about the commands I suggested you try? Did you try them? Did anything happen? Or are you asking about my comment about configuring the kernel related files and grub?


I was thought you wanted me to change menu.lst and the kernel config with something

---

### Post by AgenT on 2006-11-20
> **kthakore said:**
> I did as you said but I can't seem to find and record of the kernel that isn't working in the logs you said. I reboot at 10:58 and was in the -generic kernel till 23:01 after that I restarted the computer with the working kernel.You are running this in Qemu? Now you are having this same problem on your real computer, correct?

> **kthakore said:**
>  I was thought you wanted me to change menu.lst and the kernel config with somethingYou are correct, but I also wanted you to run those other commands. Also, try this:
```
sudo apt-get install --reinstall busybox-initramfs
sudo apt-get install --reinstall initramfs-tools
sudo apt-get install --reinstall module-init-tools
```Then try this and post the full output:
```
sudo grub
find /boot/grub/stage1
quit
```And try installing another Edgy kernel:
```
sudo apt-get install linux-image-386
```
Now reboot into this new 386 kernel. Does it give you problems?

---

### Post by kthakore on 2006-11-20
It worked!!! Hurrah!!! Thank you so much!!!

---

### Post by AgenT on 2006-11-20
> **kthakore said:**
> It worked!!! Hurrah!!! Thank you so much!!!
Which step(s) worked?

Please answer so that anyone who has the same problem will be able to solve it.

---

### Post by kthakore on 2006-11-20
oops sorry first I purged the old kernel away
>  
sudo apt-get --purge remove linux-image-generic


then I rebooted into the working kernel and did

> 
sudo apt-get install --reinstall busybox-initramfs
sudo apt-get install --reinstall initramfs-tools
sudo apt-get install --reinstall module-init-tools


and then reinstalled the generic kernel
 and it worked.
Apperentaly the logs said there was something wrong with lilo although I don't know what that is.

---

### Post by AgenT on 2006-11-20
> **kthakore said:**
> oops sorry first I purged the old kernel away


then I rebooted into the working kernel and did



and then reinstalled the generic kernel
 and it worked.
Apperentaly the logs said there was something wrong with lilo although I don't know what that is.
lilo is a boot loader like grub. A boot loader loads your kernel. You can think of your computer startup sequence this way: BIOS boots Boot Loader -> Boot Loader boots Kernel.

However, you cannot have both lilo and grub installed at the same time.

---

### Post by kthakore on 2006-11-21
Although I can boot into the kernel now, I still get some freezes where would I look to find the error messages for thats.

---

### Post by AgenT on 2006-11-21
> **kthakore said:**
> Although I can boot into the kernel now, I still get some freezes where would I look to find the error messages for thats.
```
 /var/log/kern.log
```
Most system logs are stored in /var/log/. You can also try the System -> Administration -> System Log program and look at kern.log.

---

### Post by kthakore on 2006-11-21
it froze again and here is the kern.log for the time but it doesn't make any sense:

> Nov 21 09:12:09 localhost kernel: [17215677.824000] eth0: link down
Nov 21 09:12:12 localhost kernel: [17215681.020000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov 21 09:22:06 localhost kernel: [17216274.664000] loop: loaded (max 8 devices)
Nov 21 09:22:06 localhost kernel: [17216274.984000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Nov 21 09:22:06 localhost kernel: [17216275.044000] NTFS volume version 3.1.
Nov 21 16:40:06 localhost kernel: Inspecting /boot/System.map-2.6.17-10-generic
Nov 21 16:40:06 localhost kernel: Loaded 22825 symbols from /boot/System.map-2.6.17-10-generic.
Nov 21 16:40:06 localhost kernel: Symbols match kernel version 2.6.17.
Nov 21 16:40:06 localhost kernel: No module symbols loaded - kernel modules not enabled. 

notice the big jump in time > Nov 21 09:22:06 to Nov 21 16:40:06 that is when the computer was frozen and I came home and restarted it. What can I do? Again thanks for all your help.

---

### Post by kthakore on 2006-11-21
I had another freeze and its says this 

> Nov 21 21:03:49 localhost NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 21 21:03:52 localhost bonobo-activation-server (admin-4792): Passing command-line arguments in .server files is deprecated: "/usr/bin/tomboy --panel-applet"
Nov 21 21:08:32 localhost kernel: [17191343.416000] BUG: unable to handle kernel paging request at virtual address 13357098
Nov 21 21:08:32 localhost kernel: [17191343.416000]  printing eip:
Nov 21 21:08:32 localhost kernel: [17191343.416000] c01ca36e
Nov 21 21:08:32 localhost kernel: [17191343.416000] *pde = 00000000
Nov 21 21:08:32 localhost kernel: [17191343.416000] Oops: 0000 [#1]
Nov 21 21:08:32 localhost kernel: [17191343.416000] Modules linked in: binfmt_misc rfcomm hidp l2cap bluetooth speedstep_lib cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table cpufreq_powersave cpufreq_userspace sony_acpi dev_acpi battery ac button tc1100_wmi container asus_acpi sbs pcc_acpi video hotkey i2c_ec md_mod dm_mod lp ipv6 snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq tsdev rtc pcspkr evdev snd_via82xx snd_ac97_codec snd_ac97_bus via_rhine mii snd_pcm_oss snd_mixer_oss via_ircc shpchp pci_hotplug floppy via_agp agpgart snd_mpu401 serio_raw snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device irda snd soundcore crc_ccitt psmouse analog gameport parport_pc parport i2c_viapro i2c_core ext3 jbd ehci_hcd uhci_hcd usbcore ide_generic ide_cd cdrom ide_disk via82cxxx generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Nov 21 21:08:32 localhost kernel: [17191343.416000] CPU:    0
Nov 21 21:08:32 localhost kernel: [17191343.416000] EIP:    0060:[radix_tree_delete+14/544]    Not tainted VLI
Nov 21 21:08:32 localhost kernel: [17191343.416000] EFLAGS: 00210082   (2.6.17-10-386 #2) 
Nov 21 21:08:32 localhost kernel: [17191343.416000] EIP is at radix_tree_delete+0xe/0x220
Nov 21 21:08:32 localhost kernel: [17191343.416000] eax: d4be291c   ebx: c11c40a0   ecx: c0358128   edx: 00000e12
Nov 21 21:08:32 localhost kernel: [17191343.416000] esi: d4be2918   edi: 00000e12   ebp: d4be2918   esp: dff0fe04
Nov 21 21:08:32 localhost kernel: [17191343.416000] ds: 007b   es: 007b   ss: 0068
Nov 21 21:08:32 localhost kernel: [17191343.416000] Process kswapd0 (pid: 115, threadinfo=dff0e000 task=dff89a90)
Nov 21 21:08:32 localhost kernel: [17191343.416000] Stack: d4be291c 00000000 c03580e8 ffffffff dff0fe30 c03580e8 dff0ffa4 c01408bf 
Nov 21 21:08:32 localhost kernel: [17191343.416000]        dff0feb0 c11c4098 c01431ad 0000000e 00000001 c11c3ec0 c11c3ee0 c11c3f00 
Nov 21 21:08:32 localhost kernel: [17191343.416000]        c11c3f20 c11c3f40 c11c40a0 d4be2918 c03580e8 dff0ffa4 c013e33a c11c40a0 
Nov 21 21:08:32 localhost kernel: [17191343.416000] Call Trace:
Nov 21 21:08:32 localhost kernel: [17191343.416000]  <c01408bf> __pagevec_free+0x1f/0x30  <c01431ad> __pagevec_release_nonlru+0x5d/0x80
Nov 21 21:08:32 localhost kernel: [17191343.416000]  <c013e33a> __remove_from_page_cache+0x1a/0x40  <c0143f40> remove_mapping+0x30/0x70
Nov 21 21:08:32 localhost kernel: [17191343.416000]  <c0144805> shrink_inactive_list+0x545/0x6a0  <c01449f4> shrink_zone+0x94/0xf0
Nov 21 21:08:32 localhost kernel: [17191343.416000]  <c0144de6> kswapd+0x326/0x420  <c012a640> autoremove_wake_function+0x0/0x50
Nov 21 21:08:32 localhost kernel: [17191343.416000]  <c0144ac0> kswapd+0x0/0x420  <c0101005> kernel_thread_helper+0x5/0x10
Nov 21 21:08:32 localhost kernel: [17191343.416000] Code: 14 85 24 ed 45 c0 83 2d 20 ed 45 c0 01 5b c7 04 85 24 ed 45 c0 00 00 00 00 89 d0 c3 90 55 57 89 d7 56 53 83 ec 48 89 04 24 8b 28 <39> 14 ad 38 cc 3c c0 0f 82 6c 01 00 00 85 ed c7 44 24 0c 00 00 
Nov 21 21:08:32 localhost kernel: [17191343.416000] EIP: [radix_tree_delete+14/544] radix_tree_delete+0xe/0x220 SS:ESP 0068:dff0fe04

---

### Post by AgenT on 2006-11-21
This is too advanced for me. I can tell you how to do a lot of things but from your last post it looks like this is a bug between the kernel and your hardware and I am not an expert on the inner workings of the kernel. Now it could be that you are having hardware problems and have not realized it until now. The new kernel may be more picky or it may have a new feature, etc. There are a lot of possibilities.

If you say that your old kernel and the 386 kernel work fine, then definitely post this on launchpad. Post a bug report but make it very good and informative. Mention what works, what does not, how you got over not being able to boot, etc.

Also, do not spam the post with a lot of output. Instead, take all your long (over 10 lines) output and put them in individual files. Then attach them (you will have to attach them one-by-one) in your bug report. 

And make sure you select the actual kernel as the package you are having problems with (linux-source-* are the kernel names). The easier you make it for the Ubuntu developers the faster they will help you. Link to this forum in your  bug report but *do not* expect anyone to read it. Make your bug report post very thorough and very informative. Basically give all the information you have gathered in this thread and anything else you can add.

File your bug report in the [bug section of launchpad]("https://launchpad.net/distros/ubuntu/+bugs"). Good luck!

---

### Post by Darrious on 2006-11-30
I'm sorry to sort of post in this forum about my problem, but this looks like it is the most one producing results.

When I boot up my computer the Grub loads and it says this

```
Starting Up ...
             [17179573.840000] crc error
             [17179573.840000] Kernel Panic - not syncing: VFS: Unable to mount root fs on un-known-block(0,0)
             [17179573.840000]
```

Please help me. This is becoming a really BIG PROBLEM. There is no second choice for me to pick from in the Grub menu. I have been running the liveCD for 3 days now and I need to fix this problem. Just please post any advice that you might have.

---

### Post by GuiGuy on 2006-12-14
> **AgenT said:**
> Assuming that the kernel giving you problems is 2.6.17-10-generic (x86). Assuming your root partition / is on /dev/hda1.

NOTICE: Instructions below say to use su, if this fails, use sudo with the next line below the su command instead like so: sudo mkdir....

<snip>

Reinstalling the linux-image package not only reinstalls all the files, but also updates a lot of programs that may be causing the kernel panic.

Thanks- this should be a sticky. I came up against this Kernel Panic yesterday and was about to re-install. Your guide worked a treat. 

Regards

---

