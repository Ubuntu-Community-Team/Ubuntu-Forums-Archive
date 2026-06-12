---
title: "T91MT Install Hang"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by tetris999 on 2011-01-19
Hello everyone, I've heard there were some new graphics drivers that were released; which made me want to install xubuntu on my t91mt, obviously this isn't the reason i'm here for however. 

The problem is simple, as soon as the gui installation runs and i click on english then proceed past the checks that have "connected to internet"; "this much space is free" etc, the installer totally hangs.

It's not a matter of patience because obviously i'm installing this from usb and i let it go OVERNIGHT; so there's obviously a problem and not myself being impatient for it to start. 

I've tried to get some info as to why this was happening, live usb would work, i could load into xubuntu fine; but i just could not for the life of me install the OS to my main drive. 

I have windows ultimate x86 installed already; so my first assumption was that this was conflicting with the install. With logical deduction of the fact that Gpart fails to load and crashes under my live usb os only leads me to the fact that some type of partitioning error is to blame. 

I've ruined my MBR in hope that i could somehow just get linux to recognize and continue the installation, but my methods have proven to be unsuccessful. The question is, what could be getting ubuntu to hang at this SPECIFIC part of the install and WHY does gpart have the need to crash whenever i try to open it up?

Help would be greatly appreciated, thanks :); the LAST thing i want to do is to get rid of my windows 7 installation. :(

P.S. This problem happens with Ubuntu as well; hangs in the exact same place.

---

### Post by H3g3m0n on 2011-01-20
Posting this from my T91MT, so it does work.

What method did you use to get the USB drive. I used usb-creator-gtk which should come on a standard Ubuntu install.

Also can you choose the 'try ubuntu' option? When I chose that option I was getting a lockup, I ctrl+alt+f1'd to a VT and checked the process listing in 'top' to find lzma using %100 cpu usage, I killed it and things went on as normal. I think it might have something to do with the 'persistant user storage on usb drive' option in usb-creator-gtk

Provided you can get into the livecd environment, you are probably going to have to do a little console work.

Firstly try running 'gparted' in a console and see if it prints out any error messages.

Try 'sudo fdisk -l /dev/sda' in the console and see if it prints out a valid drive map or any errors about partition mapping.

Also try 'sudo cfdisk' which is a text gui that will allow you to create a partition if gparted is crashing, then you will also need to make the actual filesystem mkfs.ext4 /dev/sda#

If you create a partition correctly, you may need to use the alternate cd if the installer is still crashing.

There is a lot of after install setup on this system though, although most of its fairly basic and just a few cut and paste commands. Check the other posts, also the eeeuser wiki has a section on it.

The new EMGD graphic drivers aren't a whole lot better that the previous PSB ones. I'm actually using the PSB ones as the EMGD ones don't support screen rotation (rotation using the stud button also needs tweaks to get it to work, I haven't gotten around to fixing that yet but I'll post it on eeeusers wiki when I do).

Video playback is a little funny on here, you need to use mplayer and specify vfm=xvid in /etc/mplayer.conf or some videos will be jittery and blocky. vlc doesn't have a workaround for that bug. Flash and HTML5 video in YouTube on the otherhand is smooth and flawless =/

---

### Post by tetris999 on 2011-01-21
Hey h3gd3mon 

Well in the end i solved my problem, but it turned out to be none of the problems listed above. Ridiculously, the problem lied with the usb stick i was using, ubuntu seriously did not like this usb stick at all unfortunately; which is funny because windows 7 installs perfectly fine from it. 

I got it working by attaching a usb card reader and using a 1GB memory stick i had lying around. Lo and behold, it worked. I have no idea why a silly contraption worked, but that's what happened. 

I'm having problems setting up though (obviously); I've gotten the graphics drivers installed and I've used the multitouch screen drivers that you posted up. I'm TRYING to get plippo's multitouch to work, but my methods, of course, are proving unsuccessful. Also, I'm trying to use the update manager for what it looks like; upgrading to Xorg 1.8, but the manager keeps telling me some packages are unauthorized, argh.

Thanks for the help btw, I used lots of what you mentioned in your post; i guess i can say the initial problem is solved now.

I'll check out the wiki on the eeeuser site, all this searching around for fixes is a headache.

---

