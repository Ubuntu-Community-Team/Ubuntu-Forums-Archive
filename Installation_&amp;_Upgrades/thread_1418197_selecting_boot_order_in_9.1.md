---
title: "selecting boot order in 9.1"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by frogmed on 2010-02-28
i am using a dual boot with windows vista, i would rather use ubuntu but my wife wants windows. how do i change m,y boot order to boot into windows instead of ubuntu?  my ubuntu is an upgraded version from 8.? then 9.04 then 9.10

---

### Post by n0dix on 2010-02-28
Two options:
1. Don't change the order and automatically boot into Windows partition instead of Ubuntu. 
2. Change the boot order. 
For both you need to change you menu.lst. Please post it.

---

### Post by oldfred on 2010-02-28
If you have a new install of Karmic you now have grub2 and no menu.lst to edit.

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]"
Then do:
sudo update-grub

---

### Post by kansasnoob on 2010-02-28
> **frogmed said:**
> i am using a dual boot with windows vista, i would rather use ubuntu but my wife wants windows. how do i change m,y boot order to boot into windows instead of ubuntu?  my ubuntu is an upgraded version from 8.? then 9.04 then 9.10

First post some info. While booted into Ubuntu run the following commands and post the output here:

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4
```

```
ls /boot/grub
```

---

### Post by herdivet on 2010-03-01
> **oldfred said:**
> If you have a new install of Karmic you now have grub2 and no menu.lst to edit.

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]"
Then do:
sudo update-grub

This was straightforward, simple, and did the job perfectly.  :p
Thanks!

---

### Post by nana336 on 2010-04-07
oldfred your's worked perfectly...Thanks for it.

Is there a way we can change the order of the OS in the boot we want ? 

Also why we have too many Ubuntu Linux boot things in the sequence like the following. What is the use of these....
[COLOR=Blue]Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-19-generic 
Ubuntu, Linux 2.6.31-19-generic (receovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory Test
Memory Test (serial console ...)[/COLOR]

---

### Post by oldfred on 2010-04-07
We generally recommend yo keep 2 kernels as the old one works and the new one may have troubles and it is easier to boot if the old one is still installed.

If you want to totally customize your menu:
total custom menu/config file 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
  
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

You can also delete old kernels and update grub, but be very careful not to delete the kernel you are using:
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by herdivet on 2010-08-24
OK, I now want to post what I think is the absolutely easiest (maybe laziest) and most foolproof way to do this. It's all GUI, no command prompt required, no editing necessary.

Click Applications
Click Ubuntu Software Center
Search for Startup Manager
Install Startup Manager
Close Ubuntu Software Center

Click System | Administration
Click Startup Manager
In 'Default Operating System' click the drop down and choose whatever you want to have as the default.
Click Close

You can also change other startup parameters here, all in a simple GUI format. Extremely simple.

---

