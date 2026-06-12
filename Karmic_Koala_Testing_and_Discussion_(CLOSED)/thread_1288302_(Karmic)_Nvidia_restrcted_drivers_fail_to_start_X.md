---
title: "(Karmic) Nvidia restrcted drivers fail to start X"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tnd on 2009-10-11
[B]EDITED: Installing Karmic has screwed up both my Linux and Windows partitions. I'm giving up on it for a while.
[/B]

I think this is already a known issue - there are a number of bug reports out there but no one definitive thread on it yet that I can find...

Basically, after installing the Nvidia proprietary drivers (I'm sorry, but they are better in almost every way than the open source ones :( ) and restarting, they conflict somewhere with the new kernel and X won't start - I get a flickering screen and am returned to the login. Apparently this affects all kernels above 2.6.31-10.

I tried to edit xorg.conf to change back to the non-proprietary drivers but it didn't seem to work, and since it was a new install anyway I have re-installed completely. What I was wondering is if anyone knows of a way round this? 

Unless Nvidia do something I'm not sure it'll be fixed in time for the Karmic full release as it's a problem with their proprietary drivers :(

-------
Another problem I've discovered while writing this:
I can't seem to open /etc/X11/xorg.conf (yes, I have capitalised the "X" of "X11") to look at what drivers I'm using now. 

Sorry for the massive post... any thoughts? I'll post any additional info I can but I'm not keen on recreating the bug at least until I can get my xorg.conf working

---

### Post by orky7 on 2009-10-11
there is no xorg.conf file in 9.10 but u can create it if u need it but its complicated at least to me....

---

### Post by tnd on 2009-10-11
Ok I'll look that up... thanks for replying so quickly!

I'm afraid I've given up with Karmic now.

Since the first post earlier today, I rebooted and couldn't turn on Xubuntu or Windows. I don't even get as far as the login screen on either... on Xubuntu the little glowing animal which I presume is the Koala shows up, then black screen, on Windows it freezes during loading. The install CD for Xubuntu doesn't work past clicking "Install" either.

I'm posting this from a fresh install of 9.04 as it appears I have buggered up (if you'll pardon the technical term) my entire computer by trying to install the beta. So, I'm going to give Karmic a miss and check back after Christmas when hopefully some of this will have been fixed.

---

### Post by mils on 2009-10-14
I eventually got restricted nvidia drivers working with

```
dpkg-reconfigure nvidia-185-kernel-source
```after poking around, installing and uninstalling various versions of nvidia-glx-*, booting with different kernel versions and so on.

---

### Post by PeteMJ on 2009-10-14
The initial install of the NVIDIA drivers fails without letting the user know very well:

Adding Module to DKMS build system

Error! Invalid number of arguments passed.
Usage: add -m <module> -v <module-version>


As Mils points out, you can use a 'dpkg-reconfigure nvidia-185-kernel-source' to run something which will add the module properly.

---

### Post by adder1972 on 2009-10-14
Hi,

I was not able to start X after upgrading from 9.04. I have a GeForce 8500GT card. 

It has been running nicely since I first installed 8.04 LTS on my computer.  I guess back then I enabled the proprietary drivers ... (but I am not sure).

I copied and removed my current Xorg:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo rm /etc/X11/xorg.conf

Then I tried to reset or fix the Nvidia config.   

sudo nvidia-xconfig
sudo nvidia-settings

I guess based on that and the error-message I got back, I decided to install the 173 kernel module:

sudo aptitude install nvidia-173-kernel-source

Then i just started X:

startx

and things were OK again.

---

### Post by trulan on 2009-10-14
The NVidia 185 drivers (installed through Jockey) have given me no trouble on any pf the generic kernels.  They have issues with the RT kernel, but can be manually patched to make them work.  NVIDIA GeForce 6150 LE.

Edit: after reading a few more threads, it seems like it is a bigger problem, hasn't affected me yet as I haven't updated in the past few days.

---

### Post by moffa on 2009-10-14
> **trulan said:**
> The NVidia 185 drivers (installed through Jockey) have given me no trouble on any pf the generic kernels.  They have issues with the RT kernel, but can be manually patched to make them work.  NVIDIA GeForce 6150 LE.

Edit: after reading a few more threads, it seems like it is a bigger problem, hasn't affected me yet as I haven't updated in the past few days.

The fix was just applied.

---

### Post by Havage on 2009-10-14
I was having trouble with the 185 driver and a 9500GT yesterday. I got the machine working with the 173 drivers but based on your comment that the fix was just applied, I tried to apply the 185 drivers again in Jockey with no luck (blackscreen upon reboot).

EDIT: Actually, my mistake. I ran update manager THEN jockey and did the 185 switch and it booted ok this time which is a big leap forward. Now the problem is that it says its showing in 16M colors but it looks more like 65K.

---

### Post by eznet on 2009-10-15
I am having the same issue on my system as tnd - after failing to get X to start, I changed 'driver' back to 'nv' in /ect/X11/xorg.conf and still cannot get X to load.  Xorg.0.log indicates the "Fatal Server Error"...

GUI worked before installing the nVidia drivers, I don't understand why changing back to 'nv' wouldn't bring that back...

Any insight is appreciated - seems like we are starting to change some of the long standing 'ways of doing things' that have just always worked...  Time to go back to school I guess...

Thanks!
-Matt

---

### Post by eznet on 2009-10-15
Got X back up and wanted to post back in case someone stumbles here.

nVidia + 9.10 Alpha 6 worked.

Upgraded to 9.10, rebooted, saw splash, screen flickers for about 15-20 seconds and I am dropped to CLI log in.

Since I was wrestling with a from-dvd clean install of 9.10 Beta already, I opted to do just that... All was well with the vesa/nv/whatever-defalt-is, installed nVidia again and got the flickr/CLI on reboot.

To get back into Gnome, I simply uninstalled the nVidia drivers, removed xorg.conf and rebooted... Back to step one - Gnome without nVidia. 

I have tried both the most recent repository driver as well as NVIDIA-Linux-x86_64-185.18.36 from nVidia's site and get the same results - no GUI.

Hope this helps someone.

---

### Post by mavros on 2009-10-17
I had a similar problem with the Nvidia dirver (version 180) when upgrading from Jaunty to Karmic. Actually the installation broke off half way due to inabilities to resolve interdependencies between the 180 and the newer 185 version of the driver package.

A workaround I used is to first activate the older 173 version instead of the 180 and then run the partial update (the remainder of the installation of 9.10) again.

Maybe a 9.10 bug?

---

### Post by aimwin on 2009-10-18
> **tnd said:**
> [B]EDITED: Installing Karmic has screwed up both my Linux and Windows partitions...............
Basically, after installing the Nvidia proprietary drivers .......and restarting, they conflict somewhere with the new kernel and X won't start - I get a flickering screen and am returned to the login. Apparently this affects all kernels above 2.6.31-10.........................

My notebook is Austek S62J OEM custom.
Nvidia driver works fine in 8.04, 8.10 and 9.04.
The notebook hibernate, stand by and resume with no hick up.
It run Google Sketch Up 7 with ease (not as fast as XP though).

For Karmic, this is my 4th time re-installation. It wreck only my Karmic partition. (lucky for me). It asked to do fchdk or something like that after reboot and it check and found something wrong and fixed it. But it failed to login after that.

I don't know if it is the problem with EXT4 with Karmic or not, I used EXT4 in all those clashes and still till this moment.

I don't knows who to be blame, Linux developers or Nvidia ?

(joking, I blame no one, everyone is working for our society. And we have to go through this road, no other road. Only helping the Guru_s to make our road flatter asap.)

But with out Nvidia Proprity driver it work fine for me so far.
Of course no suspend nor hibernation, but auto black LCD and resume function works fine.
it will just hung up and possible causing one of my wreked Karmic partition.

But I don't know if my other 3 "clashes and partial update issues" have anything to do with "no correct display driver installed or not" or EXT4 issues and the will never boot again.

But with the default display driver in Karmic, also gave me some problems with MSI netbook Wind U100 Plus (?? note: cannot remember 100% the model?)
(not aplicable for this thread, but I gave a bit of details so the Guru_s will help to diagnose the issue).
It will keep repeating the "Fn"+"F5" (brighter or darker for the LCD panel) though I press only 1 or 2 times, but it keep repeating as if the keys were pressed and stuck there for 10 to sometime 100+ maybe keep going till reboot and even after new login, still repeat that by its self as if it remember the stage before reboot.

And it will stop after I left it repeating for so long.

It will start again soon after I decide to just increase the brightness but not much repeating if I decrease by using  "Fn"+"F5".

However, in the same MSI the Kbuntu_Netbook Remix (on the first partition) still work fine without the same problems, but you cannot use brightness setting software within Power management to reduce nor increase brightness. It would not work with software, but "Fn"+"F5" work perfect with no hick up at all.

Though with Nvidia chipset (but no Nvidia Propritory driver installed) on my Austek have no issue on this matter.

I have not tried 9.04 on MSI netbook yet, will report afterward. I will try soon.

So I don't know if we should look back into the kernel of linux or "socalled blamed" the Nvidia.


I mean Nvidia should try to work on it too,
 but I think something in the kernel need to be look at too.

Best wish to everyone.

---

### Post by mavros on 2009-10-24
These are sad stories. 

I have been lucky despite the error messages mentioned above the workaround described solved my problems.  9.10 works very well on a dual booting system Vista/Ubuntu with all graphic effects both under Gnome and KDE.  I have a Geforce 9600 GT.

As mentioned the problem seems to be the 180 version of the driver which runs under Jaunty but has problems updating to 185 under Karmic.

---

### Post by nanog on 2009-10-24
for those of you who have trouble running the proprietary drivers you may be missing dkms (now required for nvidia module install) or some dependency, such as, nvidia-common. some of my karmic upgrades lacked one or both of these files resulting in jockey failure and/or failed nvidia module compiles.

---

### Post by fedexnman on 2009-10-24
same problems here on a desktop evga geforce9800gtx, so i reinstalled 9.04, in some other thread i read where people are having problems on there laptop with nvidia gpu s, and they fixed it by going to the nvida x server menu,  its either in system or admin ?? n disabling powermizer, n that fixes the problem.

---

### Post by fedexnman on 2009-10-24
i will give 9.10 another go on the 29th oct, fingers crossed, like i said try and uncheck powermizer in the nvidia xserver menu ..

---

### Post by eznet on 2009-10-25
This is what got me back up:

[http://ubuntuforums.org/showthread.php?p=8163944#post8163944](http://ubuntuforums.org/showthread.php?p=8163944#post8163944)

---

