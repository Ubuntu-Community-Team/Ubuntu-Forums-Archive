---
title: "Problems with older install (Ubuntu 8.04)"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by gallinka on 2012-07-19
Hello everyone,
 
I am trying to install Ubuntu 8.04 on an older computer. My intent was to install LinuxCNC (ECM2) on a computer to use as a CNC controller. I decided after reading the minimum system requirements to install one of the older versions (2.3) which is provided on a Live install CD/distro of Ubuntu 8.04. This was not successful. One of the problems I immediately identified was that the CD-ROM seemed to have trouble loading the CD (so far I have gotten nor further than the installation selection screen). I decided to burn a new CD with the alternate install ISO (the one avalable from Ubuntu directly) at 8x speed. This seemed to alieviate the CD-ROM seeking problem (sometimes it would be quick and sometimes it would take more than a minute or fail). However, the same problem came up when I made a selection from the install screen. I originally burned 10.04 but I cannot remember the symptoms of that unsuccessful install, they were simimlar. I have not compared MD5 checksum (on the 3rd cd with 8.04 only on it) but plan to do that tommorow.
My symptoms are these:
 
1. When I try to preform a normal install I get a grey box that says loading kernel. This has a percentage indication that goes to 100% in about 10 seconds. After that my screen clears and I immediately (almost) loose video sync (horizontal lines that slowly shift) like my resolution/refresh is over/under range. I have tried with a LCD monitor hooked up that has a max (native) resolution of 1024x1280, it is hooked to the computer through a VGA connector. I have also tried it on a very old 14" monitor but I am not sure (very unlikely) is supports resolutions above 800x600. Occasionaly I can seen an error that says "ACPI: Could not Find System Description Tables" (I am not sure if that is verbatim, I will re-check tonight and re-post if wrong) before the loose sync problem. After 1-3 seconds I have no further CD-ROM activity and pressing keys on my keyboard does not show any progress or change.
 
2. My first thought was to try an alternate installation method but as I had already tried the alt install ISO it seemed that boot parameters where my best bet. In the course of trying "nomodeset" and "apci=off" and "vga=771" (800x600 for my video chip which I verified), I had removed the "quiet" parameter. This allowed me to see further boot information (obviously). I noticed the loose sync issue (same end result as before) occurs on a line that says "initrd: Freeing up 5.....". I cannot give more info as I don't always see the whole line draw and it displays for about .25 seconds.
 
3. I don't think this is relevant but when I tried (incorrectly) to set "vga=800x600" I got a seletion screen that asks me for a video mode. I think this is asked by the kernel as it only offers collom/row seletions and none of them get me any further in the install process.
 
The troubleshooting steps I have taken are limited but include:
 
1. Trying (one at a time) the boot parameters suggested in other forum post like (but not limited to):
 
nomodeset
vga=771, 772 (just different color depths of 800x600, tried for 1024x768 too)
acpi=off
noapci
pci=noacpi
 
ect (i can't remeber the whole list but I tried all 10 or so parameters)
 
2. Changing different settings in the bios - I turned off ACPI, set bios to assign IRQ to video (and not to). I tried a few others but no success/not relevant/can't remeber (I tried a lot, I have already put in 4-6 hours of TS into this install)
 
3. Looked up info on the computer I am trying to install to, verifying there was no explicit problems with it and Ubuntu. It has a limit of 256MB of RAM but I believe (correct me if I am wrong) that is enough for 8.04. There is no shared video memory. My specs are as follows:
 
-SBC8360 single board computer:
-Celeron 850 mhz, 100 mhz FSB
-256 MB ram (1 GB ECC chip, recognized as 256 - tried ecc mem/no ecc mem in bios)
-Intel 440BX chipset (the SBC8360 has only one memory slot hence the 256mb ram)
-Chips and Tecnologies 69000 display chip (there is no seperate display adapter - SBC)
- 2mb video ram, max resolution of 1024x1280
-The SBC has several other integrated peripherals - 4 com ports, LPT, DIO, audio, LAN, etc
 
Unfortunately, my upgrade options are very limited. The above is pretty much all I can put in the computer. I could use the PCI slot (one slot) to try a different video card (just realized this while writing, may try tonight). The SBC8360 is mounted in a small computer case/assembly that has an intergrated LCD (native 800x600) and touch screen (elo tech., resistive). For this reason I am unable/unwilling to try a different computer or upgrade.
 
Any info or suggestions anyone can give me would be appreciated. I plan to repost with any additional info I can think to provide.

---

### Post by sanderj on 2012-07-19
I would try the **server** version of Ubuntu; just a text install, so I expect no resolution problems.

And if the 10.04 and 8.04 version do not work, I would also try the  12.04 Server version; maybe it has more hardware recognition.

If a server versions works, you can install the graphical stuff afterwards and see how that behaves.

---

### Post by mastablasta on 2012-07-19
instead of installign a whole server (since you are low on ram) you should use ubuntu mimimal iso. have a look here for a howto.: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
also if you go 12.04, but graphics then use Lubuntu (will probably need alternate CD). Lubuntu kernel is more suited for older mashcines (also regarding default kernel choice)
what video chip is it? also try 10.04 as it has older kernel. remember in linux drivers are built into kernel.
 
older verisons (someitmes) needed x-org.conf file to be configured manually. new versions do not have this issue.
 
edit: forgot to add that Slitaz is very interesting distribution for old mashcines.

---

### Post by sanderj on 2012-07-19
> **mastablasta said:**
> instead of installign a whole server (since you are low on ram) you should use ubuntu mimimal iso. 

The requirements for Ubuntu server are only 128MB RAM (see [https://help.ubuntu.com/12.04/serverguide/preparing-to-install.html](https://help.ubuntu.com/12.04/serverguide/preparing-to-install.html) ), so that shouldn't be a problem for the OP.

Anyway: Based on your post, I tried Ubuntu Minimal ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) in a virtual machine:
- wow: only 28MB iso download
- "install on demand" / a la carte: nice
- character / ncurses user interface, so never GUI / X problems during install ;-)
- install looks a bit more difficult than Desktop install. I don't know the Server install. 
- I got a few error messages that packages could not be downloaded. Strange; my Internet connection is working well

I'm not sure what I find best for the OP.
- Advantage of Server install: everything on CD, no dependency on Internet connection
- Advantage of Minimal install: small iso image to download

The Server install seems a bit safer to me as we don't if the OP's ethernet/internet connection is working.

---

### Post by darkod on 2012-07-19
So, have you tried the LinuxCNC images? On their website it looks like there are separate images. They are based on ubuntu, but you don't install ubuntu server separately, you only install the LinuxCNC cd.
That might be more optimized for low ram situations, because with only 256MB of ram I am not even sure ubuntu server can run, or how fast.
[http://www.linuxcnc.org/index.php/english/download](http://www.linuxcnc.org/index.php/english/download)

---

### Post by gallinka on 2012-07-19
I will try the minimal, text-based install.  I was thinking down that direction anyway.  As far as the version is concerned, it has to be Ubuntu 8.04 or bust.  Certain versions of LinuxCNX only work with certain versions of Ubuntu (I could try 6.04 but I want to exhaust the possibilities with 8.04).  I will try within the next day or so and re-post my results (maybe try 12.04 but I do not meet the minimum requirements and 12.04 won't ultimately help me).  One more question though.  I will certainly need X server and a desktop manager.  Will I run into any problems installing them on a minimal install of Ubuntu? (That is assuming I get networking up which should not be a problem.)

My hope is that I can get some version of LinuxCNC up and running and have that information available to others.  The computer, although old, is very well suited for that purpose (small, compact, intergrated LCD/touch interface).  I think the computer is an Axiomtek P2125-370 (I am not sure as the model number was written on the back)  The p2127 has an integrated CD-ROM in the housing, mine does not.  My only other option is to source a different SBC that will fit in the case (there are a few, expensive, options) but that will wait until I can allocate some funds for that purpose.

---

### Post by sanderj on 2012-07-19
Why ask, and not try? Run Ubuntu Minimal in a VirtualBox, and see what you can do. It will take 15 minutes, and will give you experience.

---

### Post by gallinka on 2012-07-19
That's is a helpful suggestion.  I will do that on my regular desktop this weekend (better specs).  I have been itching to get something other than XP on it anyway.  The last time I tried a text-only install (FreeBSD on a laptop) I never got the gui (X also, ver 4 I believe) to install/work.  This will give me some much needed experience on Linux I will need if I am to ever completely dump MS.

---

### Post by darkod on 2012-07-19
In case you missed it between other posts, just to remind you of my post #5. LinuxCNC website has a download image for the complete setup. It installs together ubuntu 8.04 (or 10.04 depending on the version) and LinuxCNC, so you don't have to install it later.

I would suggest to try their CDs first, and only if it doesn't work consider installing ubuntu 8.04 first and try adding LinuxCNC on it.

Otherwise, if their CD works, why bother and wasting time?

---

### Post by gallinka on 2012-07-21
A quick update:

     Unfortunately, I still am having problems with install.  I have tried both the server ISO and the minimal install (i386 version).  Same symptoms - blank screen/out of range/sync.  I did see the last message in full that I metioned above: "...Freeing up initrd(?) memory: 7157K"  (not sure if it was initrd or in???msg, 71xxk - exact number probably not important).  Tried "nomodeset", "acpi=off", "vga=771" on the server install boot parameters.  Tried "cli" (command line interface) option on minimal install.
     So, I can think of only two options going forward.  Try different RAM (or CPU, I should have one that is compatible).  The Ram is a 1BG ECC stick recognized as 256MB.  The other option is to use a different video card (I do have a PCI one with 32 MB vram kicking around).  I can't imagine why either of those could be my problem but stranger things have happned.  I will try these and anything else I can think of in the next day or two.
     Again, I appreciate all of your thoughts and suggestions.  "Darkod", to answer your question I originally burned/used the 8.04/LinuxCNC 2.3 install CD from LinuxCNC.com's web site.  I have been trying to get more and more basic and then work more into the install.  One other thought that just came to mind.  I have no valid OS on this computer.  I have never tried to install anything but Ubuntu.  I may try Win98 (I like and miss 98) and see where that gets me.  If this is a defective hardware issue I will never get very far with Ubuntu.   I have two of these computers (given to me from my employer out of the junk/free pile) and can also try the other one (they are identical).  Maybe it is just the one having probelems.

I will be back soon.  Sorry this took so long, I work two jobs, have no internet at my home and could not find my spindle of blank CD's.

---

### Post by sanderj on 2012-07-21
I don't think the memory is the problem if the screen just goes out-of-sync. As a test, you could run memtest86 (it's in the Ubuntu boot menu)

You could try another video card. I think you have to say in the BIOS "use the other video card". However, I'm not sure.
Just checking: there is no VGA-adapter for an external monitor somewhere on the computer?

Another thing I've done a few time with unwilling systems:

Take the harddisk out, put it in another computer (as the only harddisk), on that other computer install Linux to the harddisk, make sure it all works, and then put the harddisk back into the orginal machine

---

### Post by gallinka on 2012-07-25
Update to come soon (conclusion?),

I have finally had time to try some of suggestions and thoughts I came up with.  Not completely installed yet but close.  A video card got me around the video problem.  Still halted in the install with all the different flavors of 8.04 except the LinuxCNC/Ubuntu Live CD.  Of course this is the one the CD-ROM I am using has trouble reading.  I just burned a new one at 8x and will try it when I get home.  I have yet to resolve the video problem, one thing at a time though.  I will post within the next day of my progress, wish me luck...

PS - Any thoughts on why the install would stop after USB detection/kernel driver load?  That is where the other (desktop, server minimal) stopped at.  May not be related to USB.  Found it strange that the Image/CD from linuxcnc.org (Ubuntu 8.04/ LinuxCNC 2.3) did not have this problem (got to desktop/gui).

---

### Post by gallinka on 2012-08-04
Conclusion (sort of):

So, I did finally get Ubuntu 8.04 to install.  I used the live CD provided a LinuxCNC.org but I had to re burn it at 8x and use a different CD-ROM drive.  The CD-ROM drive I was using can burn CDs but I burned the CD from a DVD-ROM drive and I think it was just too old to read the CD reliably.  Ubuntu works fine and X is great off the 3dfx card I used.  Got online, firefox worked right out of the box.  After playing with the xorg.conf file I got the touchscreen to work also.

That is were the fun ends though.  Lots of problems with video modes.  I cannot display anything above 800x600 on my big LCD monitor.  The built in LCD on the computer does not display anything.  After much reading. editing (the xorg.conf file) and restarting I am still nowhere with the video problems.  I am going to close this thread and start a new one as I got past the install problem and have narrowed down the issue.

Thank everyone for their help.  I will post a link to the new thread.

---

### Post by gallinka on 2012-08-04
Here is the link:  [http://ubuntuforums.org/showthread.php?t=2037302](http://ubuntuforums.org/showthread.php?t=2037302)

---

