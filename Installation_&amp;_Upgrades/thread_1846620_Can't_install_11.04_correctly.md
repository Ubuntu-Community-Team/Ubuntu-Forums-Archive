---
title: "Can't install 11.04 correctly"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by Prowle on 2011-09-19
I'm trying to install Ubuntu 11.04 from a Live CD along Win 7 but I can't get it to work.

My first attempt was probably the best. Everything went alright except that it was very slow and hanged itself frequently and sometimes when I logged in I was stucked with a black screen (but if I moved the mouse I could see the pointer in the top ...maybe 50... pixels of the screen).

On the second go nothing worked and I got stucked at the very instant I started the PC with some error and a command line thing that I don't really know how to use..so I couldn't access Windows either.

Next up, I reinstalled Win and after the installations it tells me to remove the CD and reboot but it gets stuck with a bunch of "terminal text".
The same if I "try" the live CD and reboot.
So, now when I start the PC I immediately get into windows (not a list of options, with Ubuntu being one of them). Thus, I have a disappeared Ubuntu partition of 700 GB that I can't access.


I don't really know where the problem is.

The ISO-file/burner/burner software/CD? I've tried different combinations but all of them says it went OK.

The version? The first time, when it sort of worked, I had the 32-bit version but since then I tried the 64. The specs of my computer says it's 64-bit compatible.

Hardware problem? Or is my computer not compatible?

Thanks in advance,
Oscar

---

### Post by dino99 on 2011-09-19
how i make installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

note: less headache with 32 bits and installing the generic-pae kernel to use all the installed ram

---

### Post by Prowle on 2011-09-19
> **dino99 said:**
> here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)


It sounds like something to do from Ubuntu, which I can't reach..
And, what does that mean in plain language? How do I do that? I thought it was obvious but I'm not really good at this stuff.

---

### Post by dino99 on 2011-09-19
dont worry, its not so difficult ;) all is detailed and link is given, so follow it :(

more info can be found with the links below.

---

### Post by Prowle on 2011-09-19
The Partedmagic thing seems like a way to powerful and dangerous program for someone like me. I suspect I'd *completely* screw up my computer with that.

And the links are only to sites with *how to get started when everything is working as it should*-info, rather than troubleshooting.

I'm just asking what might be wrong and if there's a way to fix it.
I wanted to go the easy Live-CD way and something went wrong.

btw, thanks for those quick replies! :KS

---

### Post by varunendra on 2011-09-19
Hello prowle,

How much RAM the computer has? And what graphics card? For 11.04 with Unity, at least 1 GB of RAM is recommended. If the computer has less than this amount of RAM, try [Xubuntu]("http://www.xubuntu.org/") or [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") instead.

For the recovery of the 'lost' partition (deleting all data on it) without the risk of messing up the remaining ones, you can simply use the disk management tool of windows to delete the partition (which would appear as 'unknown' in windows) and re-create a new one using the same disk management tool.

---

### Post by Blasphemist on 2011-09-19
Prowle, I can point you to a couple good resources. First, this is a great site on installing a dual boot with windows. It provides very good explanation and lots of screen shots. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

Another good resource is the boot-repair program or cd. [http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

Boot repair might fix your system if the installation did finish but caused boot errors somehow.

The post above is right that we should also consider if there is some way that your system doesn't meet the minimum requirements but to me that is fairly unlikely if you have a 64 bit system. Do pass on the make and model and any hardware details that you can.

GParted is the tool I recommend for manual partitioning but that is normally not needed if you prefer that Ubuntu's installation do it for you. At this stage now, a partition could have been created and therefore be seen as not available to be used by Ubuntu without your making that manual choice. If you can boot the Ubuntu live cd/usb and run GParted, you can get a look at the partitions. The boot-repair cd also has a button for you to create a boot summary that will automatically post to a ubuntu web site with partition details. When you create that summary, take note of the site address and post it back here. We can then review it and help guide you.

---

### Post by Prowle on 2011-09-19
Thanks, varunendra, for the partition manager tips. It was super easy!

But, thus I can't do this now...

> **Blasphemist said:**
> 
GParted is the tool I recommend for manual partitioning but that is normally not needed if you prefer that Ubuntu's installation do it for you. At this stage now, a partition could have been created and therefore be seen as not available to be used by Ubuntu without your making that manual choice. If you can boot the Ubuntu live cd/usb and run GParted, you can get a look at the partitions. The boot-repair cd also has a button for you to create a boot summary that will automatically post to a ubuntu web site with partition details. When you create that summary, take note of the site address and post it back here. We can then review it and help guide you.

... so I will try to install it again and if (...) it doesn't work I'll try the GParted tool, because I agree: it seemed to work and everything seemed to be as it should except the little fact that I couldn't boot it correctly.

> **varunendra said:**
> How much RAM the computer has? And what graphics card? For 11.04 with Unity, at least 1 GB of RAM is recommended. If the computer has less than this amount of RAM, try [Xubuntu]("http://www.xubuntu.org/") or [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") instead.
> **Blasphemist said:**
> 
The post above is right that we should also consider if there is some way that your system doesn't meet the minimum requirements but to me that is fairly unlikely if you have a 64 bit system. Do pass on the make and model and any hardware details that you can.

As for the hardware, I have a HP Pavilion ([http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02930764]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02930764")) with 6GB RAM and apparently a "AMD Radeon HD 6450 1GB" graphic card.
The specs should be enough (and I've done a disk error check) but could they be incompatible anyway? Please, don't say now that this particular computer doesn't match!

---

### Post by varunendra on 2011-09-20
> **Prowle said:**
> Thanks, varunendra, for the partition manager tips. It was super easy!Anytime mate!

> **Prowle said:**
> As for the hardware, I have a HP Pavilion ([http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02930764](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02930764)) with 6GB RAM and apparently a "AMD Radeon HD 6450 1GB" graphic card.
The specs should be enough (and I've done a disk error check) but could they be incompatible anyway? Please, don't say now that this particular computer doesn't match!
Your system seems awsome!! :) Also, the graphics card seems natively supported in Natty, except that it may need 'modesetting' as stated here: [https://help.ubuntu.com/community/RadeonDriver#Require_Natty.2BAC8-11.04_and_Modesetting_Only](https://help.ubuntu.com/community/RadeonDriver#Require_Natty.2BAC8-11.04_and_Modesetting_Only)

Currently I have no experience with modesetting except using the 'nomodeset' option which should allow you to boot and work normally in 'safe graphics' mode.

And assuming that now you have only windows in your hard drive, make sure Ubuntu works flawlessly in Live mode before attempting to reinstall. Please post back if you face any problems again.

---

### Post by Prowle on 2011-09-21
> **Blasphemist said:**
> The boot-repair cd also has a button for you to create a boot summary that will automatically post to a ubuntu web site with partition details. When you create that summary, take note of the site address and post it back here. We can then review it and help guide you.
OK, I tried it and it made its job... except that it found no errors and there's still no difference; I still don't get that list in the start and can't boot Ubuntu.
But I really like its concept: just click a few buttons and it works for itself. Great for a lazy and not so computer-knowing guy like me. :lolflag: Unlike the GParted tool which I also DLed and tried but don't really know what do do with. It seems complex and to dangerous for me.
Anyway, here's the report: [http://paste.debian.net/131424/]("http://paste.debian.net/131424/").

> **varunendra said:**
> Anytime mate!


Your system seems awsome!! :) Also, the graphics card seems natively supported in Natty, except that it may need 'modesetting' as stated here: [https://help.ubuntu.com/community/RadeonDriver#Require_Natty.2BAC8-11.04_and_Modesetting_Only](https://help.ubuntu.com/community/RadeonDriver#Require_Natty.2BAC8-11.04_and_Modesetting_Only)

Currently I have no experience with modesetting except using the 'nomodeset' option which should allow you to boot and work normally in 'safe graphics' mode.

And assuming that now you have only windows in your hard drive, make sure Ubuntu works flawlessly in Live mode before attempting to reinstall. Please post back if you face any problems again.

Well, the graphics is far from flawless when in the Live CD mode. Sometimes the screen just hangs itself and I have to wait from a few to maybe 10-20 secs until it updates. And the monitor sometimes suddenly says "No Signal" and gets to sleep and don't show anything more unless I "force-reboot" the PC.

Should I do something about that before going on with trying to get the boot thing to work? (I assume it's not the monitor itself that is the problem?)

---

### Post by varunendra on 2011-09-21
> **Prowle said:**
> Unlike the GParted tool which I also DLed and tried but don't really know what do do with. It seems complex and to dangerous for me.
Anyway, here's the report: [http://paste.debian.net/131424/](http://paste.debian.net/131424/).
Partition manipulation tasks are always a bit risky, no matter how simple a particular software makes it look. But gparted complex?? I don't get it :)

> **Prowle said:**
> 
Well, the graphics is far from flawless when in the Live CD mode. Sometimes the screen just hangs itself and I have to wait from a few to maybe 10-20 secs until it updates. And the monitor sometimes suddenly says "No Signal" and gets to sleep and don't show anything more unless I "force-reboot" the PC.

Should I do something about that before going on with trying to get the boot thing to work? (I assume it's not the monitor itself that is the problem?)
In such a case, I would suggest to make a Live USB persistent install, and do your experiments with permanent settings and drivers on it rather than a native installation. This way, your native installation of Windows will not be touched, and you can be sure that in case something goes wrong with Ubuntu, you can just reboot without the flash drive to boot your windows normally as if nothing had happened.

IMHO, it is very important that you make sure which driver/ setting is going to work with Ubuntu before installing it permanently.

---

