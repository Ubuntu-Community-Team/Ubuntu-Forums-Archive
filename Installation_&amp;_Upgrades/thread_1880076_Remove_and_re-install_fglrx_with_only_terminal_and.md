---
title: "Remove and re-install fglrx with only terminal and no apt-get"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by lifelike27 on 2011-11-12
So I made a mistake of trying to remove the proprietary ATI graphics drivers so I could use the open source ones - I screwed up. What exactly I screwed up, I'm not sure. Though now, when I boot into Ubuntu, I'm greeted without X11 running. I've tried running 'startx' but it says there's a graphical issue obviously (I'll provide details once I've restarted and copied all the text).

I managed to download ATI's proprietary drivers and tried to install them with: ```
sudo sh ./ati-driver-installer-11-9-x86.x86_64.run --buildpkg
```
Then installing the debs - didn't work. So I removed what was installed with:
```
sudo dpkg --remove fglrx fglrx-dev fglrx-amdcccle
```

I tried running the command again without ' --buildpkd ', it seemed to install fine, but still no luck.

I got an error saying loki_setup: couldn't write to file //usr/bin/ati
It says there are a couple of files that couldn't be copied. I tried removing /usr/lib/ati (might be the wrong path) and then trying again, but no luck.

Some other errors included "failed to build fglrx-8.861 with dkms"

Can anyone guide me into completely removing EVERYTHING first and then reinstalling the proprietary drivers again? I'm not sure exactly what other info to provide.

---

### Post by MAFoElffen on 2011-11-12
> **lifelike27 said:**
> So I made a mistake of trying to remove the proprietary ATI graphics drivers so I could use the open source ones - I screwed up. What exactly I screwed up, I'm not sure. Though now, when I boot into Ubuntu, I'm greeted without X11 running. I've tried running 'startx' but it says there's a graphical issue obviously (I'll provide details once I've restarted and copied all the text).

I managed to download ATI's proprietary drivers and tried to install them with: ```
sudo sh ./ati-driver-installer-[COLOR=Red]11-9[/COLOR]-x86.x86_64.run --buildpkg
```Then installing the debs - didn't work. So I removed what was installed with:
```
sudo dpkg --remove fglrx fglrx-dev fglrx-amdcccle
```I tried running the command again without ' --buildpkd ', it seemed to install fine, but still no luck.

I got an error saying loki_setup: couldn't write to file //usr/bin/ati
It says there are a couple of files that couldn't be copied. I tried removing /usr/lib/ati (might be the wrong path) and then trying again, but no luck.

Some other errors included "failed to build fglrx-8.861 with dkms"

Can anyone guide me into completely removing EVERYTHING first and then reinstalling the proprietary drivers again? I'm not sure exactly what other info to provide.
Please refer to the lower half of my post here:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")**[/SIZE][/COLOR][/SIZE][/COLOR]

User 3602 and I keep this post updated with the latest workarounds. 

*** Problem with what you posted / downloaded.  Looks like you have Catalyst version 11.9 <> It had problems with Ubuntu.  I'd recommend the current version 11.10 or the previous version 11.8. They worked okay.

What version of Ubuntu are you running? Why not apt-get? (<-- In title)

---

### Post by lifelike27 on 2011-11-12
Sorry, I wrote the first post in a hurry. I didn't realize I missed out a bunch of details.

Ubuntu 11.04 (I don't intend on updating any time soon until 12.04 comes out).

There's no apt-get available because I can't connect to my wireless through the terminal (separate issue, and no wired internet). What I can do is boot into elementaryOS and transfer files to the Ubuntu partition.

Also, the ATI options told me to download this version since this the one that works for my graphics card on my laptop.

---

### Post by MAFoElffen on 2011-11-12
> **lifelike27 said:**
> Sorry, I wrote the first post in a hurry. I didn't realize I missed out a bunch of details.

Ubuntu 11.04 (I don't intend on updating any time soon until 12.04 comes out).

There's no apt-get available because I can't connect to my wireless through the terminal (separate issue, and no wired internet). What I can do is boot into elementaryOS and transfer files to the Ubuntu partition.

Also, the ATI options told me to download this version since this the one that works for my graphics card on my laptop.
I guess since you are on Ubuntu 11.04 and have Catalyst 11.9 already, it would get you going.  It has big problems with unity, but unity is Ubuntu 11.10 (and in 12.10).  You must have got that about a week ago, as Catalyst 11.10 released about that time.

No matter.  Those instruction should get you going.  So tell me about your "ElementaryOS."  You know you could do this by temporarily editing the grub menu to boot into mutli-user tty text console... or boot a LiveCD, mount the filesystem, mount the installed system and install ffrom within a GUI (Live image).

***Because booting Linux externally requires that you mount the installed system (chroot) to affect changes in that system.  Is that understandable?

---

### Post by lifelike27 on 2011-11-12
> **MAFoElffen said:**
> I guess since you are on Ubuntu 11.04 and have Catalyst 11.9 already, it would get you going.  It has big problems with unity, but unity is Ubuntu 11.10 (and in 12.10).  You must have got that about a week ago, as Catalyst 11.10 released about that time.

No matter.  Those instruction should get you going.  So tell me about your "ElementaryOS."  You know you could do this by temporarily editing the grub menu to boot into mutli-user tty text console... or boot a LiveCD, mount the filesystem, mount the installed system and install ffrom within a GUI (Live image).

***Because booting Linux externally requires that you mount the installed system (chroot) to affect changes in that system.  Is that understandable?

Booting into the recovery console on my Ubuntu 11.04 is fine. I can do that through grub. So permissions isn't a problem. It's basically the process of getting rid of what exists (main problem), and then doing a fresh install of the driver.

The elementaryOS partition is meant for using the internet to download files (eg. ati graphics driver). I tried manually downloading the files that I would use from apt-get fglrx but there are way too many dependencies. 

I noticed in your tutorial you require the use of apt-get which I don't have access to in this case..

P.S: [www.elementaryos.org](www.elementaryos.org) :)

---

### Post by MAFoElffen on 2011-11-13
> **lifelike27 said:**
> Booting into the recovery console on my Ubuntu 11.04 is fine. I can do that through grub. So permissions isn't a problem. It's basically the process of getting rid of what exists (main problem), and then doing a fresh install of the driver.

The elementaryOS partition is meant for using the internet to download files (eg. ati graphics driver). I tried manually downloading the files that I would use from apt-get fglrx but there are way too many dependencies. 

I noticed in your tutorial you require the use of apt-get which I don't have access to in this case..
Yes. ATI and even NVidia binaries have build dependencies, therefore in step 6, there is an apt-get statement to make sure those libraries and other dependencies are present.

But for you, since you already had Catalyst installed, you may have all that installed already.  If not, you could download them and install them manaully...

---

### Post by lifelike27 on 2011-11-13
How could I get all the dependencies downloaded at once? When I tried earlier, there were a lot of them and they were all a few KBs.

---

### Post by MAFoElffen on 2011-11-13
> **lifelike27 said:**
> How could I get all the dependencies downloaded at once? When I tried earlier, there were a lot of them and they were all a few KBs.
You asked for it.  Manually would entail downloading each file, copying over, but installation would stil need to be mount/chroot to system, where you would then dpkg to install them... Where if you were going to mount and chroot, you could do that all from there.

The way you are going about this **"is**" the hardest way of many ways.  That's what I tried to hint on before. I know 5 ways off the top of my head to do this from your Ubuntu installed base.

Here's how I would do it...Read and do this (follow link): 
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR]

You will then be booted onto your installed system, with networking and all the normal rights and privileges at a commandline prompt. <Directions for Installing Drivers>

If you did the same instructions to where you are at the linux commandline, but rather inserted the text "radeon.modeset=0", then it would boot in a VESA mode GUI and you would be able to install your graphics from the desktop... Where you could install your drivers.

Do you need to hear other ways in?

---

### Post by lifelike27 on 2011-11-13
I don't think I need to mount and chroot because I have access to the text console already for the Ubuntu partition. What I DON'T have access to, is a direct internet connection (I can download and copy to the Ubuntu partition). 

Before I saw your reply I managed to download the dependencies and install them, ran the proprietary graphics driver install file and SUCCESS..partially. I realized that the reason I thought there were so many because I forgot some of them were already installed on my system.

For some reason, my keyboard, touchpad and mouse don't seem to work so I can't login to Ubuntu.

I tried to solve this by booting into the recovery console and once logged in, I started X Server. First thing I noticed - Unity wasn't working (I installed 11.6 so that's probably why), there didn't seem to be proper graphics acceleration (libnotify didn't have it's faded effect when a notification popped up) and still my keyboard and mouse didn't work...

---

### Post by MAFoElffen on 2011-11-13
> **lifelike27 said:**
> I don't think I need to mount and chroot because I have access to the text console already for the Ubuntu partition. What I DON'T have access to, is a direct internet connection (I can download and copy to the Ubuntu partition). 

Before I saw your reply I managed to download the dependencies and install them, ran the proprietary graphics driver install file and SUCCESS..partially. I realized that the reason I thought there were so many because I forgot some of them were already installed on my system.

For some reason, my keyboard, touchpad and mouse don't seem to work so I can't login to Ubuntu.

I tried to solve this by booting into the recovery console and once logged in, I started X Server. First thing I noticed - Unity wasn't working (I installed 11.6 so that's probably why), there didn't seem to be proper graphics acceleration (libnotify didn't have it's faded effect when a notification popped up) and still my keyboard and mouse didn't work...
11.8 or 11.10 work with 11.10 and unity, thats what I said on my 2d(?) post... 11.9 doesn't work with Unity.  I don't ven remeber what 11.6 did, LOL, sorry.

---

### Post by lifelike27 on 2011-11-13
How would I be able to remove a previous installation of the install file if I just ran it without the flag '--buildpkg'?

---

### Post by lifelike27 on 2011-11-22
Ok, so I was able to use this [wiki]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver") to completely remove all existence of fglrx or anything I installed previous and do a clean installation of 11.8.

The problem is after I boot and I see the login screen, my mouse and keyboard *still* don't work. I've tried using a usb keyboard and mouse, doesn't work either.

I can login through the recovery console and then run startx, but as soon as I do that, keyboard and mouse fails. I know my graphics are working now because libnotify seems to fade in and out like it would with proper graphics acceleration. 

I really REALLY would like getting this solved soon. I have a final coming up and it's in linux systems, so having my original working would really help.

No, I don't like 11.10 that much. I'm used to my original 11.04 - sorry.

---

### Post by lifelike27 on 2011-11-24
Bump.

I have a final and it would really make my life easier if I got this working!

---

