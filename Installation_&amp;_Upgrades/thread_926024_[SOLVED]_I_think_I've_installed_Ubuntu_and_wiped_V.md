---
title: "[SOLVED] I think I've installed Ubuntu and wiped Vista (yes, I do feel like an idiot)"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by hard2explain on 2008-09-21
Right, as it says in the thread title, I do feel like a bit of an idiot at the moment.  Basically, I'd read about Ubuntu and how great it is so I downloaded it onto a CD-R and installed it onto my HP Pavilion DV6000 laptop.  

I'd read that you could create a dual boot, but obviously I messed that up at some point.  I've got Ubuntu up and running now but the resolution is all wrong and the wireless doesn't work (I'm writing this using a wired connection).  

Looking around at some other threads I'm fairly sure that I've managed to wipe Vista and my files.  In terms of my own files it's not the end of the world, I used the Vista's backup and recovery program a couple of weeks ago which transferred my personal stuff onto a USB external hard drive.  

It looks as though tweaking my system to get Ubuntu to run properly looks like it's going to be difficult, (especially seeing as I couldn't even install it properly!) so I figure my best bet is to go running back to Vista ASAP.

So basically I want to get Vista back on my system and then restore the files from the hard drive.

I tried downloading a Vista Recovery CD image using another computer and using that but it didn't work, so I'm guessing that Ubuntu got rid of all the traces of it.  

Anyone got any ideas as to the best course of action?

I feel like a right prat!

---

### Post by Bucky Ball on 2008-09-21
Open a terminal, paste this into it:

sudo fdisk -l

... and post the results here. You need to be more specific. Were all your files on the Vista hard drive or an external or internal backup drive? There are a few ways to go to check out if Ubuntu is going to work well with your system. I have one of the HP Pavillion dv6000 series and trust me, it is humming. \\:D/

To boot your wireless (probably Broadcom) is pretty easy nowadays and everything else reasonably straightforward too. The forums are a great source of help of course ..

---

### Post by hard2explain on 2008-09-21
Bucky Ball, thank you for replying to me so quickly.  

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

All of my files on the Vista hard drive are on an external USB drive.  

If I can get Ubuntu running nicely, then I would like to stick with it.

---

### Post by Bucky Ball on 2008-09-21
Wireless:

In a terminal, paste (just copy and paste from here):

**lspci**

This will tell us the exact card. If you see a couple of lines with 'Broadcom' in them, that will be enough, if not the whole lot. Post the results back here - copy from the terminal and paste in a post (save the fingers and is more precise).  :)

Do the same with:

[B]sudo blkid

[/B]If you have a Windoze installation disk, a dual boot is straightforward (I am dual booting with vista on my dv).But if you decide to keep Ubuntu as 'home', then that is easy too. You can rewrite the grub to the Ubuntu disk I would think. Incidentally, the IDE sda1, the large one?

---

### Post by hard2explain on 2008-09-21
Right, here it is:

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by caljohnsmith on 2008-09-21
hard2explain, try again:
```
sudo fdisk -l
```
but notice it is a lower case L, not a one.

---

### Post by hard2explain on 2008-09-21
And this is what came up when I typed in **sudo blkid**

/dev/sda1: UUID="d56aeb18-db5a-40f6-a620-6ffb021026b2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="d01c5059-df23-4c3b-bab7-9bd5e8b85c45"

---

### Post by hard2explain on 2008-09-21
OK, I've tried again and this is what came out with **sudo fdisk -l**

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fe991db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

---

### Post by hard2explain on 2008-09-21
OK, I've tried again and this is what came out with **sudo fdisk -l**

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fe991db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

---

### Post by caljohnsmith on 2008-09-21
Unfortunately, it looks like you're right--you no longer have Vista on your HDD. So unless you have some sort of Vista Install CD/DVD, you might be stuck.

---

### Post by Bucky Ball on 2008-09-21
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02). That is your wireless card. I got my card which is the same working by going:

**System->Admin->Hardware Drivers**

And ticking 'Broadcom B43 Driver' in there. It then asked if I would like to download 'fw-b43cutter'. I agreed and the whole process took about 2 minutes!

If this isn't successful, there is another walk through here, which is done in a terminal but don't worry, just copy and paste it line by line and check the results of the commands as you go:

[http://leorockway.wordpress.com/category/lignux/distros/kubuntu/hardy/](http://leorockway.wordpress.com/category/lignux/distros/kubuntu/hardy/)

ps: saw your last post and hoping you have got the install cd. They put it on a 10Gb partition on my machine which I had to make a disk of before I removed it and changed things. If your machine is under warranty no doubt they would send a replacement.

ps: Caljohnsmith might be able to point us in the direction of a solid way of installing the newer wl driver for this card but above is what worked for me on the same machine ... :)

---

### Post by eragon100 on 2008-09-21
And The nvidia geforce 7050 graphics card is also perfectly supported on ubuntu, in the screen mentioned above, you have to select the nvidia restricted 3d driver as well.

reboot

That should fix the resolution (automatically, or you'll be able to select a higher one in system -> preferences -> screen resolution)

Then go to add/remove, set the show option to "all available applications", and search for and install ubuntu-restricted-extras (yjust mark it and click apply)

Then, your computer will be 100% ready for use! :wink:

---

### Post by Bucky Ball on 2008-09-21
Eragon100 pretty well said it all! Then I guess, all going well, it's up to your imagination and how far you want to get into it.

Having said that, you may find it is not for you. It is not for everyone, different way of looking at it more than anything.

---

### Post by eragon100 on 2008-09-21
> **Bucky Ball said:**
> Eragon100 pretty well said it all! Then I guess, all going well, it's up to your imagination and how far you want to get into it.

Having said that, you may find it is not for you. It is not for everyone, different way of looking at it more than anything.

Believe me, you won't have to make ANY more changes from now on :wink:

(By the way, if you install windows, you also have to download video card drivers to get proper resolution and 3d support, and sound drivers to get sound working. The sound drivers are unnecessary in ubuntu, the video card drivers are necessary in ubuntu as well.)

---

### Post by Bucky Ball on 2008-09-21
[quote=eragon100]Believe me, you won't have to make ANY more changes from now on :wink:[/quote]

I have almost the same machine and I change it constantly! :wink:  But I like to play ... \\:D/

But you're right, to get the hardware up and running that *should* be about it. There can be unexpected idiosyncracies of course. In my case inevitably user error!

---

### Post by hard2explain on 2008-09-21
Ok guys, thanks for your help so far.  

I haven't got Vista disc myself and my machine is out of warranty so I'll have to try and speak to a friend if I want to move back.

In terms of trying to fix these niggly things with Ubuntu, I'm still having a few problems.

When I go to the Hardware Drivers section, the only device driver that appears is for 'NVIDIA accelerated graphics driver (latest cards)'.  

When I try to enable that it tries to download the file but says the following:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

It then wants to restart my system anyway, but nothing changes after it's done this.

Obviously there is nothing about my wireless controller on this screen, so I decided to try using the commands from the link that Bucky Ball gave at [http://leorockway.wordpress.com/category/lignux/distros/kubuntu/hardy/](http://leorockway.wordpress.com/category/lignux/distros/kubuntu/hardy/) 

When I tried pasting the first one in, I got the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

Am I OK to continue with going through it?

Sorry to be such a pain in the neck guys!

---

### Post by eragon100 on 2008-09-21
> **Bucky Ball said:**
> I have almost the same machine and I change it constantly! :wink:  But I like to play ... \\:D/

I change the theme and wallpaper etc often as well, but I said **won't have to**, *not* **can't** :)

---

### Post by Bucky Ball on 2008-09-21
Did you install the 64bit version of Ubuntu Hardy? Your machine probably is one. 

In a terminal run:

**sudo apt-get update **

Then try the last command again:

**sudo apt-get install build-essential**

If still no joy, open a terminal and paste in the results of:

**nano /etc/apt/sources.lst**

eragon100: yea, I edited to that effect before ... for hardware this is good.

---

### Post by eragon100 on 2008-09-21
> **hard2explain said:**
> Ok guys, thanks for your help so far.  

I haven't got Vista disc myself and my machine is out of warranty so I'll have to try and speak to a friend if I want to move back.

In terms of trying to fix these niggly things with Ubuntu, I'm still having a few problems.

When I go to the Hardware Drivers section, the only device driver that appears is for 'NVIDIA accelerated graphics driver (latest cards)'.  

When I try to enable that it tries to download the file but says the following:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

It then wants to restart my system anyway, but nothing changes after it's done this.

Obviously there is nothing about my wireless controller on this screen, so I decided to try using the commands from the link that Bucky Ball gave at [http://leorockway.wordpress.com/category/lignux/distros/kubuntu/hardy/](http://leorockway.wordpress.com/category/lignux/distros/kubuntu/hardy/) 

When I tried pasting the first one in, I got the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

Am I OK to continue with going through it?

Sorry to be such a pain in the neck guys!

I don't understand this... It should work without problem. I don't understand why it can't find the files, the server ( [http://security.ubuntu.com](http://security.ubuntu.com) ) isn't down :confused:

Just try again later, I guess the server is having network problems (which is very rare by the way.)

---

### Post by hard2explain on 2008-09-21
Hmm, do you guys think it's worth me starting again with a fresh Ubuntu installation?  Before I just used the normal Ubuntu one from their website. I'm not sure which option I chose to be honest, (which is what caused the problems in the first place when I hastily went through clicking on everything like a moron) and that way I can make sure that I've got the right version installed.

This is the result for **nano /etc/apt/sources.lst**:

GNU nano 2.0.7          File: /etc/apt/sources.lst

(There are also some keyboard shortcuts at the bottom of the screen)

---

### Post by Bucky Ball on 2008-09-21
Read my last post, I edited.

Run:

**sudo apt-get update**

Then try again.

---

### Post by Bucky Ball on 2008-09-21
Before you do this next step, go to System->Admin->Software Sources and see what is checked there.

Ubuntu Sources: tick all 4 but not source code at the bottom.
Update: The first two.

If you tick anything new, you will see an arrow up in the right tool bar telling you updates are available. Click it. Then, just to be safe, 

Run** sudo apt-get update **then[B] sudo apt-get install build-essential
[/B]
Your source.lst should then look something like the one below. As I say, you probably have a 64bit machine but you maybe have installed the i386 Ubuntu Hardy.

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main $
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ hardy main multiverse restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted $

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main multiverse restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
# deb [http://ubuntusatanic.org/hell](http://ubuntusatanic.org/hell) hardy main
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main universe multiverse$
```

---

### Post by hard2explain on 2008-09-21
Well, I've been fiddling with things a bit, (I wasn't exactly sure if I was doing things in the right order) but thanks to your advice my wireless is working properly and my screen resolution is fine!  Suddenly Ubuntu doesn't seem half as scary as it did.

Now that I've got the basics working I can start fiddling with it a bit.

Thanks ever so much guys for all your help, especially Bucky Ball, it's really cool that I was able to come on here and find someone that had a similar set up to me.  I'm sure I'll be back on here soon with some daft questions, but in the meantime:

THANKS!

---

### Post by Bucky Ball on 2008-09-21
Excellent news! Sorry, I had to sleep!

With Ubuntu, you may well grow to love it. If you come up against one of these ](*,)don't be afraid to ask questions. We were all new to it once and the sharing of info here is great. You can learn a lot in a short time. There is a lot of help out there also if you google and just put 'Ubuntu' after your topic, ie:

**Nvidia settings ubuntu hardy**

Have fun and enjoy your explorations. \\:D/

ps: don't forget to go to 'Thread Tools' at the top of this page and mark the thread as 'solved'. Post afresh next time and you will have a much better chance of getting help, plus others can surf here for a possible fix to their problems. Couple of things to remember:

* Try and be as specific as you can in your post heading (this one was pretty good! lol)
* Give details of your machine

Some things you might like to check out, if you haven't already, are Open Office and The Gimp for graphics. For burning disks Brasero is good and for ripping CDs, Audio CD extractor (sound juicer). They are all in Applications drop down menu. Also, you have probably discovered this, bottom of that menu is 'Add/Remove'. Go there if you are looking for any programs to try. Safe to download whatever you fancy and install, if you don't like, just go back there, tick and apply changes and gone. No nasty bits and pieces all over. :)

---

### Post by eragon100 on 2008-09-22
> **Bucky Ball said:**
> Excellent news! Sorry, I had to sleep!

With Ubuntu, you may well grow to love it. If you come up against one of these ](*,)don't be afraid to ask questions. We were all new to it once and the sharing of info here is great. You can learn a lot in a short time. There is a lot of help out there also if you google and just put 'Ubuntu' after your topic, ie:

**Nvidia settings ubuntu hardy**

Have fun and enjoy your explorations. \\:D/

ps: don't forget to go to 'Thread Tools' at the top of this page and mark the thread as 'solved'. Post afresh next time and you will have a much better chance of getting help, plus others can surf here for a possible fix to their problems. Couple of things to remember:

* Try and be as specific as you can in your post heading (this one was pretty good! lol)
* Give details of your machine

Some things you might like to check out, if you haven't already, are Open Office and The Gimp for graphics. For burning disks Brasero is good and for ripping CDs, Audio CD extractor (sound juicer). They are all in Applications drop down menu. Also, you have probably discovered this, bottom of that menu is 'Add/Remove'. Go there if you are looking for any programs to try. Safe to download whatever you fancy and install, if you don't like, just go back there, tick and apply changes and gone. No nasty bits and pieces all over. :)

Sorry, I had to sleep as well :(

VLC media player is a cool program to, tough you might have heard of it already. Also, be sure to check out battle for wesnoth, tremulous and nexuiz if you want to game, they are in add/remove. Another great free game is savage 1, you can get that one from [www.newerth.com](www.newerth.com) .

One last tip: program versions in add/remove are often a bit outdated, which is irritating for games. You should try to get the .deb packages for those from [www.getdeb.net](www.getdeb.net) , which always has the latest versions.
(yes, nexuiz as well). Don't forget to install wine ( [www.winehq.org](www.winehq.org) )

Good luck and have fun! :wink:

---

### Post by hard2explain on 2008-09-22
Ok guys, cheers for all the heads up, much appreciated.  I've already started loading on different bits and it all seems pretty cool.

Cheers!

---

