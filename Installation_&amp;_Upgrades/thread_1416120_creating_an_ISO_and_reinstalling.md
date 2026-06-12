---
title: "creating an ISO and reinstalling"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by razor180 on 2010-02-25
I'm going to be replacing my computer with a custom built one soon, and I want to transfer the software and packages that's already installed. I have an ISO disc creator to take the current information on my hard disk and format it for an ISO, which I can burn onto a DVD, but what I'm wondering is, how would I go about reinstalling the OS

here's the backstory, I'm wanting to transfer the hard drive from this computer to the one I'm going to custom build once it's finished, and I'm pretty sure I would have to reinstall due to the fact that I would have to reconfigure and install new hardware drivers. If I'm wrong, please tell me so I don't waste the time and go through the trouble of this

my plan is to create an ISO of my hard disk, then backup all of my personal files, then remove them so the ISO will have more room (and I may get rid of some unnecessary packages), then get rid of everything on the hard drive (just use a livedisc of something and use a partition manager to delete all partitions on the hard drive) then move the hard drive over to the new computer, and reinstall with the ISO disc I created

the things that will be staying the same is the graphics card, some peripherals (like monitors, keyboard, wacom tablet, printer, etc...) but the motherboard has a different sound card and a different processor (I'll probably just install a different kernel to accommodate for that) and some different things that are smaller (don't forget the power supply) 

so please either answer the question, or offer a better method of transferring the hard drive (and don't say "just simply take the hard drive out and put it in the other computer" unless you have indisputable proof that it will work. I know it most likely won't work for multiple reasons, the drivers being one of them, the fact that windows can't do that (I have a different plan for windows that involves upgrading from vista 32bit to windows 7 64 bit))

---

### Post by razor180 on 2010-02-26
okay, bumping this first off

second, I'm wondering, is there something on synaptic that I can get to install, or is there a terminal command, or am I just going to have to make some sort of script to do it?

do I even need to do this, or is there another way (I'm seriously hoping there's another way, an easier way)

---

### Post by robert shearer on 2010-02-26
I have used Remastersys many times.

 [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

It makes a bootable live cd of your current configuration that can be installed on most other hardware as you would install a normal Ubuntu.
Note that it is** not** meant to be a back-up of all your data and will fail to build if there is too big an iso to make.

Backup all user data(video/pictures/photos/music etc) and then remove those files from the drive.
Clear the apt cache of old packages
```
sudo apt-get clean
```

Unmount any other partitions (but not /, home, or swap) including external drives/usb etc.

Now you just have your configured o/s and should be able to run remastersys to make an iso of it.

As the cd made is a live cd you have the chance to test it (and or install it on a spare drive--any old one will do 10Gb should be fine) or try it in a virtual machine **before** you wipe the old hard drive.

This should also let you try moving the existing hard drive over to see if it boots and if it doesn't then installing from the remastered disc.
Also lets you run the live cd on the new system to see if all the hardware works too.

Here is a link to an older tutorial (probably all still valid for the current version) shows how easy it is.
[http://klikit.pbworks.com/Remastersys+tutorial+by+dedoimedo](http://klikit.pbworks.com/Remastersys+tutorial+by+dedoimedo)

Note that the repo given in the tutorial is out of date. Use the one in the first link that applies to your Ubuntu version.

---

### Post by razor180 on 2010-02-26
thank you

one thing though, all I'm doing is moving my hard drive from one PC to another, and I'm wondering if I have to do a fresh install or if I can just simply move my hard drive over (I'm assuming I can't do the latter, but I'm still not quite sure). all the peripherals are the same, it's just most of the internal hardware that's going to change (the things that are going to stay the same are the video card and disc drive). I'm wondering because if I don't have to go through this hassle, then I don't want to go through it

---

### Post by robert shearer on 2010-02-26
> **razor180 said:**
> 
I'm wondering because if I don't have to go through this hassle, then I don't want to go through it

**Hopefully** you will be **backing up your data** anyway no matter what option you choose. ;)

Remastersys is a simple download and install like any other, it runs to build the live cd with one click and builds unattended.

Where is the hassle ?.

Just moving the hard drive **might** work but you won't know until you try and I do not think that anyone here can** assure** you of the outcome either way.

So best to have a **plan b**. That is why I suggest Remastersys.

Sometimes a reinstall cleans out a lot of leftover cruft.

Using a reinstall with Remastersys at least gets you set up with the apps you had and the layout,menus etc that you had configured.
All you need then is to set up graphics drivers and reload the data from your backup.

---

### Post by razor180 on 2010-02-26
it's the hassle of having to reinstall the whole thing, fix errors, having to backup my whole system, having to back up all of my files, and having to reinstall it later

and remastersys came with my OS, I didn't have to install it

the reason I don't want to try is because I don't want to cause any damage to anything, I don't really want to screw up anything that's already pre-existing on the hard drive or make something leave remnants on the hard drive, or any other things that could happen

---

### Post by presence1960 on 2010-02-26
I just upgraded my machine. Took out my AMD Athlon64 x2 +5400 CPU, Biostar TF7050-M2 mobo, EVGA GeForce 8600GT Vid card & 4 GB OCZ RAM and put that in my daughter's machine. Added a 320 GB Seagate SATA drive to her machine and left in the 40 GB IDE Seagate with XP and Karmic. Did not need do anything as I booted the machine and both OSs worked.

In my machine I added an AMD Phenom II X4 955 Black Edition (3.2 GHz quad-core), a Biostar TA790GXE AMD 790GX Socket AM3 Motherboard, 4 GB OCZ platinum RAM, EVGA GeForce 9500 vid card & a 1 TB Seagate SATA hard disk. Left the 250 GB Seagate SATA disk with the OSs on there and the 500 GB Seagate SATA disk with my backups on there. Booted up and everything worked.

I would still back everything up. I recommend clonezilla. You can make an image of individual partitions or the entire hard disk. Then restore using those images if need be.

---

### Post by robert shearer on 2010-02-27
> **razor180 said:**
> 
the reason I don't want to try is because I don't want to cause any damage to anything, I don't really want to screw up anything that's already pre-existing on the hard drive or make something leave remnants on the hard drive, or any other things that could happen

???  :eek:

---

### Post by razor180 on 2010-03-01
> **robert shearer said:**
> ???  :eek:
lol

don't see how that doesn't make sense

pretty much I don't want to try and have complications or have the possibility of having irreversible damage done to my hard drive (there are things that can happen)

thanks presence, that's reassuring :D I'll try that first now that I know there shouldn't be a problem (I'm not sure if vista will boot, but yeah, since my OS is an ubuntu karmic derivitive, than that should work fine depending on what you say)

I'm actually upgrading to the same CPU (phenom II X4 955 black edition)

thanks both of you (I've ordered the parts 2 days ago and they should be here any day now)

---

### Post by presence1960 on 2010-03-01
> **razor180 said:**
> 

I'm actually upgrading to the same CPU (phenom II X4 955 black edition)



You will not be disappointed. That CPU rocks!

---

### Post by oldfred on 2010-03-01
About a year ago I put new motherboard and video card in my computer and had no issues. I believe it was because the old video card was nvidia as was the new. If you switch brands then you will need a new video card driver to work correctly.

I do not backup operating system as I think it is very easy to reinstall. But I do back up /home and periodically export a list of installed apps to a location that gets backed up. I have copied a few install scripts that users have posted and am modifying them for my use as my set-up is not standard with separate data partitions and linked folders.

---

### Post by razor180 on 2010-03-01
> **oldfred said:**
> About a year ago I put new motherboard and video card in my computer and had no issues. I believe it was because the old video card was nvidia as was the new. If you switch brands then you will need a new video card driver to work correctly.

I do not backup operating system as I think it is very easy to reinstall. But I do back up /home and periodically export a list of installed apps to a location that gets backed up. I have copied a few install scripts that users have posted and am modifying them for my use as my set-up is not standard with separate data partitions and linked folders.ah

well, I'm not even changing the video card, that's moving to the new computer (ran out of room in the budget and since I've kind of dialed back on playing video games and I am focusing more on 3d modeling, and most renderers require a good CPU and don't really even use the video card for the rendering process, I decided that a new video card is something I could wait on)

I didn't know you could easily create a list of installed packages, that was the main thing I wanted to backup for, I didn't want to try and remember what packages and softwares I installed myself

thanks :D

---

### Post by presence1960 on 2010-03-01
I use this to restore installed packages from an old install to a clean installation: [http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Thanks to lovinglinux for the how to!

---

### Post by razor180 on 2010-03-01
that's really helpful
thank you :D

---

