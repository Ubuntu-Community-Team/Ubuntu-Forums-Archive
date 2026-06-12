---
title: "Dual Boot problem Vista Business/Ubuntu 7.10"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by eikichi on 2008-02-03
I am having problems booting into Ubuntu 7.10. I only manage to boot into recovery.

I have installed Vista Business on a WD250GB IDE drive which serves as Primary Master.

I then installed Ubuntu 7.10 on a WD160GB SATA drive which serves as Secondary Master.

The modifications on the menu.lst to achieve dual boot are as follows:

title  Windows Vista
rootnoverify (hd1,0)
map  (hd0,0) (hd1,0)
map  (hd1,0) (hd0,1)
makeactive
chainloader +1

Ubuntu recovery and Vista boots fine from the GRUB loader. Do note that I installed the Start up manager to change the grub theme, I don't know if that has caused any conflict. On BIOS I have set the IDE drive to boot first.

What seems weird to me is that Ubuntu is installed on a SATA drive and on the menu.lst the drive was shown as (hd0,0) instead of (sd0,0).

Regards,
Eikichi

---

### Post by nobody13 on 2008-02-03
Here's a snip from the Gentoo handbook. It should still work the same:

```
Understanding GRUB's terminology

The most critical part of understanding GRUB is getting comfortable with how GRUB refers to hard drives and partitions. Your Linux partition /dev/hda1 (for IDE drives) or /dev/sda1 (for SATA/SCSI drives) will most likely be called (hd0,0) under GRUB. Notice the parentheses around the hd0,0 - they are required.

Hard drives count from zero rather than "a" and partitions start at zero rather than one. Be aware too that with the hd devices, only hard drives are counted, not atapi-ide devices such as cdrom players and burners. Also, the same construct is used with SCSI drives. (Normally they get higher numbers than IDE drives except when the BIOS is configured to boot from SCSI devices.) When you ask the BIOS to boot from a different hard disk (for instance your primary slave), that harddisk is seen as hd0.

Assuming you have a hard drive on /dev/hda, a cdrom player on /dev/hdb, a burner on /dev/hdc, a second hard drive on /dev/hdd and no SCSI hard drive, /dev/hdd7 gets translated to (hd1,6). It might sound tricky and tricky it is indeed, but as we will see, GRUB offers a tab completion mechanism that comes handy for those of you having a lot of hard drives and partitions and who are a little lost in the GRUB numbering scheme.

Having gotten the feel for that, it is time to install GRUB. 
```


Your boot kernel and recovery kernel should be in the same place, at least mine are :

```

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-386 root=UUID=1ca578fe-d25a-4be3-9f13-51790ed331b2 ro quiet splash
initrd		/initrd.img-2.6.22-14-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-386 root=UUID=1ca578fe-d25a-4be3-9f13-51790ed331b2 ro single
initrd		/initrd.img-2.6.22-14-386
```

What errors do you have when you try to boot?

---

### Post by eikichi on 2008-02-03
I don't understand how that can help me, since when I choose Ubuntu recovery from GRUB, it  boots fine I assume that Ubuntu 7.10 which is the very same drive will also boot fine but it doen't.

When I choose Ubuntu 7.10 to boot I don't get any errors like the partition was not found etc or any sort of an error. The monitor flickers for a second and it just remains black. I do hear in the backgournd though the drive operating, like it's booting but nothing happens.

Is the Start up manager that I installed causing any problems?
Do you need any logs from the Ubuntu recovery?

Do take into account that I am new in Linux.

Regards, 
Eikichi

---

### Post by eikichi on 2008-02-03
My 7.10 and recovery mode kernels are in the same place, at the end of menu.lst i added the Vista one.

---

### Post by nobody13 on 2008-02-03
I though you were saying you were having trouble setting it up to boot correctly. If it's booting up with no screen you'll have to look at your graphic card. Maybe its going to a setting thats out of range for you monitor? Maybe there is no support for it in your current kernel. This could be past what I'm capable of helping with. Start by posting lspci, and listing your hardware. I might be helpful if you can you connect to it through another pc over your network.

---

### Post by confused57 on 2008-02-03
Here's part of my menu.lst:
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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=3

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false 
```

You might check if Startup Manager may have added themes or whatnot to load, by comparing your menu.lst with mine.
```
nano /boot/grub/menu.lst
```

I've never used Startup Manager, but you might check...if you created a backup of your menu.lst before installing SM, you could restore that...

---

### Post by eikichi on 2008-02-03
Hardware:
CPU: C2D E6600 @ 2.4GHz (stock clocked)
Mobo: Gigabyte P965-DS4 
VGA: 8800GTX (stock clocked)
Mem: 2x1GB DDR2 PC6400

I don't think that the problem is caused from my VGA since everything was fine before I tampered with the menu.lst

I will try unplugging my Windows drive from the system and removing the entry in menu.lst and see if I can boot properly into 7.10. Will let you now shortly.

Please be specific when asking me to post logs as I am not Linux literate. Thanks!

---

### Post by eikichi on 2008-02-03
@ Confused57

Indeed I made a backup copy of menu.list prior to installing Startup Manager but the SM hasn't added any entries on the menu.lst

---

### Post by confused57 on 2008-02-03
> **eikichi said:**
> @ Confused57

Indeed I made a backup copy of menu.list prior to installing Startup Manager but the SM hasn't added any entries on the menu.lst
If you haven't seen it already, this thread may have something that will help:
[http://ubuntuforums.org/showthread.php?t=295524](http://ubuntuforums.org/showthread.php?t=295524)

---

### Post by nobody13 on 2008-02-03
It looks like startup manager is just for splash screens. I'm going to installit and see what happens
If you were just trying to get your menu all you have to do is comment out hiddenmenu.

---

### Post by nobody13 on 2008-02-03
Didn't change anything you can try from recovery mode:

sudo apt-get remove startupmanager
sudo dpkg-reconfigure grub
You might also restore your origonal menu.1st and starting over fresh

---

### Post by eikichi on 2008-02-03
I trying removing the Windows entry and the one looking to read an image and unplugged the drive, still nothing. 

I then followed the above two commands to uninstall SUM and restore the menu.lst, still nothing.

I have come to the conclusion to believe that Ubuntu boots fine but it doesn't show me the Welcome screen to log in into my account. Because there is background noise and it feels like the drive is working properly like any other time.

---

### Post by froy02 on 2008-02-03
I have the same issue.  Your computer actually boots in the regular Ubuntu session but I think during the start up the OS is trying to detect the monitor which causes it to go black and shuts off during the detection process.  Then the OS thinks there is no monitor attached.  This happens on my old analog E790 Viewsonic.  

My solution is to move the mouse when I hear the clicking sound. It just then continue booting up.

Most older monitors shut off  when given a refresh rate that they can not display.

I also noticed that the resolution for the splash screen is different from my setting for the session.  Also the 'Preference->Screen Resolution'  and the System-> Administration-> Screen and Graphics' settings seem to have different setup files because the change in one is not reflected on the other. 

I have been using Ubuntu for only 5 months and I have been a DO$/Window$ guru since the 80's and so I have seen worse issues that's why I do not usually report 'little' things like that. It could be a graphic card setting issue.  It does not happen on my LCD monitor, but then the LCD has only one refresh rate at 60.

---

### Post by eikichi on 2008-02-03
Well I don't think that it is a monitor issue because when my monitor looses the signal the status LED starts to go on and off. In this case the LED remains solid green. The monitor doesn't go entirely black like it is turned off, it seems like it is illuminated.

Also everything worked fine before I installed SUM, so I believe that for some reason it just looses the spashscreen. #-o

As I read from the another post, SUM causes problem and tends to make the pc unbootable, now that it is out of the way it should work fine. Obviously I need to restore the system back to before the installaiton of SUM if there is a way to do that or find any other files that it altered.

---

### Post by confused57 on 2008-02-03
> **eikichi said:**
> Well I don't think that it is a monitor issue because when my monitor looses the signal the status LED starts to go on and off. In this case the LED remains solid green. The monitor doesn't go entirely black like it is turned off, it seems like it is illuminated.

Also everything worked fine before I installed SUM, so I believe that for some reason it just looses the spashscreen. #-o

As I read from the another post, SUM causes problem and tends to make the pc unbootable, now that it is out of the way it should work fine. Obviously I need to restore the system back to before the installaiton of SUM if there is a way to do that or find any other files that it altered.
Have you tried entering your username & password, even though you don't see the login screen?

If this doesn't work...when you boot to the blank screen, press "Ctrl+Alt+F1"...login if you get to a console, then enter:
```
startx
```
or
```
sudo /etc/init.d/gdm stop
startx
```

---

### Post by eikichi on 2008-02-03
Yes I tried the first time I encountered the problem but nothing happens.

I also tried the Ctrl+Alt+F1 but there is no change, I don't get a console. The screen remained as it was.

---

### Post by eikichi on 2008-02-04
Any other ideas?

---

### Post by confused57 on 2008-02-04
> **eikichi said:**
> Any other ideas?
Maybe this will completely remove start-up manager(from the thread I linked you to earlier):
[http://ubuntuforums.org/showpost.php?p=1936296&postcount=54](http://ubuntuforums.org/showpost.php?p=1936296&postcount=54)
if you do this from recovery mode, you shouldn't have to use sudo

---

### Post by eikichi on 2008-02-04
No it didn't help at all :( 

From the second command and onwards it said that the file didn't existed.

In case that it might be a VGA drivers setting issue as it was posted earlier, how will I uninstall and install the drivers again?

Or set the settings to default. If I remember correctly on the SUM i set the GRUB screen to be displayed 1280x1024, now that SUM is out of my system, it probably didn''t revert the changes back to 800x600 which is the default one (I think). My VGA is an nvidia 8800GTX.

I would like to eliminate all available options so I want to give that path a try. Thanks!

---

### Post by eikichi on 2008-02-04
OK Problem Solved :D:D

It was indeed a VGA setting issue(sort of), since uninstalling SUM didn't do the trick of reverting the changes on GRUB's resolutions, I decided to install it again. I manually changed GRUB's reso to 800x600 and 8bit color and tada! It's working!:popcorn:

But :lolflag: fixing the problem that way means that there is something wrong with my VGA drivers and somehow the pc seems to take more time to boot!

Any suggestions on that?

Thank you all for your help and time! I am now a very happy person :D

---

