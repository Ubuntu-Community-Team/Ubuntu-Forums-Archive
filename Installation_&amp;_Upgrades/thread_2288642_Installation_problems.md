---
title: "Installation problems"
date: 2015-07-28
forum: Installation &amp; Upgrades
---

### Post by bfallon on 2015-07-28
This looks like the beginning of a never ending story. After finally getting around to learning Linux I downloaded the iso for Mint, picked out a reasonable spec machine (Shuttle XPC, P4 3.0 GHz with 2Gb RAM and a 120Gb HDD) This is a perfect working pc on Windows. After initially installing the operating system it would not start following the restart prompt at the end of the procedure. Either blank screen, or purple/black vertical stripes eventually darkening until totally blank and a monitor message about the resolution not being the optimum.

Initially looking to the disc having errors, despite being verified, I next turned to an earlier version (Ubuntu 15.04 LTS) which I then burnt and went through the installation procedure. Again no hiccups at all and at the restart prompt I once again got the same blank screen and no activity from the HDD. Each time the screen message says the install was completed, so I assume this means successful as well. When subsequently attempting to boot from the live cd it freezes at the first part of the boot process. 

My current options are to either open the window and launch the Shuttle, which is presently a brick, through the window and go to bed. Or just go to bed and see if I have an answer that I may be able to follow tomorrow. I warn you I am a complete blank when it comes to Linux terminology so please word your advice in the way an idiot can understand.

---

### Post by Bucky Ball on 2015-07-28
*Thread moved to **MINT**.*

You turned to an earlier version? What version were you trying to install originally? 

When you boot from the install media, can you 'Try Mint' without issue? When you boot the disk to install, can you hit a key when the screen gets to the icon down the bottom. That should take you to some options. Hit F6 and choose the 'nomodeset' option. Proceed. Any different?

PS: You might also consider posting this in the Linux Mint forums. Good luck. :)

---

### Post by bfallon on 2015-07-28
Yes I originally tried Mint but after failure I reverted to Ubuntu 15.04, thinking it may be better for an older machine (which doesn't seem to be the case) so I am on, or not on I suppose, Ubuntu. That is why it is in this forum and not Mint. 

Subsequent attempts to boot from the install media freeze the machine. I have now got to the stage where it freezes with this on screen;

[OK] Started CUPS Scheduler.
[OK] Started Authenticate and Authorize Users to Run Privileged Tasks...
[OK] Started Accounts Service.
[OK] Started Modem Manager.
[OK] Started Network Manager.
       Starting Network Manager Wait Online...
[OK] Reached Network Target.
       Starting /etc/rc. Local Compatibility...
[OK] Starting /etc/rc. Local Compatibility.
       Starting Wait for Plymouth Boot Screen to Quit...

And from this point it does absolutely nothing

---

### Post by Bucky Ball on 2015-07-28
This thread has been moved back. Don't like doing that but my mistake.

---

### Post by ubfan1 on 2015-07-29
What video does your machine have?  You might need the proprietary drivers to improve performance over the default, but you might need either Lubuntu or xubuntu with only 2G.  I found unity eventually upgraded to the point that my ubuntu 14.04 wouldn't run with video issues on my 2G HP, but Lubutu runs just fine.

---

### Post by bfallon on 2015-07-29
s I am starting the install from a blank, unpartitioned drive, allowing the installation to format and create the correct parameters for installation I am taking the view that any proprietary drivers required are downloaded during that part of the procedure. I am using the onboard graphics, I don't actually have a reasonably decent card that will go in, it's AGP and now that it is getting harder to find higher spec cards that will run anything past Win XP the prices are through the roof. That was one of the reasons I used this machine - the specs required for Ubuntu being (theoretically) substantially lower than it has. I am at the stage of wondering if this is another Vista type fallacy - they said that will run on 1 Gb if you remember but it hardly crawled. 
I am not definitely committed to using this machine, I can pull another older thing off the shelf and play with that to see how things pan out. I have a few HP desktops but they will be something like a 2.8 Celeron with Intel 915 chipset, not likely to go up from 2 Gb RAM because I only have 1 Gb memory sticks of 266 or 400 and the boards have (from my memory) only got 2 slots on. It's probable that I will come up against the same problems using one of them.

Going to the hitting F6 suggestion that was offered, I can get the various menus up on screen doing that during the live CD boot, but when I manage to select the nomodeset option hitting enter only selects or deselects the option in the submenu, but no keystroke seems to cause further operations.  
I will grab an iso of Lubuntu and burn it to see if that gets further, discs are cheap, and it beats tearing out what little remains of my hair over what is essentially a learning project.

---

### Post by Bucky Ball on 2015-07-29
Use Lubuntu for those specs, or Xubutnu, yes. Not familiar with Mint so no idea how lightweight or not it is.

Nothing happens when you select 'nomodeset'. Were you expecting something visible? You just choose nomodeset then proceed with the install. The machine will do it's thing with the 'nomodeset' option enabled. That's it. You won't visibly see any action when you set the option or be asked to do anything else. Just proceed.

---

### Post by dino99 on 2015-07-29
Try Lubuntu Trusty with that driver

[http://packages.ubuntu.com/trusty/nvidia-173](http://packages.ubuntu.com/trusty/nvidia-173)

---

### Post by bfallon on 2015-07-29
Well it looks like I am getting somewhere, but in a different direction. I have managed a successful install of Xubuntu 15.04 on to a little netbook thing, not much use to me other than learning the OS due to it only having a 12Gb SSD. But as it was another dust gatherer it will serve the purpose. That does leave me with sorting out why the repeated failures happened on the other machine, but I've always learned more from getting past problems than I do from sitting watching a progress indicator working away. 
Thank you gentlemen for sending me in the direction I needed to go.  This all takes me back to installing MSDOS from 8 floppies before putting Win 3.1 on.... Yes I am that ancient. :lolflag:

---

### Post by Bucky Ball on 2015-07-29
Nice you're getting somewhere. Xubuntu's great and very configuarble. Has the machine got a couple of Gb of RAM? That should fly if so with Xubuntu. :)

If you want to keep going at the original issue here, go for it! If not, please see the first link in my signature and start new threads as required (solving doesn't close the thread to further discussion). ;)

PS: Down the track you might like to try a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD"). That will get even lighter (Ubuntu base kernel only to start) on those old machines. I use a mini with xfce4 on a modern i3 with 4Gb and if it's not quite rocket it's definitely speed boat.

---

### Post by bfallon on 2015-07-30
So yes, I have a working installation that will allow me to start learning. It is the bare minimum though and I will still want to press on and get a reasonably decent system, so next thing is to try both of the suggestions offered - Lubuntu Trusty and a minimum install. 
My main consideration for sticking with this Shuttle is because I have a place it can fit in my workroom but if necessary I can go to plan B, which is to drop another drive into the system I use most of the time, that's quad core with good graphics card and 8 Gb ram. Meanwhile let the games continue, I'll keep it updated how I'm doing as things develop, and once again thanks for the ongoing assistance.

---

