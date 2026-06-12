---
title: "can't install ubuntu no matter what"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by movgourouni on 2011-11-06
Hi Guys,

HELPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP.


I've got a toshiba laptop, satelite pro A60 gk, intel pendium 4 at 2,8 GHz, ATI graphics card (can't remember more specifically right now), 256 RAM and 40GB HD. Don't know if more data is required. Yet, I've checked at the minimum system requirements, and apart from the 11.04 release (at which I think fails the RAM part) it does support the previous ones.


It is indeed an obsolete device and that is the reason I need to install ubuntu. It runs winxp pro prety decently, but it would be a completely different laptop with ubuntu on it.

I tried recently to install ubuntu 11.04 but unfortunately it got back with that unsolvable problem [http://ubuntuforums.org/showthread.php?t=1811913](http://ubuntuforums.org/showthread.php?t=1811913) .I tried to do as much of the instructions given at that thread, as my pc knowledge would let me to, still not much success.

Then, I thought, trying a previous version would solve my problems. I tried both ubuntu 10.04 LTS and Karmic Koala, tried to install them through windows (my cd-rom drive is out of order and my bios doesn't have booting from a usb device as an option). I still run my laptop with winxp only.

The problem is that the installation through windows goes fine until it asks me to reboot. It then gets me to grub and I choose ubuntu to complete installation. It starts with a bar saying installation check, goes up to 5% making the ext4 relevant actions and then goes on with the installation giving me the presentation of the os silmutaneously (I guess this is all pretty normal up to now, same thing happened with my desktop without any problems). 

The problem is that at some point (which varies from 19% to 68% of the installation --- never got anything better than that) it gets stuck and the installation never gets completed. The screen freezes and so does the mouse.


WHYYYYYY???? I'm about to cry. As far as I know, my obsolete laptop meets the minimum system requirements. Why can't I get the installation completed and what do I do wrong? What can I do to make it work.


I thank you all in advance.
Please, go easy on me with your instructions as I am not a computer genious, I many times have to read a lot to understand what computer experts are talking about, most of them without success.


Panos

---

### Post by MAFoElffen on 2011-11-07
> **movgourouni said:**
> Hi Guys,

HELPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP.


I've got a toshiba laptop, satelite pro A60 gk, intel pendium 4 at 2,8 GHz, ATI graphics card (can't remember more specifically right now), 256 RAM and 40GB HD. Don't know if more data is required. Yet, I've checked at the minimum system requirements, and apart from the 11.04 release (at which I think fails the RAM part) it does support the previous ones.


It is indeed an obsolete device and that is the reason I need to install ubuntu. It runs winxp pro prety decently, but it would be a completely different laptop with ubuntu on it.

I tried recently to install ubuntu 11.04 but unfortunately it got back with that unsolvable problem [http://ubuntuforums.org/showthread.php?t=1811913](http://ubuntuforums.org/showthread.php?t=1811913) .I tried to do as much of the instructions given at that thread, as my pc knowledge would let me to, still not much success.

Then, I thought, trying a previous version would solve my problems. I tried both ubuntu 10.04 LTS and Karmic Koala, tried to install them through windows (my cd-rom drive is out of order and my bios doesn't have booting from a usb device as an option). I still run my laptop with winxp only.

The problem is that the installation through windows goes fine until it asks me to reboot. It then gets me to grub and I choose ubuntu to complete installation. It starts with a bar saying installation check, goes up to 5% making the ext4 relevant actions and then goes on with the installation giving me the presentation of the os silmutaneously (I guess this is all pretty normal up to now, same thing happened with my desktop without any problems). 

The problem is that at some point (which varies from 19% to 68% of the installation --- never got anything better than that) it gets stuck and the installation never gets completed. The screen freezes and so does the mouse.


WHYYYYYY???? I'm about to cry. As far as I know, my obsolete laptop meets the minimum system requirements. Why can't I get the installation completed and what do I do wrong? What can I do to make it work.


I thank you all in advance.
Please, go easy on me with your instructions as I am not a computer genious, I many times have to read a lot to understand what computer experts are talking about, most of them without success.


Panos
First- What is the CPU, video and RAM on that laptop.

Second does your laptop boot from floppy?  If so, you could boot from the plop boot manager installed on a floppy.  That would allow you to boot from a cd...  There are lots of different options.

---

### Post by robert shearer on 2011-11-07
Panos, your laptop meets the minimum requirements for a _command line install_ of Ubuntu.  ie **not enough ram** for a GUI.
You really need 500 or better and you only have 256. (and even 500 would be sluggish)
Either add more ram or try a **lighter desktop version** of Ubuntu.
**Lubuntu** [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu) 
[http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/)
**Xubuntu**  [http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

---

### Post by movgourouni on 2011-11-07
> **MAFoElffen said:**
> First- What is the CPU, video and RAM on that laptop.

Second does your laptop boot from floppy?  If so, you could boot from the plop boot manager installed on a floppy.  That would allow you to boot from a cd...  There are lots of different options.



Hi there MAFoElffen,

 think that intel pendium 4 at 2,8 GHz is the answer to the cpu question, if not let me know

RAM is 256 mb and my video card is ATI MOBILITY RADEON 7000 IGP with 64mb memory and my ram is 448 mb according to the results given by the dxdiag prompt

My bios gives me the choice to boot from a floppy but unfortunately it doesn't have a floppy drive. However, 2 years back I tried to install ubuntu from a bootable cd (back then the cd drive was still working decently) and it got stuck again at 64%. I thought at the time that the problem was the drive, but after trying the installation through windows and having the same results, I am starting to believe that the drive wasn't the actual problem.

Any ideas? I think that there must be a clash with my hardware, but then again I couldn't specify what.

Thanks for the answer and your time anyway man.

---

### Post by movgourouni on 2011-11-07
> **robert shearer said:**
> Panos, your laptop meets the minimum requirements for a _command line install_ of Ubuntu.  ie **not enough ram** for a GUI.
You really need 500 or better and you only have 256. (and even 500 would be sluggish)
Either add more ram or try a **lighter desktop version** of Ubuntu.
**Lubuntu** [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu) 
[http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/)
**Xubuntu**  [http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)


Hi Robert,


do you think that, given my limited knowledge, I should go for a command line install?

Moreover, running the dxdiag prompt, I found out that my RAM is 448 mb. The point is that it gets me at some point of the istall, so I thought that RAM wouldn't be a problem.

Could it be anything else? Do you think that adding some RAM up to 1GB f.e. would solve the problem? Or could it be perhaps, that I must change any settings for instance and it would then complete the setup?

Sorry for the number of questions, I'm just trying to be specific.

Thanks for your answers.

---

### Post by BillyBoa on 2011-11-07
I believe that you are losing your time. Maybe you could search for a special Linux distro, with exceptionally small size, but again I warn you that the results aren't worth the effort.

---

### Post by ottosykora on 2011-11-07
just to mention, some time ago I was trying to install ubuntu 8.10 on an old dell laptop. It had 256 ram then. I could install 8.04 but not 8.10 on it via the GUI. I tried then kubuntu, this also crashed on login screen and then xubuntu 8.10 which did work.

I was however able to install 8.10 ubuntu from the alternate CD, that means the procedure with the command line, well it has some graphical help in it. 
And it did work then with 256ram, slow , but stable.

I then gave it more ram (512 now in fact) and was able to install also under GUI and in fact I run this part still with 10.04LTS until now, with xubuntu and ubuntu desktop for selection. 
Slow but works.

So I think the advise with the alternate CD , the kind of command line install, might well bring you the installation and all might (or might not) work later. The installer GUI seemed to be always more resources hungry then the normal operation later.



But then: how to do a wubi install (this seems to be the you are trying to do) this way I dont know.
The wubi install stops during install for various reasons, the last time I used it, it was because I had linux swap partition on the computer from some other installs and it tried to use both swap prt and swap file at the same time.

---

### Post by MAFoElffen on 2011-11-07
> **movgourouni said:**
> Hi Robert,


do you think that, given my limited knowledge, I should go for a command line install?

Moreover, running the dxdiag prompt, I found out that my RAM is 448 mb. The point is that it gets me at some point of the istall, so I thought that RAM wouldn't be a problem.

Could it be anything else? Do you think that adding some RAM up to 1GB f.e. would solve the problem? Or could it be perhaps, that I must change any settings for instance and it would then complete the setup?

Sorry for the number of questions, I'm just trying to be specific.

Thanks for your answers.
System requirements on Ubuntu say 1GB.  I've installed on 512MB with Pentium III, but I wouldn't recommend with anything less. That was "noticeable."  Less memory, as you have, you were probably bouncing the memory limit for that installer.

Have you tried the Alternate Install CD or the Minimal Install CD?  The Xubuntu or Lubuntu Install CD's both run in 128MB of memory, where as the Alternate Install CD and the Minimal Install CD both run in 64MB of memory.  The Alternate and minimal CD's both get to a point in the install, where you pick your desktop, then go on...   Try those first.

/* ------------------ */
Tell you what, you are already going to have a challenge with how to boot an install ISO. You said that your BIOS boot order is Floppy, HDD... That's it?  No CD or USB boot?  You said you do not have a floppy?  Did the CD replace the Floppy? Does Toshiba  Support have any BIOS Upgrades for your laptop? If so, that would be a worthwhile thing to install before you do anything!!!

Here is my warning to you-->  Right now, the only way into your laptop is through booting the hard disk...  You are trying to install another OS to your hard disk, where it is going to install a boot manager-- That sometimes is not successful in it's initial install -OR- the OS sometimes has problems on updates...  

To me, this is just something that goes along with the territory and is rare.  I have many ways in. But to you, without an external way into your system, you might be at risk of losing access to both Linux and Windows XP?

Look into the BIOS update.  A lot of older laptops, if they had a CD or later had a CD as an option > Had BIOS update to allow boot from CD.  USB boot didn't seem to be a priority in that... 

That's what i had to do for an old Dell laptop someone gave me. It had floppy and HDD w/ Windows NT workstation (probably older than yours).  Even though it had a USB port, it was USB 1.0, so could not support a redirected boot from the USB.  Traded for a CD Drive, which replaced the FD in the case.  [COLOR=Red]BIOS had to be updated to boot from the CD drive.[/COLOR]  Memory on this laptop upgraded to max is 512 MB.  Installed and running XFCE. Network access is PCMCIA ethernet and wireless cards, because it has neither internally...

---

### Post by movgourouni on 2011-11-07
> **MAFoElffen said:**
> System requirements on Ubuntu say 1GB.  I've installed on 512MB with Pentium III, but I wouldn't recommend with anything less. That was "noticeable."  Less memory, as you have, you were probably bouncing the memory limit for that installer.

Have you tried the Alternate Install CD or the Minimal Install CD?  The Xubuntu or Lubuntu Install CD's both run in 128MB of memory, where as the Alternate Install CD and the Minimal Install CD both run in 64MB of memory.  The Alternate and minimal CD's both get to a point in the install, where you pick your desktop, then go on...   Try those first.

/* ------------------ */
Tell you what, you are already going to have a challenge with how to boot an install ISO. You said that your BIOS boot order is Floppy, HDD... That's it?  No CD or USB boot?  You said you do not have a floppy?  Did the CD replace the Floppy? Does Toshiba  Support have any BIOS Upgrades for your laptop? If so, that would be a worthwhile thing to install before you do anything!!!

Here is my warning to you-->  Right now, the only way into your laptop is through booting the hard disk...  You are trying to install another OS to your hard disk, where it is going to install a boot manager-- That sometimes is not successful in it's initial install -OR- the OS sometimes has problems on updates...  

To me, this is just something that goes along with the territory and is rare.  I have many ways in. But to you, without an external way into your system, you might be at risk of losing access to both Linux and Windows XP?

Look into the BIOS update.  A lot of older laptops, if they had a CD or later had a CD as an option > Had BIOS update to allow boot from CD.  USB boot didn't seem to be a priority in that... 

That's what i had to do for an old Dell laptop someone gave me. It had floppy and HDD w/ Windows NT workstation (probably older than yours).  Even though it had a USB port, it was USB 1.0, so could not support a redirected boot from the USB.  Traded for a CD Drive, which replaced the FD in the case.  [COLOR=Red]BIOS had to be updated to boot from the CD drive.[/COLOR]  Memory on this laptop upgraded to max is 512 MB.  Installed and running XFCE. Network access is PCMCIA ethernet and wireless cards, because it has neither internally...



MAFoElffen, hi again,

RAM is 448 mb afterall and regarding the boot options, they are HDD - CD ROM - FD - LAN, but unfortunately the cd drive is out of order.

I didn't even know about alternate and minimum cd's. I'll try them.

As far as my bios is concerned, I have updated it already, but no luck. Didn't give me more boot options. The reason that I am trying to install ubuntu through windows is that I was afraid too of the potential, that I could load neither of OS's.

This is all the new info I've got today, I've started to believe that it will be really difficult to install ubuntu. 

Would you recommend me to try installing it with the command line process? Can I do that through windows, or does it have to a complete install?


MAFoElffen thanks again for your time and advices. They are very specific and helpful, regardless the outcome.

---

### Post by MAFoElffen on 2011-11-07
> **movgourouni said:**
> MAFoElffen, hi again,

RAM is 448 mb afterall and regarding the boot options, they are HDD - CD ROM - FD - LAN, but unfortunately the cd drive is out of order.

I didn't even know about alternate and minimum cd's. I'll try them.

As far as my bios is concerned, I have updated it already, but no luck. Didn't give me more boot options. The reason that I am trying to install ubuntu through windows is that I was afraid too of the potential, that I could load neither of OS's.

This is all the new info I've got today, I've started to believe that it will be really difficult to install ubuntu. 

Would you recommend me to try installing it with the command line process? Can I do that through windows, or does it have to a complete install?

MAFoElffen thanks again for your time and advices. They are very specific and helpful, regardless the outcome.
Command LIne for you?  Depends on your experience level.  From what you have said, probably not.

Ubuntu with less that 512MB? I found at that- is very slow (was swapping  to disk a lot) and on laptops and you'll find the LCD graphics "washing  out."  (I thought it was out or close to being out of memory) On  Lubuntu and Xubuntu , they still run okay in 256MB. 

The Alternate or Minimals CD's would have to be booted from your CD.  I think USB would have to be via a redirect from PLOP.  PLOP also has a script to add itself to a Windows Boot menu.  Or if the CD stills works/boots, but you just didn't trust it, Slackware Linux has an ISO that will redirect to the USB to boot from there. Limitation on that is that it has to be USB2.0 or newer.  Some earleirs 1.0 ports still don't work with this.

Another way in-- would be to install Grub2 onto your hard disk (It's own partition).  You can create a menu item to boot CD or USB from the Grub menu.  --OR-- What is handy about that option is that you don't even need to go CD or USB, you could then boot directly from the ISO file itself.

---

### Post by collisionystm on 2011-11-07
The max memory for your computer is 1.25gb.

Order a 1gb stick from crucial memory. 34.99.

Your computer should be running good after that

[http://www.crucial.com/store/listparts.aspx?model=Satellite%20Pro%20A60%20Series&Cat=RAM](http://www.crucial.com/store/listparts.aspx?model=Satellite%20Pro%20A60%20Series&Cat=RAM)

---

### Post by 1clue on 2011-11-07
I strongly recommend that if you are a Linux novice, that you try first with relatively recent hardware (no more than 3 years old), especially with a mainstream distribution like Ubuntu.

I really don't understand people's inclination to install Linux on old junk, especially when they're new at it.  There's a really good chance that part of the hardware is nonfunctional, and even so the mainstream distributions are all aimed at recent hardware so the distro will not be fast or even especially useful if it even works at all.

---

### Post by collisionystm on 2011-11-07
> **1clue said:**
> I strongly recommend that if you are a Linux novice, that you try first with relatively recent hardware (no more than 3 years old), especially with a mainstream distribution like Ubuntu.

I really don't understand people's inclination to install Linux on old junk, especially when they're new at it.  There's a really good chance that part of the hardware is nonfunctional, and even so the mainstream distributions are all aimed at recent hardware so the distro will not be fast or even especially useful if it even works at all.

Well most people use a free OS on a free computer.

Not everyone has the luxury of a newer machine or even wants to buy a new computer just to put Ubuntu on it.

---

### Post by MAFoElffen on 2011-11-07
> **1clue said:**
> I really don't understand people's inclination to install Linux on old junk, especially when they're new at it.  There's a really good chance that part of the hardware is nonfunctional, and even so the mainstream distributions are all aimed at recent hardware so the distro will not be fast or even especially useful if it even works at all.
Sidenote, but pertinent... (I work at a computer recyclers)  Why Linux on old hardware?  Because Old hardware has problems running newer Win OS'es.  Vista started cutting out hardware, saying it had to be compatible. Win7 continued that trend.

Linux does give a lot of those machines new life. It has low overhead- comparatively.  With that low overhead, its performance is higher. It does have support for a lot of old hardware, where as Win7 and Vista just says that same hardware is not compatible.  I have nothing against M$... My Little brother is a group leader there.  

I don't recommend a "Command Line" Linux install to a new user.  I remember supporting PC-DOS on IBM PC's (8086) in the Corporate World with Terminals sitting along side of them.  "Command Line" Linux assumes you know what you are doing... in a big way.  Admittedly, GUI interfaces are easier for new users to learn.  

There are low resource GUI based Linux distro's that run on low-resource hardware, that run faster then... Win OS'es.  New low-end users that use the internet and wirite a few notes here and there-- most of those users are not even aware of what OS is running underneath.  

Old hardware with Linux? ...Also has the advantage of being very cost efficient.

New hardware with Linux? Very fast and comfortable.  Some hardware, I have to wait for driver support to get supported.  It is usually about a 6 month lag. Some vendors support Linux or not.  Some get opensourced with deb packages, some as rpm / where I have to convert, some I have to compile myself. Some new do not get supported.

---

### Post by 1clue on 2011-11-07
Windows 95 started cutting out new hardware.  Vista continued a long tradition.

Installing a UI-hungry distro like Ubuntu does NOT have "low overhead."  It's at least as resource hungry as Windows 7.  Try running a modern Windows on identical hardware as what you run Linux on sometime, and use the defaults for installing Linux.

Back before XFree86 was stable, people started saying that Linux was the fastest OS you could put on a computer.  It might have been true then, but it was only true because it was the only one not running a UI.

Since then, it's definitely possible that a desktop system could be faster than equivalent Windows software of the same era, but only with a lightweight distro.  Ever since RedHat came into the limelight, there has been a movement to make Linux be every bit as functional as Windows, mostly by shamelessly copying the look of Windows or Mac.  As nearly as I can tell, none of these guys cared a bit about speed.  Ubuntu looks great and is easy to use, but it's not in any way a "light" distro.

That doesn't bother me in the slightest, I just made sure I had hardware adequate to the task.  But assuming that Ubuntu with all its bells and whistles is going to outrun Windows 7 is a lie.

---

### Post by MAFoElffen on 2011-11-07
> **1clue said:**
> Windows 95 started cutting out new hardware.  Vista continued a long tradition.

Installing a UI-hungry distro like Ubuntu does NOT have "low overhead."  It's at least as resource hungry as Windows 7.  Try running a modern Windows on identical hardware as what you run Linux on sometime, and use the defaults for installing Linux.

Back before XFree86 was stable, people started saying that Linux was the fastest OS you could put on a computer.  It might have been true then, but it was only true because it was the only one not running a UI.

Since then, it's definitely possible that a desktop system could be faster than equivalent Windows software of the same era, but only with a lightweight distro.  Ever since RedHat came into the limelight, there has been a movement to make Linux be every bit as functional as Windows, mostly by shamelessly copying the look of Windows or Mac.  As nearly as I can tell, none of these guys cared a bit about speed.  Ubuntu looks great and is easy to use, but it's not in any way a "light" distro.

That doesn't bother me in the slightest, I just made sure I had hardware adequate to the task.  But assuming that Ubuntu with all its bells and whistles is going to outrun Windows 7 is a lie.
I agree on most of that... I test and bench mark dev_builds of Win, Linux and Unix. Windows 8 is even more resource hungry.  Linux Side, Ubuntu's Unity is hhuunggrryy.  same on Gnome 3 is great. There is catchup needed yet there.  Fastest I've worked on yet was Solaris 11 with Java Desktop on a Quad CPU- Opteron 12 cores with SSD's. 

Look at my sig line... I have benchmarks for the various. 

*** But I have to stop there.  (Before a MOD comes in and gives us a warning) I think we are now a bit off-topic from the OP's problem, which is installing Linux on an older laptop.  I think he said he had other PC's running Ubuntu, > Has an older Laptop that he just wants to re-use, keep productive, make useful again...  I can see that. 

Like I said before, I think XFCE or LXDE would be okay on that.  I know that full blown Ubuntu would run poorly if at all with those lmited resources... Unless he upgraded the RAM to 1GB or more.

---

### Post by 1clue on 2011-11-07
OK I'll throw one last one in there and then let the OP have the thread back.

XFCE and LXDE are good low-resource alternatives, but AFAICT this thread is for stock Ubuntu.

The 1G option was pretty much a prerequisite IMO for any mainstream distro.

If you're short of cash and recycling some old system because you can't afford a new one, that's one thing.  But IMO that's not what generally happens.  The most common thing I see is somebody uses their old computer until it doesn't run all the new stuff with Windows, then they buy a new box and install Linux on the old one because they just can't stand to throw it away.  Or they clean out the closet and find something from 10 years back and decide to make it into a project.

In that case, Linux is just a deodorizing trash bag.  It lets you keep your junk longer.

In my experience, if you avoid the bleeding edge hardware then you also avoid bleeding edge prices.  Buy new hardware, install Linux on it as its first operating system.  You can pick the hardware that works, and you get new hardware with a new operating system that's really well matched to it.  Contemporary distros work best with moderately new hardware.

---

### Post by robert shearer on 2011-11-07
> Like I said before, I think XFCE or LXDE would be okay on that. I know that full blown Ubuntu would run poorly if at all with those lmited resources... Unless he upgraded the RAM to 1GB or more.

Which, of course, brings us right back to...

> Either add more ram or try a lighter desktop version of Ubuntu.
Lubuntu [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
[http://cdimage.ubuntu.com/lubuntu/re...11.10/release/](http://cdimage.ubuntu.com/lubuntu/re...11.10/release/)
Xubuntu [http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)
  ;)

---

### Post by Rodney9 on 2011-11-07
Lubuntu Has Breathed New Life Into My Old Machine

[http://ubuntuforums.org/showthread.php?t=1875976](http://ubuntuforums.org/showthread.php?t=1875976)

---

### Post by movgourouni on 2011-11-08
Hi guys,

the reason that I want to put ubuntu in my computer as one more option is that I can't afford going for a new device for the time being.

My laptop, although obsolete, still functions decently with xp SP3, given its potentials of course and without comparing it with more modern devices.

I've got a desktop, xp home sp3, intel pendium 4 at 2,8 GHz, 512 GB RAM and a more potent graphics card (but nothing exquisite), at which I installed Ubuntu 10.04 LTS and its performance was surprisingly enhanced.

Therefore, I thought putting ubuntu at my laptop would revive it as well. Had the money to go for a new device, I would install ubuntu as well, cause I think it a lovely OS. But a new device isn't always an option.


MAFoElffen, I read about command line install and the alternate cd and the GRUB 2. Command line install isn't an option for me anymore. I think I'll go for the alternate cd first and if nothing happens, for GRUB 2. I hope something of them will do the thing.

Thanks for the solutions.

---

