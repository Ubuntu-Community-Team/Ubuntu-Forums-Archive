---
title: "Freeze on GRUB Screen Fresh Install 6.10"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by SpikeyLozenge on 2007-01-19
Hello!  thanks in advance to any help you can give me...

   I have loaded a fresh install of Edgy onto a Toshiba Laptop.  It will boot the Live CD fine, and I do a Full Erase, and Re-partition (I let the Installer partition the drive) and the install completes, tells me to eject the CD, and then it reboots.

   Upon the first load, it will freeze at a black screen displaying:
"GRUB _"

The Underscore will flash, but there is no disk activity, and it does not respond to any keystrokes.  I have let it sit for 15 minutes at this screen to make sure I wasn't just being impatient.

   I have re-loaded it 3 times to make sure it wasn't a faulty install.  I have Checked the Disk, and it does not fail any checksums.  I have done a Memory Check, and there were no failures either.  I have run a Hard Disk Check with a seperate utility, and there were no bad sectors there either.  Any suggestions?  I'm stumped!! 

Here are the Basic Specs, and link to the Toshiba Detailed Specs Page (PDF Warning.  Sorry!)

Satellite® M35-S456 
512 MB Ram
80 GB Hard Drive
2 Ghz Pentium Centrino (100Mghz FSB)
NVidia x5200 Portable (128 MB Ram)

[Detailed Specs PDF]("http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_M35-S456.pdf")

Thanks for any help you can give!

---

### Post by kebes on 2007-01-19
Hmm... some things to try:

1. Check grub.
-Boot into a LiveCD.
-Mount the hard drive. (If not already mounted.)
-Go look at the file "/boot/grub/menu.lst"
-Make sure it looks "normal." Compare with "menu.lst" files online or post it here. First off, the file should exist and within it you should see comments explaining the sections. Near the bottom you should see a section like:
```

title           Ubuntu, kernel 2.6.15-27-k7
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot

```


2. Reinstall Grub.
-Boot into the LiveCD.
-In a terminal, run "grub" or "grub-install." You should check the documentation for grub to figure out exactly what to type. For instance see this sub-section of the grub guide:
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)

The command for an IDE hard drive would usually be something like:
grub-install /dev/hda
(but again it depends on your exact drive mapping)


3. If the above doesn't work, you could always try installing LILO as the booloader instead of grub. See this thread I wrote:
[http://ubuntuforums.org/showthread.php?t=230384](http://ubuntuforums.org/showthread.php?t=230384)

For more information.


Hope that helps. If you need help with any steps (not sure how much experience with the commandline you have), feel free to post again with questions.

---

### Post by SpikeyLozenge on 2007-01-19
Thanks! I'll give this a try when I get home.   I'm still pretty Linux-Green, but the best way to learn is to dive in....  I've used DOS Ever since I was a kid, so command line interfaces aren't to scary.... even though you have WAY more power in linux it seems... haha.

---

### Post by SpikeyLozenge on 2007-01-19
Okay... I know this is stupid but...*Sigh* How do I mount the drive?

I started searching the site, and found instructions for the mount command, and I looked in the partition editor and saw the ext3 formatted partition was /dev/hda1.

but... where do I mount it to?  Once I have mounted it, where do I go to see the files?  If I go inside the Filesystem, is all that what is on the hard drive, or off the Live CD?  I'm sorry for not knowing more.... but I am trying to learn.  Thanks again anybody who can help.

---

### Post by kebes on 2007-01-20
> **SpikeyLozenge said:**
> Okay... I know this is stupid but...*Sigh* How do I mount the drive?

I started searching the site, and found instructions for the mount command, and I looked in the partition editor and saw the ext3 formatted partition was /dev/hda1.

but... where do I mount it to?  Once I have mounted it, where do I go to see the files?  If I go inside the Filesystem, is all that what is on the hard drive, or off the Live CD?  I'm sorry for not knowing more.... but I am trying to learn.  Thanks again anybody who can help.


First thing to do is check if it is already mounted! I think a LiveCD by default wants to put it in the "/media/" folder. So you can go to Computer > Filesystem > Media

And see what's there. If it's not mounted, then do this:



To mount a drive, go to a terminal (Applications > Accessories > Terminal) and:
1. First make a directory mount to:
cd /media/
mkdir drive

2. Now mount the device:
sudo mount /dev/hda1 drive



You should be able to then go into the directory (/media/drive/) and see everything that is on the partition "hda1"... In the example I used hda1 but your actual hard drive may be called something else (e.g. SATA drives would be called sda1 etc.). To find out about the partitions that exist do:
sudo fdisk -l

From the order and sizes you should be able to figure out which one is the right one.

Hopefully that makes sense (if not, feel free to ask again!)...

---

### Post by SpikeyLozenge on 2007-01-20
Here is the Code from my Menu.lst file:
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
timeout		3

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
# kopt=root=UUID=d893ee9d-59fb-430d-a92e-957e62d3c0b3 ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Different Kernel than you posted, but it looks to be in the the correct format according to the comments in the file.    I checked in the path specified in the file, and the kernals are there as well.

Any suggestions?

I'm going to try and re-install grub in the mean time... I guess we'll see!  Thanks for all the help!

---

### Post by kebes on 2007-01-20
Yup your "menu.lst" looks fine to me. Your root partition is /dev/hda1 so you could try
sudo grub-install /dev/hda1

Hope that works...

---

### Post by SpikeyLozenge on 2007-01-20
> **kebes said:**
> Yup your "menu.lst" looks fine to me. Your root partition is /dev/hda1 so you could try
sudo grub-install /dev/hda1

Hope that works...

When I try that command, I get an error that its not a valid device.  I tried it both Mounted, and Unmounted.  However, I noticed something odd during the install process.  When it gets to the install summary screen, it states that it is going to install Grub to (hd0).  Should this be (hda) instead?  I guess it couldn't hurt to chance it, so I'll give it a try and change that device.  I really appreciate all your help kebes!

I'll let you know what happens after the install.  If this doesn't work, I'll try to install Lilo.  Is there anything I need to do to 'uninstall' grub first?  What do I need to do to prep the system for it?  I have a pendrive if I need to transfer things to it (The wireless on the notebook doesn't work off the live CD, but thats to be expected I suppose)

I have to leave Sunday for a business Trip, I hope I can get it up before then! :p

---

### Post by SpikeyLozenge on 2007-01-20
Well That didn't work... Got to the end of the install, and then came up with:

Titlebar: Unable to install GRUB in (hda)
Executing 'grub-install (hda)' failed
This is a Fatal Error  
(OK)


So... that sucks.

---

### Post by SpikeyLozenge on 2007-01-20
Okay, More trouble.

I tried installing Lilo as per kebes suggestion, but have run into more problems.

I got through his tutorial up to the 'Aptitude install lilo' command.  It wouldn't resolve any network addresses when I chroot to the hard drive install.  In a new terminal (before chroot-ing), I can ping, and install it, but it installs lilo on the Live CD drives. 

So it seems I am stuck in the same boat... Grub has a problem somewhere, and I can't install lilo over the net.  is there a way to transfer the lilo install files to a USB drive?

I'll be taking the computer with me on my trip to try and get it working... so if anybody has any solutions, I'd love to hear them!  8)

---

### Post by SpikeyLozenge on 2007-01-21
> **SpikeyLozenge said:**
> Okay, More trouble.

I tried installing Lilo as per kebes suggestion, but have run into more problems.

I got through his tutorial up to the 'Aptitude install lilo' command.  It wouldn't resolve any network addresses when I chroot to the hard drive install.  In a new terminal (before chroot-ing), I can ping, and install it, but it installs lilo on the Live CD drives. 

So it seems I am stuck in the same boat... Grub has a problem somewhere, and I can't install lilo over the net.  is there a way to transfer the lilo install files to a USB drive?

I'll be taking the computer with me on my trip to try and get it working... so if anybody has any solutions, I'd love to hear them!  8)

Okay, I've narrowed part of the problem down.  I lose internet ability in the terminal screen the moment I chroot to the mounted install. 
```
ubuntu@ubuntu:/mnt$ sudo mkdir newfs
ubuntu@ubuntu:/mnt$ sudo mount /dev/hda1 newfs
ubuntu@ubuntu:/mnt$ sudo chroot newfs/
``` <- Here is the trouble area

After this command, I no longer have access to the internet.  I know on the original Install, It only detected the lo (loopback) network device... does that have any effect?  Since i've plugged in the network cable and rebooted, the new network device shows up (eth0).

I guess i'll re-install based on my current configuration.... and see what happens.

---

### Post by kebes on 2007-01-21
Okay, when I said to use the command:
sudo grub-install /dev/hda1

I should have said:
sudo grub-install /dev/hda

(Note the missing "1" off of the device path.) With grub this is identical to:
sudo grub-install /dev/hd0
(either should work...)

Still, if that doesn't work, there are more options:


I recently noticed that the Edgy Alternate Install CD gives the option to install LILO... thus if you could reinstall using this CD and select LILO instead of grub at the correct time during install.

If you don't want to reinstall all of Ubuntu, I'm pretty sure you could still use the Edgy Alternate Install CD... just boot to a console and then follow the command I mentioned (in my other thread) to install LILO.



If you're following [my previous thread]("http://ubuntuforums.org/showthread.php?t=230384"), and can't get LILO installed to the chrooted session (only into the LiveCD session), then try this:

Just after chrooting, the networking will stop working... however inside this new chroot, try restarting the network with:
/etc/init.d/networking start

(or use "/etc/init.d/networking restart" if you have to). This may reload the network in the chroot environment (since, as you said, this was not setup during your initial install).

---

### Post by SpikeyLozenge on 2007-01-22
> **kebes said:**
> Okay, when I said to use the command:
sudo grub-install /dev/hda1

I should have said:
sudo grub-install /dev/hda

(Note the missing "1" off of the device path.) With grub this is identical to:
sudo grub-install /dev/hd0
(either should work...)

Still, if that doesn't work, there are more options:


I recently noticed that the Edgy Alternate Install CD gives the option to install LILO... thus if you could reinstall using this CD and select LILO instead of grub at the correct time during install.

If you don't want to reinstall all of Ubuntu, I'm pretty sure you could still use the Edgy Alternate Install CD... just boot to a console and then follow the command I mentioned (in my other thread) to install LILO.



If you're following [my previous thread]("http://ubuntuforums.org/showthread.php?t=230384"), and can't get LILO installed to the chrooted session (only into the LiveCD session), then try this:

Just after chrooting, the networking will stop working... however inside this new chroot, try restarting the network with:
/etc/init.d/networking start

(or use "/etc/init.d/networking restart" if you have to). This may reload the network in the chroot environment (since, as you said, this was not setup during your initial install).

Okay, I tried installing with the Alternate CD, and I did not receive any prompt to install lilo instead... I may have missed something, but it was not prompted.  Is there something I should hit?

  Regardless, here may be a helpful bit of information:  When I boot to the Live CD, there is an option to boot from the first hard drive.  When I do this, it will load sucessfully into my installed session of 6.10.

  I'd be happy installing/fixing grub, or getting lilo installed.  It doesn't bother me so much, i'm having fun learning it, and tinkering.  

By the way, i started installing lilo, and after re-installing after the Live CD detected my network setups, the networking was functional in the chroot-ed directory as I suspected.  I got lilo installed, but it would not configure, stating that the Device ID didn't seem right, and that I should fix the fstab, or hand roll my own config file.  However, through the terminal I could not edit the files on the chroot-ed drive because I didn't own them.  I was logged in as ubuntu on the live cd, but when I tried to chown the files on the mounted drive, it stated that 'ubuntu' was not a user.

   I tried using gedit to edit the files,  but they were read only because I was not the root user.  that's why I tried the Alternate CD....

   Sorry if you are running out of options, This computer is being a pain in the ***! ](*,)

---

### Post by kebes on 2007-01-22
On the Alternate CD the option to install LILO doesn't appear by default... if one of the steps fails then you fall back to a screen where it lists all the install steps (and some alternates of install steps) and in that list after "install grub" is "install LILO". However the normal install will skip the "install LILO" if you install grub.

I'm not sure how to force it to bring you to this screen (I know it exists!) but perhaps at the stage where it is about to install grub you could select cancel or something. Try to make it fail!



The fact that you can use the install CD to boot from your hard disk is a very good thing! Once you're booted into your disk, then you should just be able to go:
sudo /etc/init.d/networking restart
sudo aptitude install lilo
sudo liloconfig

Does that work? If not, what exactly are the error messages it gives you? What does your "/etc/fstab" look like:
more /etc/fstab


Lastly, when you're getting the "don't have permission to write file" you should be able to go:
gksudo gedit whateverfile

This will open "gedit" with root power, so you'll be able to edit the file. In a normal environment you have to enter your password. In a LiveCD environment it should just let you do it.

---

### Post by SpikeyLozenge on 2007-01-23
> **kebes said:**
> On the Alternate CD the option to install LILO doesn't appear by default... if one of the steps fails then you fall back to a screen where it lists all the install steps (and some alternates of install steps) and in that list after "install grub" is "install LILO". However the normal install will skip the "install LILO" if you install grub.

I'm not sure how to force it to bring you to this screen (I know it exists!) but perhaps at the stage where it is about to install grub you could select cancel or something. Try to make it fail!



The fact that you can use the install CD to boot from your hard disk is a very good thing! Once you're booted into your disk, then you should just be able to go:
sudo /etc/init.d/networking restart
sudo aptitude install lilo
sudo liloconfig

Does that work? If not, what exactly are the error messages it gives you? What does your "/etc/fstab" look like:
more /etc/fstab


Lastly, when you're getting the "don't have permission to write file" you should be able to go:
gksudo gedit whateverfile

This will open "gedit" with root power, so you'll be able to edit the file. In a normal environment you have to enter your password. In a LiveCD environment it should just let you do it.

Okay!  When I tried to install Lilo on the system after booting into the hard drive off the CD, I got this:
```

david@ubuntu:~$ sudo aptitude install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libpng12-0 linux-image-2.6.17-10-generic xbase-clients xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-video-all xutils 
The following packages have been kept back:
  avahi-daemon capplets-data dbus dbus-1-utils evince firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnome-control-center 
  gnome-games gnome-games-data gnome-system-tools gnupg info 
  language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 libc6 
  libc6-i686 libdbus-1-3 libgimp2.0 libgnome-window-settings1 
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomevfs2-0 
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 
  libgsf-1-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7 
  libgtop2-common libkrb53 libmagick9 libmono-cairo1.0-cil 
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil 
  libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil 
  libnspr4 libnss3 libpoppler1 libpoppler1-glib libsoup2.2-8 
  libtotem-plparser1 linux-headers-2.6.17-10 
  linux-headers-2.6.17-10-generic mono-common mono-gac mono-jit 
  mono-runtime openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils python-uno screen tar totem 
  totem-gstreamer totem-mozilla ttf-opensymbol tzdata vino w3m x11-common 
  xorg xserver-xorg 
The following NEW packages will be installed:
  lilo 
0 packages upgraded, 1 newly installed, 0 to remove and 103 not upgraded.
Need to get 0B/343kB of archives. After unpacking 1098kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package lilo.
(Reading database ... 88029 files and directories currently installed.)
Unpacking lilo (from .../lilo_22.6.1-7ubuntu2_i386.deb) ...
Setting up lilo (22.6.1-7ubuntu2) ...

david@ubuntu:~$ liloconfig
LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.
    
    WARNING!
        Your /etc/fstab configuration file gives device UUID=1aff5d50-5a6e-4216-82f2-837295a6545a as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle. 

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.
david@ubuntu:~$ 
```

At the end, you can see the error I get when I try to configure it.  Here is a copy of my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1aff5d50-5a6e-4216-82f2-837295a6545a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=39fe5ea4-98ce-4467-a1d9-069a1be7dc16 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I'll wait a while to hear from you, and if I don't hear anything, I'll reload again, and see if I can make it fail... what have I got to lose?!  :roll: :p

---

### Post by kebes on 2007-01-23
Aha! I think I now see what the problem is. Your "fstab" looks wrong.... in fact it's probably this that is causing grub to fail also. (Too bad we didn't check this a long time ago!)

I've seen this happen before.. somehow the fstab gets set with hardcoded values, and then something on the system changes so the fstab doesn't make sense anymore. You need to rebuild a more normal fstab... one that doesn't have those "UUID=###" bits. For example, my fstab is like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /home           ext3    defaults        0       2
/dev/sda4       /media/data     ext3    defaults        0       2
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Notice the differences... some sort of upgrade or system change has inserted those UUID tags. You'll notice that whatever operation did this kept the older lines in the file, but commented out with # signs. So here's what you should do (in my opinion). First, make a backup of this current fstab. Then edit it. So in a terminal:
cd /etc/
sudo cp fstab fstab.backup
gksudo gedit fstab

Then change your fstab to look more like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/hda1              ext3    defaults,errors=remount-ro 0       1
/dev/hda5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Notice that all I did was uncomment the lines that started "/dev/hda" and erased the UUID junk. Save the file and then reboot. (Or maybe you'll need to reboot and retry installing LILO or whatever.) If this doesn't work you can revert to your older fstab.

If you have reason to believe that the designations /dev/hda1 and /dev/hda5 are wrong, then double-check with:
sudo fdisk -l

This will list the partitions that exist and this should let you figure out what those "/dev/hda" parts should be written as.


I think this is the base of the problem... let me know how it goes.

---

### Post by SpikeyLozenge on 2007-01-23
> **kebes said:**
> Aha! I think I now see what the problem is. Your "fstab" looks wrong.... in fact it's probably this that is causing grub to fail also. (Too bad we didn't check this a long time ago!)

I've seen this happen before.. somehow the fstab gets set with hardcoded values, and then something on the system changes so the fstab doesn't make sense anymore. You need to rebuild a more normal fstab... one that doesn't have those "UUID=###" bits. For example, my fstab is like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /home           ext3    defaults        0       2
/dev/sda4       /media/data     ext3    defaults        0       2
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Notice the differences... some sort of upgrade or system change has inserted those UUID tags. You'll notice that whatever operation did this kept the older lines in the file, but commented out with # signs. So here's what you should do (in my opinion). First, make a backup of this current fstab. Then edit it. So in a terminal:
cd /etc/
sudo cp fstab fstab.backup
gksudo gedit fstab

Then change your fstab to look more like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/hda1              ext3    defaults,errors=remount-ro 0       1
/dev/hda5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Notice that all I did was uncomment the lines that started "/dev/hda" and erased the UUID junk. Save the file and then reboot. (Or maybe you'll need to reboot and retry installing LILO or whatever.) If this doesn't work you can revert to your older fstab.

If you have reason to believe that the designations /dev/hda1 and /dev/hda5 are wrong, then double-check with:
sudo fdisk -l

This will list the partitions that exist and this should let you figure out what those "/dev/hda" parts should be written as.


I think this is the base of the problem... let me know how it goes.

Good Grief! That sounds like such an easy fix! haha.

I've since re-installed using Lilo (to get the system to prompt you from the get go, use the alternate CD, when booted, before selecting install, press f6 for Extra Options, then f6 again, and select 'Expert Mode'.   It takes a little clunking around, but there is an option to install lilo near the bottom, as well as all the other options.)

Also, *Drumrolls....* It works!  I installed with Lilo and it boots, but looks quite ugly during the boot process.  Once it hits the gnome start, its fine though.  (during the boot it throws up a bunch of errors and such that scroll the screen, but obviously no big deal since it boots....)


I think I may re-install AGAIN to get it to boot with grub.  No sense in making you do all this work without me seeing if it works!

I really appreciate all your help!  Now, to install nVidia Drivers, and I want to try out this 3D desktop Beryl Crazyness....  Any links for those? haha ;) 

Again, thanks for all your help.  I'll let you know how the re-(re-re-re....)install goes with grub, and fixing the fstab.  (and the part about the drive devices is correct, I've checked it enough times during other steps to have it almost memorized!):biggrin:

---

### Post by SpikeyLozenge on 2007-01-23
Well, changing the fstab didn't work for grub... but I got it working installing lilo in expert mode.  I'll just do that again.  Thanks for the help!  Let me know if you have any suggestions about the nvida drivers or Beryl stuff...

---

### Post by kebes on 2007-01-23
Glad that you got LILO installed! finally!

To install the nvidia driver you just need to install "nvidia-glx" from the repositories. A detailed tutorial is here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

To install Beryl there are lots of how-tos. The Beryl site has Ubuntu-specific guides that you can follow. Also the ubuntuguide has hints:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)


Get the nvidia driver working first. That should go smoothly (but you never know!). You can also install "automatix":
[http://www.getautomatix.com/](http://www.getautomatix.com/)

It will help you automatically install the top "most requested" things, like mp3 support, DVD support, nvidia driver, etc. Quite a useful app on a fresh install.


As always, feel free to post with questions!

---

### Post by SpikeyLozenge on 2007-01-23
> **kebes said:**
> Glad that you got LILO installed! finally!

To install the nvidia driver you just need to install "nvidia-glx" from the repositories. A detailed tutorial is here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

To install Beryl there are lots of how-tos. The Beryl site has Ubuntu-specific guides that you can follow. Also the ubuntuguide has hints:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)


Get the nvidia driver working first. That should go smoothly (but you never know!). You can also install "automatix":
[http://www.getautomatix.com/](http://www.getautomatix.com/)

It will help you automatically install the top "most requested" things, like mp3 support, DVD support, nvidia driver, etc. Quite a useful app on a fresh install.


As always, feel free to post with questions!

](*,)  *sigh* Seems I spoke too soon.... On the second boot, it locks up after logging in.

I am going to try and install by the normal method, and then install lilo after I boot it to the hard drive from the CD.

   Here is a question, do I need to uninstall grub before installing lilo?  if so, How?  do I delete files, or un-check it from the package manager?  since the system is loading again, I can't check if its in the packages now.

  So, to sum up, I'm going to install the normal way with the alternate CD to avoid any Live CD problems, Boot to the first hard drive using the CD, and then uninstall grub if needed, fix my fstab file, linstall lilo, config it, and then.... hopefully be done.

Let me know if you have any other things to try.  Thanks kebes!

---

### Post by kebes on 2007-01-24
Sorry I didn't respond right away.... In theory you should not have to uninstall grub. Installing LILO (and running lilofonfig) will overwrite the master boot record, and that's all that's needed. I don't think uninstalling grub will help... then again something strange is going on so it's worth a try if all else fails.

The plan you mentioned sounds like a good one. I have a question, however, does your fstab look "strange" after every reboot and/or reinstall? I wonder what it is that is always changing it...

Let me know how it goes.

---

### Post by SpikeyLozenge on 2007-01-24
> **kebes said:**
> Sorry I didn't respond right away.... In theory you should not have to uninstall grub. Installing LILO (and running lilofonfig) will overwrite the master boot record, and that's all that's needed. I don't think uninstalling grub will help... then again something strange is going on so it's worth a try if all else fails.

The plan you mentioned sounds like a good one. I have a question, however, does your fstab look "strange" after every reboot and/or reinstall? I wonder what it is that is always changing it...

Let me know how it goes.

Acutally, the fstab has not changed at all.  After each install it was in that odd format, but since I have 'fixed' it, it has stayed that way.

  Grub will not load no matter what I do.  When I boot off the CD, I stop the countdown to take a look at the boot commands (pressing 'e') and wrote down each line.  It matches letter for letter what is in my menu.lst file, but it won't boot unless i jumpstart it with the CD.

Now that it is installed, i'm going to try and get lilo installed again.  It seemed to run much slower when I did the Lilo install off the CD in expert mode.  Now that it was installed off the default installation, its much faster.  I removed grub from the package manager, and am going to try lilo again... and hope for the best.

I'm going to boot off a live CD, and follow the instructions you posted in the link.  I'll let you know how the configuration goes

---

### Post by SpikeyLozenge on 2007-01-24
Okay, here is the error I get during the configuration:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ cd /mnt/
ubuntu@ubuntu:/mnt$ sudo mkdir newfs
ubuntu@ubuntu:/mnt$ sudo mount /dev/hda newfs
mount: you must specify the filesystem type
ubuntu@ubuntu:/mnt$ sudo mount /dev/hda1 newfs
ubuntu@ubuntu:/mnt$ sudo chroot newfs/
root@ubuntu:/# mount /proc
root@ubuntu:/# mount -t sysfs none /sys
root@ubuntu:/# ls /dev/hd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5  /dev/hdc
root@ubuntu:/# liloconfig
LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.

You must do three things to make the Linux system boot from the
hard disk. Install a partition boot record, install a master boot
record, and set the partition active. You'll be asked to perform
each of these tasks. You may skip any or all of them, and perform
them manually later on.

This will result in Linux being booted by default from the hard disk.
If your setup is complicated or unusual you should consider writing your
own customised /etc/lilo.conf. To do this you should exit this configuration
program and refer to the comprehensive lilo documentation, which can be
found in /usr/share/doc/lilo/.

Install a partition boot record to boot Linux from /dev/hda1? [Yes] Yes

   ==========================================================================
Creating small lilo.conf and running lilo.
Use LBA32 for addressing big disks using new BIOS features ? [Yes] Yes

   ==========================================================================
Searching for installed kernels and updating image entries ...
The following is the list of the available bitmaps:

1. /boot/sarge.bmp
2. /boot/sid.bmp
3. /boot/coffee.bmp
4. /boot/debianlilo.bmp

Enter the number of the bitmap: 3
Warning: Unable to determine video adapter in use in the present system.
Warning: Video adapter does not support VESA BIOS extensions needed for
  display of 256 colors.  Boot loader will fall back to TEXT only operation.
Added Lin_2.6.17img0 *
Added Memory_Test+

A master boot record is required to run the partition boot record.
If you are already using a boot manager, and want to keep it,
answer "no" to the following question. If you don't know
what a boot manager is or whether you have one, answer "yes".
Install a master boot record on /dev/hda? [No] yes

   ==========================================================================
Installing MBR on /dev/hda
ERROR: install-mbr failed! Your system may not be bootable.
root@ubuntu:/# 
```

Please note that this is off a Live CD boot, and mounting my system, and chroot-ing to it.

...any other suggestions?  I can't believe it my self...  I wish there was more to the error than just that.  it doesn't help at all!

---

### Post by kebes on 2007-01-24
That error message is truly unhelpful! I guess you tried rebooting but it didn't work?

You said before that you could boot into your actual system using the CD (instead of booting into a LiveCD session). Try doing that instead, and see if installing LILO in that environment works.

---

### Post by SpikeyLozenge on 2007-01-24
> **kebes said:**
> That error message is truly unhelpful! I guess you tried rebooting but it didn't work?

You said before that you could boot into your actual system using the CD (instead of booting into a LiveCD session). Try doing that instead, and see if installing LILO in that environment works.

Tried running from the actual install, and get the same message.

.... Well Crap! haha

---

### Post by curiousnose on 2007-01-24
I also had the same problem. I just installed Ubuntu 6.10 Edgy Eft yesterday and then booted to Windows XP (triple boot). I partitioned my USB hard drive in Win XP because Ubuntu (and Linux based systems) can't write to NTFS. Somehow, Partition Magic 8.0 messed up and produced errors during the process. It gave me a button wherein I had no choice but to press OK to reboot. My PC froze after the POST. I was presented with a blinking cursor and I can't type anything.

I figured that I need to reinstall GRUB so I can have the Menu of Operating Systems back. I searched this forum and found one post as to how to go about restoring GRUB. Here's what I did to successfully reinstall GRUB:

[LIST=1]
[*]Restart PC and boot to the Ubuntu 6.10 Edgy Eft CD.
[*]When you reach the desktop, open a Terminal (Applications - Accessories)
[*]I assume that you're already granted a SuperUser (su) status, otherwise log in as root.
[*]Type in **grub** in the terminal. The GRUB prompt will appear.
[*]Type **find /boot/grub/stage1**. There should be a response similar to this - (hd0,0).
[*]After verifying the response, type in **root (hdx,x)** where x is the number corresponding the the response above. For example, root (hd0,5).
[*]Type **setup (hdx,x)** where x is the number coressponding to the response in procedure 5. This will write GRUB to the MBR.
[*]Type in **quit** to exit to GRUB.
[*]You may now to reboot to see the results.
[/LIST]

Reference: 

Subject: **[[COLOR="Red"]HOWTO: Restore GRUB (if your MBR is messed up)[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-24113.html")**
Posted by **wernst** on April 9th, 2005

---

### Post by SpikeyLozenge on 2007-01-24
> **kebes said:**
> That error message is truly unhelpful! I guess you tried rebooting but it didn't work?

You said before that you could boot into your actual system using the CD (instead of booting into a LiveCD session). Try doing that instead, and see if installing LILO in that environment works.

**[SIZE="6"]SUCCESS!!!!![/SIZE]** 


For whatever reason it didn't work before, but I loaded the alternate CD, set it in expert mode, and went through the install piece by piece, installed Lilo, and it BOOTS! MORE THAN ONCE!!!!  (I did load a MBR tool before, and wiped it clean before I did this... that 


Thank Goodness.... because I was getting to the end of my rope.

Anyway, I have updated the system software, rebooted a few times, and I am going to proceed and install the NVidia drivers, and all that...


 I just have ONE LAST QUESTION....( I Hope!!)

When booting, it States:
"Lilo (version numbers) Loading Linux.............................../ Etc /......................Done!"
And then a bunch of devices loading ,and a huge mess of stuff, and then it pops up to the login screen.

Is there any way to boot with the ubuntu splash screen instead?  Trivial, I know, but it looks much nicer when I want to show it off!

Thank you so much for all your help Kebes, you have been awesome.

---

### Post by SpikeyLozenge on 2007-01-24
Thanks for the tip curiousnose!  I have actually tried that a long time ago, but forgot to post anything about it.... its been a long week of troubleshooting with this system....  But thank you for posting a solution that wasn't here!  I've been pulling my hair out with this laptop.

---

### Post by kebes on 2007-01-25
Yah! Finally! I'm glad you got it working... because frankly I was running out of ideas!

As for a LILO splash screen... yes it's possible. You need to edit the file "/etc/lilo.conf" and then run the command "lilo" again to update changes (hopefully that will not break anything!...) The changes you need to make are something like what's described here:
[http://www.kde-look.org/content/show.php?content=17113](http://www.kde-look.org/content/show.php?content=17113)

I think the "lilo.conf" file has a commented-out line that reads "bitmap=/boot/sarge.bmp" or something like that. You can uncomment it and select from a coupld different bitmaps they provide. You can also find/create your own bitmap, but there are restrictions on the dimensions of course.

---

