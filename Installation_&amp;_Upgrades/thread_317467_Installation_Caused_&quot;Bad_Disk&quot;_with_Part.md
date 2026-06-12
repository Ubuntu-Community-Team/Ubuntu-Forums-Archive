---
title: "Installation Caused &quot;Bad Disk&quot; with Partition Magic 2002"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by Juan Largo on 2006-12-12
I recently did an installation of Ubuntu 6.10 on a second hard disk (hdb).  First, I backed up a copy of the master boot record of my first hard disk (hda) because I wasn't sure whether Ubuntu would install GRUB on it and I wanted to be able to "undo" things if it did.

Anyway, I used Partition Magic 2002 to create three new partitions on the second hard disk.  Two ext2 partitions:  hdb7 for / and hdb8 for /home; plus hdb9 for a  Linux swap partition.  Although Partition Magic 2002 doesn't support ext3, I figured that Ubuntu would reformat hdb7, hdb8 and hdb9 to ext3 during the install process.

Next, I went through the Ubuntu "manual" installation by assigning / to hdb7, /home to hdb8, and swap to hdb9.  (I was afraid to let Ubuntu do things automatically, because I didn't want to "lose" the whole disk.  I also manually defined the mount points for all of the other partitions on hda and hdb.)

As I suspected, the Ubuntu installation procedure didn't offer me the option of installing GRUB on / and went right ahead with overwriting the mbr on hda .... arrrrrgh!  But what really made matters worse is that Partition Magic thinks the partition table on hdb is messed up and I get a "BAD DISK" error when Partition Magic starts and can no longer resize or modify hdb.  It may be that PM just doesn't recognize the ext3 format on hdb7, hdb8, and hdb9.  I have no trouble accessing files on any of these partitions, so the disk seems to be okay otherwise.

I don't know how to fix the "errors" on hdb that keep giving me the "BAD DISK" with PM.  PM asks if it's okay to apply fixes, but I'm afraid that would really mess up the disk.  Does anyone know how to safely "fix" the errors that PM thinks it found?  Or should I just ignore the errors and "upgrade" to a different partitioning tool?

By the way, there was a happy ending to the involuntary installation of GRUB on the MBR.  I used the back up copy of the master boot record to restore the original on hda and now the computer automatically boots into Windows like it did before.  (This makes my wife happy ... and if she's not happy, I'm not happy.)  If I want to boot Ubuntu, I use a bootable floppy that has a boot manager on it.  But I really wish that Ubuntu would give people the option of NOT installing GRUB on the MBR and give us the freedom to use a different boot method instead!

---

### Post by bulldog on 2006-12-12
You can use GRUB and tell it to boot into windows instead of ubuntu by default.
If you want,you can hide GRUB entirely and your wife will not know it's there :-)
Use gparted live cd instead of Partition Magic.
Partition Magic is known to not to handle ext3 partitions very well,so you better not use it.
You can find it here,

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it to a cd and boot from it when you want to resize your partitions.

---

### Post by Juan Largo on 2006-12-12
bulldog -

So in other words, the "BAD DISK" error is bogus and is related to Partition Magic's limitations?  In that case, I'll get a copy of gparted live and use it from now on.

I'm intrigued with your second suggestion.  I think I could make Windows boot by default with GRUB by modifying /boot/grub/menu.lst, but how to I "hide" GRUB altogether, as you suggest?  And if GRUB's "hidden," how would I use it to boot to Ubuntu?

---

### Post by bulldog on 2006-12-12
The time you have to make a choice,set it to three seconds,if you hit ESC in this three seconds you'll see the GRUB menu and you can choose ubuntu.
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3 <--- set this to your convenience [seconds]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu[/code <--- uncomment this line and GRUB will be hidden[remove the #]
```
The following is used to change the default boot
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0 <----count your kernels and other entry's starting with a zero,and make the default zero the number you found for your windows
```

If you have any trouble ,just ask.
If you want to reinstall GRUB from the live cd do it this way,
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by seashell11 on 2006-12-12
I am not by my ubuntu computer right now, so I can't tell you exactly, but in the grub menu.lst file, you need to uncomment the hide grub menu, or something like that. Then you set the delay to 3 seconds before it will automatically boot to the default boot option. You will also need to set windows as the default boot option of course. Then, when you start the computer it will say automatically booting to dafault press escape to choose your boot option, or something like that. If you don't do anything, it will boot to windows in 3 seconds. If you press escape, you can choose to boot from windows or ubuntu.

---

### Post by seashell11 on 2006-12-12
Looks like someone else beat me to it, and they got more information anyway. Hope it works for you!

---

### Post by Juan Largo on 2006-12-12
Thanks to all for the quick responses and the good suggestions, especially the tip about gparted live, which appears to work fine.  I also found partitioning software from Acronis that I might try.  

I'm still experimenting with Ubuntu, and haven't decided if I'll keep it on hdb permanently.  If I do, I'll reinstall GRUB on hda and go from there.  Right now it's a toss up between Ubuntu and MEPIS.

Cheers!

---

### Post by gn2 on 2006-12-13
> **Juan Largo said:**
> Right now it's a toss up between Ubuntu and MEPIS.

Cheers!

Looked at PCLinuxOS yet?

I've found similar problems in the past with Partition Magic 8.0, now if I'm setting up a dual-boot I just use it to create blank space to install to and let the Linux installer do the work.

---

### Post by Juan Largo on 2006-12-13
gn2 -

When you create empty space with Partition Magic 8.0 and then let the Linux installer do its thing with the empty space, what happens when you run PM8.0 after the installation is completed?  Do you get  disk "errors" then?

---

### Post by Juan Largo on 2006-12-13
gn2 -

Getting back to you about PCLinuxOS.  I think PCLinuxOS may be useful as a live CD or when you need a "lite" installation, but I'm not sure it's quite ready for prime time yet.

I just removed the Ubuntu installation and installed MEPIS.  Then I installed the Ubuntu desktop on the MEPIS kernel and voila ... I have a dual log-in option where I can switch between desktops without even rebooting!

There are some things I like about MEPIS:  I think it has a better installer -- allowing you to control how GRUB is installed, for example.  IMHO, it also has superior hardware recognition, like Knoppix, especially for old clunky systems, and it has better tools overall.  Plus, MEPIS seems to offer a lot more packages in Synaptic (19,000+) and I like the way KPackage organizes those packages by class.  But the KDE environment does seem a bit confusing and chaotic at times.  Having the option of logging into the Ubuntu desktop allows me to retire to a really nice peaceful environment in gnome and any applications I install in KDE automatically carry over into the Ubuntu desktop.  What a sweet combination! 

With MEPIS having automatic plug 'n play for the iPod, I think it won't be long before I say goodbye to Windows forever ... that is, if I can convince my wife to go along. :p

---

### Post by gn2 on 2006-12-13
Haven't had any probs with using partition magic after installing  with Linux installers.


> **Juan Largo said:**
> gn2 -

Getting back to you about PCLinuxOS.  I think PCLinuxOS may be useful as a live CD or when you need a "lite" installation, but I'm not sure it's quite ready for prime time yet.

There's three versions, Big Daddy is fairly comprehensive, and it's streets ahead of Ubuntu in terms of simplicity and ease of use.

> **Juan Largo said:**
> 
There are some things I like about MEPIS:  I think it has a better installer -- allowing you to control how GRUB is installed, for example.   

As does the PCLinuxOS installer

> **Juan Largo said:**
> 
Plus, MEPIS seems to offer a lot more packages in Synaptic (19,000+)

How many will you ever use? PCLinuxOS has everything I will ever need.

> **Juan Largo said:**
>  
automatic plug 'n play for the iPod, 


Not an issue for me, I don't currently own and will never purchase an Apple iPod.

Mepis is a well reviewed Distro, but I have yet to try it. PCLinuxOS meets all my needs, other than one laptop which I run Xubuntu on.

> **Juan Largo said:**
>  

goodbye to Windows forever ... that is, if I can convince my wife to go along. :p

Sudo apt-get wife-un-windows-iser ? ](*,) 

Similar problems in my household.....

---

### Post by Juan Largo on 2006-12-14
gn2 -

I'll follow your advice and let Linux installers use unallocated space instead of partitioning disks ahead of time.  I hope I'll avoid "Bad Disk" problems in the future by doing it that way.

As far as other distros are concerned, Before making any more snap judgements, I WILL give PCLinuxOS a try as you suggest.  My main computer interests are audio recording, ripping, and organizing music files.  My secondary interests are office-type applications, such as word processing, data base, scanning, etc.  Third, is managing digital photography.  If PCLinuxOS has good software to do these things "out of the box" and it's also easy to use, I guess I'm sold.  But how's the support for PCLinuxOS?  I think Ubuntu and MEPIS are both super in that regard ... a very large user/expert base and very good forums, like this one, with lots of helpful advice.  Some of the other Linux forums I've visited leave much to be desired.  It seems that PCLinuxOS hasn't been around quite as long as the others ... but I guess all distros have to start somewhere.

---

### Post by gn2 on 2006-12-14
> **Juan Largo said:**
> gn2 -

My main computer interests are audio recording, ripping, and organizing music files.  My secondary interests are office-type applications, such as word processing, data base, scanning, etc.  Third, is managing digital photography.  If PCLinuxOS has good software to do these things "out of the box" and it's also easy to use, I guess I'm sold.  But how's the support for PCLinuxOS?  I think Ubuntu and MEPIS are both super in that regard ... a very large user/expert base and very good forums, like this one, with lots of helpful advice.  Some of the other Linux forums I've visited leave much to be desired.  It seems that PCLinuxOS hasn't been around quite as long as the others ... but I guess all distros have to start somewhere.

There's no doubt that support for Ubuntu is absolutely outstanding.
PCLinuxOS has good Forums too.

Don't do any recording myself but my (modest) music needs are catered for by Amarok.

Open Office works for my office requirements.

The Gimp isn't Photoshop, but does more than I'll ever need. I like Digikam.

I have an HP PSC 1215 which works with Linux.

I like the simplicity of the PCLinuxOS control Centre, and find using PCLinuxOS very straightforward.

Just need some to un-windows-ise the wife and I'm fully sorted!

---

