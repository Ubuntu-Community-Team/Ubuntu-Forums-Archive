---
title: "have you got a really old computer"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by sudodus on 2014-03-06
We want to try a new 'community' kernel for Trusty Tahr. Many people help to build an Ubuntu based operating system around it, a system that should work on most computers (maybe except some of those brand new ones that cannot switch off UEFI).

We have a wide variety of computers, but have not found any really old one without PAE capability. I'm not talking about Pentium M and Celeron M, [s]I'm talking about CPUs before Pentium II:

Pentium Pro, Pentium (i586), or Intel 486 or maybe the corresponding generation of AMD from 1993-1997.

I have an old computer from 1998, and it has a Pentium II CPU at 400 MHz, so it must be older. Check for a clock frequency at or below 200 MHz.[/s]

If you are a happy owner of such a jewel, please help us test that the non-pae kernel really works in a computer without PAE capability.

-o-

***Edit 1***: After testing for a couple of weeks we have found that pre-pentium computers are not really an alternative for Trusty. We have also found, that Trusty needs more RAM to be installed via the conventional installers. Even the Ubuntu ***mini.iso ***will have problems at 128 MB RAM, trying to install a basic server.

I think there are many computers around with 'more powerful' CPUs  (for example Pentium III, some old Celerons, and corresponding AMD CPUs), but only 128 GB RAM. It is worthwhile to try installing  Lubuntu Core Trusty or the plain text version of Trusty in such computers using ***9w***.

-o-

***Edit 2***: There is a new wiki page for the ***9w*** installer can install systems with 80 MB RAM to install and run the Ubuntu mini.iso based text system.
[B]
Lubuntu Core Trusty[/B] needs 128 MB RAM to run and at least 256 MB RAM to be really useful. 

See this wiki page [https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w) 

and this page, where you can download the 9w iso files [http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)


Examples of non-pae CPUs

1. ***Early Pentium M with 1.2 GHz*** clock frequency. (The later Pentium M CPUs have PAE capability even if they lack a PAE flag).
2. ***Old ViA-processors around 1GHz***
3. ***Transmeta Crusoe***
(4. Pre Pentium II CPUs are too old and weak to be tested for this purpose)

You can test for the PAE flag with the following command

```
grep --color pae /proc/cpuinfo
```

If you are a happy owner of such a jewel, please help us test that the  non-pae kernel really works in a computer without PAE capability.

---

### Post by Doug S on 2014-03-07
I have an old computer that I use for minimum requirements testing for Ubuntu server edition. Currently, it is running the development 14.04 server edition. The CPU is a Pentium Pro at 200 Mhz. It has 128 Megabytes of memory. The computer was purchased on 1996.08.31. I'll PM you a link to its hardware profile (the OS part of that link is a bit outdated).

Edit: Sorry, I think my old Pentium pro is PAE capable. I have an even older 486 50Mhz in the closest that I could have a look at. I do not recall how much memory it has. The current OS is Red Hat linux about version 5.

---

### Post by ventrical on 2014-03-07
Lots of olde stuff here, Where is it? The kernel.

---

### Post by sudodus on 2014-03-07
> **Doug S said:**
> I have an old computer that I use for minimum requirements testing for Ubuntu server edition. Currently, it is running the development 14.04 server edition. The CPU is a Pentium Pro at 200 Mhz. It has 128 Megabytes of memory. The computer was purchased on 1996.08.31. I'll PM you a link to its hardware profile (the OS part of that link is a bit outdated).

Edit: Sorry, I think my old Pentium pro is PAE capable. I have an even older 486 50Mhz in the closest that I could have a look at. I do not recall how much memory it has. The current OS is Red Hat linux about version 5.

I am testing the installer now, but have not uploaded anything yet. Maybe I can upload an iso file during the weekend.

The installer itself, with a Debian i486 kernel, uses 18-22 MB RAM idling with only a text screen (before starting X). And the Ubuntu based kernel will need more RAM.

I think the current version would be able to install with 64 MB staying in text mode (with the Debian kernel), but I think 80 MB is the bottom level of RAM in a serious test for a Trusty kernel (so in practical life, 96-128 MB RAM).

The installation is done with **mkusb** (which comes with the iso file), a special method, that uses very little memory. It will be interesting to see if

- it boots at all from the CD with the Debian installer (or maybe chainloads from Plop on a floppy to the CD)
- you can install the image
- it boots with the installed Lubuntu
- the graphics work, or if you can only run the computer in text mode.

-o-

You can prepare reading these links and the attached file kappa.zip, which contains the newest version of

- the scrip **mkusb** and the manuals **mkUSB-quick-start-manual.pdf** and **GrowIt.pdf**
- md5sum: ```
2b8797d4af041ea8b3fc74  kappa.zip
```

[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

Best regards
Nio

---

### Post by sudodus on 2014-03-07
> **ventrical said:**
> Lots of olde stuff here, Where is it? The kernel.

I hope to be able to upload an iso file with it during the week-end. I want to test it more before uploading it, so that I know that it works for me :-)

---

### Post by pqwoerituytrueiwoq on 2014-03-08
i have a old box
[http://reviews.cnet.com/desktops/hp-pavilion-6640c-k6/4505-3118_7-31099901.html](http://reviews.cnet.com/desktops/hp-pavilion-6640c-k6/4505-3118_7-31099901.html)
please don't ask me to install to that thing, it is god awful slow, and i have never had working sound in linux on that box the couple times i have tried
if you give a grub 2 boot entry and a iso file i will try it

---

### Post by sudodus on 2014-03-08
> **pqwoerituytrueiwoq said:**
> i have a old box
[http://reviews.cnet.com/desktops/hp-pavilion-6640c-k6/4505-3118_7-31099901.html](http://reviews.cnet.com/desktops/hp-pavilion-6640c-k6/4505-3118_7-31099901.html)
please don't ask me to install to that thing, it is god awful slow, and i have never had working sound in linux on that box the couple times i have tried
if you give a grub 2 boot entry and a iso file i will try it

This will be interesting :-)

The iso file, that I intend to upload contains 'everything needed' to flash an installed system (which will be booting from grub).

***mkusb*** and a compressed image file.

64 MB RAM seems to be the minimum specified. How much memory is there in your HP Pavilion 6640C?

If only the mininum RAM the installer will probably run, but I don't know about the Trusty system with a non-pae kernel. It is close to the limit. Depending on the drivers activated (and how much memory they need), it just might boot into text mode. If you have 96 MB RAM or more, the memory will not be a bottleneck, at least not in text mode, but there might be other issues, for example the graphics.

In that case, remove the boot options [FONT=courier new]**quiet splash**[/FONT] and add **[FONT=courier new]text[/FONT]** (and maybe **[FONT=courier new]nomodeset[/FONT]**)

---

### Post by sudodus on 2014-03-08
[SIZE=4]9w - an installer for old computers[/SIZE]

So I uploaded a directory with an experimental installer and two sample systems to install. The installer is based on a Debian system with an i486 kernel, and it can install any kind of [free] operating system. There are two sample systems which expand to 4 GB

***Lubuntu Trusty non-pae built february 23*** -  '[SIZE=3]**[FONT=courier new]Ltrusty-npae-feb23.iso[/FONT]**[/SIZE]'

***Lubuntu Saucy PAE-for-Pentium-M***  - '[SIZE=3][FONT=courier new]**LubuSaucy-pae2pm-4GB.iso**[/FONT][/SIZE]'

***9w*** comes as a hybrid ISO file, that works from CD/DVD and cloned from USB. So it is simple to make install media for most old computers.

See this link

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

---

### Post by ventrical on 2014-03-08
I brought out my old NEC Ready 9710 with Pentium MMX 166MHz 32bit virtual/physical.  I had to test the PLOP floppy disk and it works just great. Had to find a compatible CD-ROM (as those were one of the First PCs that would set-up to boot from CMOS) and I have the original CD ROM unit working! 

  It has only 80MBs of RAM so I further tested the Grub Rescue "live" CD (which is LDXE circa 2011) and it booted  -and is running- just beautifully , however .. very slow load up time.

  I am going to try a few more experiments and then perhaps try your method(s) but I want to see if I can actually install trusty Lubuntu to a hard drive from a CD or at least mini.

Regards.

[http://www.youtube.com/watch?v=t8lfK0HwMts&feature=youtu.be](http://www.youtube.com/watch?v=t8lfK0HwMts&feature=youtu.be)

---

### Post by sgage on 2014-03-08
I have a ca. 1997 Micron computer with a 200 MHz Pentium MMX. It ran RedHat 5.0 just fine - my first experience with Linux.

If that ain't old enough, I also have a ca. 1992 Zeos 486DX2-66 at a whopping 66 MHz. It only has 32 MB of RAM, though, and anyway, I can't seem to find the hand-crank to start 'er up ;-)

All my other old computers are 16-bit, or indeed, 8-bit. I should start a museum...

[edit: I did a bit of research, and the Pentium MMX did NOT have PAE, so perhaps I'll give your kernel a try...]

---

### Post by sudodus on 2014-03-08
> **ventrical said:**
> I brought out my old NEC Ready 9710 with Pentium MMX 166MHz 32bit virtual/physical.  I had to test the PLOP floppy disk and it works just great. Had to find a compatible CD-ROM (as those were one of the First PCs that would set-up to boot from CMOS) and I have the original CD ROM unit working! 

  It has only 80MBs of RAM so I further tested the Grub Rescue "live" CD (which is LDXE circa 2011) and it booted  -and is running- just beautifully , however .. very slow load up time.

  I am going to try a few more experiments and then perhaps try your method(s) but I want to see if I can actually install trusty Lubuntu to a hard drive from a CD or at least mini.

Regards.

[http://www.youtube.com/watch?v=t8lfK0HwMts&feature=youtu.be](http://www.youtube.com/watch?v=t8lfK0HwMts&feature=youtu.be)

It should work at least with a text screen with Lubuntu Trusty (it did for me with the non-pae kernel and 80 MB, but not with 64 MB). That was after I installed it with 9w. I'm afraid the mini.iso 'alternate installer' needs more RAM, maybe as much as the double.

See this link [https://help.ubuntu.com/community/Lubuntu/LowRamTesting](https://help.ubuntu.com/community/Lubuntu/LowRamTesting)

---

### Post by ventrical on 2014-03-08
> **sgage said:**
> I have a ca. 1997 Micron computer with a 200 MHz Pentium MMX. It ran RedHat 5.0 just fine - my first experience with Linux.

If that ain't old enough, I also have a ca. 1992 Zeos 486DX2-66 at a whopping 66 MHz. It only has 32 MB of RAM, though, and anyway, I can't seem to find the hand-crank to start 'er up ;-)

All my other old computers are 16-bit, or indeed, 8-bit. I should start a museum...

I got an Amiga 500, Baby XT and a Nintendo "Duck Shooter"  thingy in the basement. Those guns still work (optical recognition) lol

@sudodus

Downloading ltrusty-npae now.

Of course with those other kernels I got:

cmov

 and of course they would not boot.

I'll keep you apprised.

Regards..

---

### Post by sgage on 2014-03-08
> **ventrical said:**
> I got an Amiga 500, Baby XT and a Nintendo "Duck Shooter"  thingy in the basement. Those guns still work (optical recognition) lol

@sudodus

Downloading ltrusty-npae now.

Of course with those other kernels I got:

cmov

 and of course they would not boot.

I'll keep you apprised.

Regards..

And I've got a 1978 Commodore PET (6502), an original Osborne 1 (Z-80) from 1981, and a Zenith SuperSport "laptop" (8088) from 1988 I think). When I think about all the learning I did on those old machines, I understand what a great foundation in software and hardware it gave me. Heck, I ran a FidoNet point on the SS for several years, until the IntarWebtubez came along in a big way :-)

---

### Post by sudodus on 2014-03-08
> **sgage said:**
> I have a ca. 1997 Micron computer with a 200 MHz Pentium MMX. It ran RedHat 5.0 just fine - my first experience with Linux.

If that ain't old enough, I also have a ca. 1992 Zeos 486DX2-66 at a whopping 66 MHz. It only has 32 MB of RAM, though, and anyway, I can't seem to find the hand-crank to start 'er up ;-)

All my other old computers are 16-bit, or indeed, 8-bit. I should start a museum...

[edit: I did a bit of research, and the Pentium MMX did NOT have PAE, so perhaps I'll give your kernel a try...]

I think your *1997 Micron computer with a 200 MHz Pentium MMX* would be very interesting, particularly if it has at least 64 MB RAM :-)

Otherwise the Debian installer might work, but not Ubuntu Trusty non-pae, not even in text mode.

---

### Post by sgage on 2014-03-08
> **sudodus said:**
> I think your *1997 Micron computer with a 200 MHz Pentium MMX* would be very interesting, particularly if it has at least 64 MB RAM :-)

Otherwise the Debian installer might work, but not Ubuntu Trusty non-pae, not even in text mode.

I have 64 MB RAM in the thing, so I'll give it a try when I get a chance to blow the dust off it and set it up...

---

### Post by ventrical on 2014-03-08
> **sgage said:**
> And I've got a 1978 Commodore PET (6502), an original Osborne 1 (Z-80) from 1981, and a Zenith SuperSport "laptop" (8088) from 1988 I think). When I think about all the learning I did on those old machines, I understand what a great foundation in software and hardware it gave me. Heck, I ran a FidoNet point on the SS for several years, until the IntarWebtubez came along in a big way :-)

Ran my own Telix and WWIV BBSes. FIDO was a laugh. Quite a few thousand beans I v'e left there:) You don't want to know:)lol  Some of those beans were with FIDO_Linux echos. The sysop of the local FIDO point  pointed me to try and help some guy by the name of Linus Torvalds who was trying to build his own system. So I logged on there for a while.. that was during the time when he didn't even have a bootable floppy yet:) lol .. Of course there was UNIVAX and before that , in 1963, the IBM punchcard computers at Norfolk&Western Railways (I wasn't even a teenager yet) :)lol .. ohhh .. the good olde days. I'm still modding to this day ...

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> It should work at least with a text screen with Lubuntu Trusty (it did for me with the non-pae kernel and 80 MB, but not with 64 MB). That was after I installed it with 9w. I'm afraid the mini.iso 'alternate installer' needs more RAM, maybe as much as the double.

See this link [https://help.ubuntu.com/community/Lubuntu/LowRamTesting](https://help.ubuntu.com/community/Lubuntu/LowRamTesting)

  I got the full graphical LDXE screen after typing in 'startx'. All is (was) working until I tried to use iceweasle internet browser and now  the CD rom light and the hdd light are just reading/writing? on and on .. and I have no idea what it is doing. No harm here . Tons of hdds and old stuff. I am going to disconenct the hdd and try to reboot back the live session and try iceweasle again..

Regards..

---

### Post by sudodus on 2014-03-08
> **ventrical said:**
> Ran my own Telix and WWIV BBSes. FIDO was a laugh. Quite a few thousand beans I v'e left there:) You don't want to know:)lol  Some of those beans were with FIDO_Linux echos. The sysop of the local FIDO point  pointed me to try and help some guy by the name of Linus Torvalds who was trying to build his own system. So I logged on there for a while.. that was during the time when he didn't even have a bootable floppy yet:) lol .. Of course there was UNIVAX and before that , in 1963, the IBM punchcard computers at Norfolk&Western Railways (I wasn't even a teenager yet) :)lol .. ohhh .. the good olde days. I'm still modding to this day ...

Nice memory about Linus :-)

from [Anybody miss Windows 98 ?]("http://ubuntuforums.org/showthread.php?t=2206896")

> **sudodus said:**
> I grew up with the command line (punched cards,  punched tape, teletype terminals, 'dumb' text terminals) and I was  around when the first IBM compatible computers appeared. I did not think  Windows was stable until NT and not really nice until XP. But Windows  95 was a big step forward from the previous versions and 98 was even  better, nice with USB, but not really stable.

I was also learning UNIX long time ago, so it was not too difficult to convert to linux.

But I can [multi]boot Windows 98 in an old IBM Thinkcentre for old PC  games, some of which do not work in newer operating systems :wink:

> **sudodus said:**
> The punched cards were used when I learned Algol  (a programming language similar to C) at college. It did not make me  happy, I hated the long waiting time between each attempt to run between  the debugging sessions :razz:

Punched cards had 80 positions. Each card represented a text line with  max 80 characters (of programming code or input data) and they were  stacked in card readers.

---

### Post by sudodus on 2014-03-08
Great that you are running the installer in graphic mode (LXDE) :-D

I'm afraid ***iceweasle*** needs more RAM than what is available. But

- can you install?

```
mkusb /path/filename.img.xz
```

- can you edit partitions with ***gparted***?

- can you read the pdf files?

- can you install some utitilty for example ***scrot*** (and take screenshots)?

```
apt-get install scrot
```

Edit: ***htop*** is installed. Can you run it in a window and check the CPU and RAM usage while doing other tasks? Or is it too close to the limit?

And I think you can *at least install in text mode* (using the command line with mkusb, that is prompted).

---

### Post by pqwoerituytrueiwoq on 2014-03-08
> **sudodus said:**
> This will be interesting :-)

The iso file, that I intend to upload contains 'everything needed' to flash an installed system (which will be booting from grub).

***mkusb*** and a compressed image file.

64 MB RAM seems to be the minimum specified. How much memory is there in your HP Pavilion 6640C?

If only the mininum RAM the installer will probably run, but I don't know about the Trusty system with a non-pae kernel. It is close to the limit. Depending on the drivers activated (and how much memory they need), it just might boot into text mode. If you have 96 MB RAM or more, the memory will not be a bottleneck, at least not in text mode, but there might be other issues, for example the graphics.

In that case, remove the boot options [FONT=courier new]**quiet splash**[/FONT] and add **[FONT=courier new]text[/FONT]** (and maybe **[FONT=courier new]nomodeset[/FONT]**)
will it run a live session?
it will run puppy linux so it has enough ram, it is 128 or 256

---

### Post by sudodus on 2014-03-08
Yes, the debian installer runs a live session off a CD/DVD/USB drive made from one of the iso files. A standard live session, quite similar to the corresponding Ubuntu installers but very light-weight.

First a text screen, and you can ***startx*** and get LXDE with 128 MB (if there is a suitable graphics driver).

After installing (with ***mkusb***) either from text screen or a terminal window, you can reboot into the installed system. Or you can start ***gparted*** and try growing the installed partition and file system from ~4 GB to fill the HDD.

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> Great that you are running the installer in graphic mode (LXDE) :-D

I'm afraid ***iceweasle*** needs more RAM than what is available. But

- can you install?

```
mkusb /path/filename.img.xz
```

- can you edit partitions with ***gparted***?

- can you read the pdf files?

- can you install some utitilty for example ***scrot*** (and take screenshots)?

```
apt-get install scrot
```

Edit: ***htop*** is installed. Can you run it in a window and check the CPU and RAM usage while doing other tasks? Or is it too close to the limit?

And I think you can *at least install in text mode* (using the command line with mkusb, that is prompted).


1. I can read the PDF files no problem.
2. All terminals open with bash#
3. sudo chmod ugo+x mkusb will not work in the Bourne Shell as it does not regognize 'sudo'
4. CPU usage indicator works well.
5. Menus/GUI/pull downs works well/.
6. Windows placement /drag/drop/min/max work well.

 Have not tried install - do now.

 Have not downloaded 'scrot' do now.
7.edit: Write error: no space left on device (locked up).


 Have not ran htop, will do now.

---

### Post by sudodus on 2014-03-08
> **ventrical said:**
> 1. I can read the PDF files no problem.
2. All terminals open with bash#
3. sudo chmod ugo+x mkusb will not work in the Bourne Shell as it does not regognize 'sudo'

You are root, so you need no sudo. Run
```
mkusb /path/filename.img.xz
```
> 
4. CPU usage indicator works well.
5. Menus/GUI/pull downs works well/.
6. Windows placement /drag/drop/min/max work well.

 Have not tried install - do now.
 Have not downloaded 'scrot' do now.
 Have not ran htop, will do now.

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> You are root, so you need no sudo. Run
```
mkusb /path/filename.img.xz
```

what  /path/ ... what /filename/ ... keeps asking.

 I have a 30GB hdd that I want to install it on. Any suggestions? I'll read up some more.

---

### Post by sudodus on 2014-03-08
These are quirks, because the system is in a very early stage (pre-alpha) :-)

When you launch a terminal window, the whole command line is prompted. You can mark and paste it to run :-)

---

### Post by sudodus on 2014-03-08
And I think the 30 GB drive will be found, when you 'toggle USB' with u (should also be polished away in a future version). It is very valuable, that someone else (alias *you*) tries it and asks questions that I am 'too close' to see :-)

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> These are quirks, because the system is in a very early stage (pre-alpha) :-)

When you launch a terminal window, the whole command line is prompted. You can mark and paste it to run :-)

Ahhhhh :) .... long day here ...

Here are some pics so far: Gparted worked great , formatted a partition. Also htop worked great.

---

### Post by sudodus on 2014-03-08
Great to see that the installer works for you in LXDE with 80 MB RAM, and that the graphics driver works :-)

I just made some screenshots after installing scrot (that dumps the screenshots in the home folder (/root in this case). See the attachments

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> And I think the 30 GB drive will be found, when you 'toggle USB' with u (should also be polished away in a future version). It is very valuable, that someone else (alias *you*) tries it and asks questions that I am 'too close' to see :-)


Yep .. thats it .. it is installing now. I'll get back a little later. It is a little confusing , the langauge that is as it  presumes that the 'u' may toggle USB to fix, but , then the other dialog comes up for to install image to hdd, but one would not expect this (uless the manuals had been thuroughly read :)lol

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> Great to see that the installer works for you in LXDE with 80 MB RAM, and that the graphics driver works :-)



Just awesome really .. on such an old beast of a machine, But that NEC machine had an option in the BIOS to disable DOS and enable UNIX .. so maybe that was a helper for sure :)

Regards..

---

### Post by sudodus on 2014-03-08
> **ventrical said:**
> Yep .. thats it .. it is installing now. I'll get back a little later. It is a little confusing , the langauge that is as it  presumes that the 'u' may toggle USB to fix, but , then the other dialog comes up for to install image to hdd, but one would not expect this (uless the manuals had been thuroughly read :)lol

Yes, I admit that in this case USB is not the main target, so toggle USB could be removed in a special version of mkusb for 9w.

> **ventrical said:**
> Just awesome really .. on such an old beast of a machine, But that NEC machine had an option in the BIOS to disable DOS and enable UNIX .. so maybe that was a helper for sure :)

Regards..

Yes, the machine is doing quite well considering the age and low specs. I bet it was a monster computer once upon a time :-)

BTW, I uploaded 2 more screenshots to the previous post, which might help the next guy to try.

And after installation, we'll see if Trusty is as successful as the installer. I think it should *at least* run in text mode.

*Edit* - just a reminder of the specs: NEC Ready 9710 with Pentium MMX 166MHz 32bit virtual/physical, and 80 GB RAM.

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> Yes, I admit that in this case USB is not the main target, so toggle USB could be removed in a special version of mkusb for 9w.



Yes, the machine is doing quite well considering the age and low specs. I bet it was a monster computer once upon a time :-)

BTW, I uploaded 2 more screenshots to the previous post, which might help the next guy to try.

And after installation, we'll see if Trusty is as successful as the installer. I think it should *at least* run in text mode.

*Edit* - just a reminder of the specs: NEC Ready 9710 with Pentium MMX 166MHz 32bit virtual/physical, and 80 GB RAM.

Yes.

 I may need some extra help. During the process of installation it (the installer) more or less took over the whole drive and proceeded to format it. There were two other partitions on it. One was a swap partition. I am assuming that is gone now. So then I will have to use Gparted to make a swap partition?

---

### Post by sudodus on 2014-03-08
... and in a more polished version, there should be a desktop icon that starts the installation (so that you need not mark and paste to get mkusb running).

What do you think of running as root?

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> Yes, I admit that in this case USB is not the main target, so toggle USB could be removed in a special version of mkusb for 9w.



Yes, the machine is doing quite well considering the age and low specs. I bet it was a monster computer once upon a time :-)


 It had the unique ability to be able to clone drives effectively. I used it for the sole purpose of cloning an install of WinXP, to keep one copy always pure. No other PC I had at the time could do it effectively.

 So now it looks like it is back to work on another mission. :)

---

### Post by sudodus on 2014-03-08
> **ventrical said:**
> Yes.

 I may need some extra help. During the process of installation it (the installer) more or less took over the whole drive and proceeded to format it. There were two other partitions on it. One was a swap partition. I am assuming that is gone now. So then I will have to use Gparted to make a swap partition?

The installer is simply cloning a portable installed system (similar to flashing a system to a mobile phone). So it will clone a system using 4 GB disk space with a root partition and a swap partition. If the installer starts to format it explicitly, something is wrong. It should simply clone alias flash with dd under the hood of the mkusb shell-script.

After that, you can move the swap partition to the end of the drive and grow the root partiiton. See the pdf-file describing it ***GrowIt.pdf***

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> The installer is simply cloning a portable installed system (similar to flashing a system to a mobile phone). So it will clone a system using 4 GB disk space with a root partition and a swap partition. If the installer starts to format it explicitly, something is wrong. It should simply clone alias flash with dd under the hood of the mkusb shell-script.

After that, you can move the swap partition to the end of the drive and grow the root partiiton. See the pdf-file describing it ***GrowIt.pdf***!

You are correct. But it would not boot after the install. I stuck the hdd on my USB to IDE bridge and got this:

edit:

 I think that the problem is that on that machine , the Maxtor 30GB is too big .. so I'll try with another drive tommorrow.

---

### Post by ventrical on 2014-03-08
> **sudodus said:**
> This will be interesting :-)

The iso file, that I intend to upload contains 'everything needed' to flash an installed system (which will be booting from grub).

[FONT=courier new][/FONT]**[FONT=courier new][/FONT]****[FONT=courier new][/FONT]**


Ahh .. so naturally i forgot to 

update-grub

?

---

### Post by sudodus on 2014-03-08
> **ventrical said:**
> You are correct. But it would not boot after the install. I stuck the hdd on my USB to IDE bridge and got this:

edit:

 I think that the problem is that on that machine , the Maxtor 30GB is too big .. so I'll try with another drive tommorrow.

The partition table seems OK. Did the installation - cloning - finish properly (without any error)?

Will the computer boot from that bridge? Can you connect the drive internally or boot via Plop?

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> Ahh .. so naturally i forgot to 

update-grub

?

You should not need update-grub to boot into this system, but if you boot from another drive, and want to include this drive into that drive's grub menu, yes, update-grub.

And vice versa.

-o-

And the bootloader need not be installed (so no grub-install should be necessary). This installer does not write anything to any other drive, it only [expands the compressed file and] clones to the target drive.

-o-

What happens? I mean is there any sign of life (for example any output to the screen), when you try to boot Trusty from the where it is installed?

*Edit*: Testing in my IBM Thinkpad T42 with Pentium M without a PAE flag, I reduced the available RAM with the boot option mem=80M, but I changed other boot options too.

removed boot options:
```
quiet splash
```

added boot options:
```
text mem=80M
```

This (80 MB) was the lowest RAM, that worked for me. I tried mem=64M, and it did not work, but I did not try anything between those memory specs.

---

### Post by ventrical on 2014-03-09
> **sudodus said:**
> The partition table seems OK. Did the installation - cloning - finish properly (without any error)?

Will the computer boot from that bridge? Can you connect the drive internally or boot via Plop?

There were no errors. The hdd will not boot from that bridge. I had the hdd connected during the install. It will not boot but PLOP does recognize the partitions.  I took the drive to another PC and tried to install GRuB but that will not work either.

I am going to try another hdd with EIDE cable (80) and go through the documents. There could be a hardware problem here at my end. I have also two more PI166HMZ systems in my shop . One with 128MB RAM.. so I'll be doing some swapping around. I'll keep at the original install too. I'll look over the docs again. Must be something I missed.

Regards..

---

### Post by ventrical on 2014-03-09
> **sudodus said:**
> You should not need update-grub to boot into this system, but if you boot from another drive, and want to include this drive into that drive's grub menu, yes, update-grub.

And vice versa.

-o-

And the bootloader need not be installed (so no grub-install should be necessary). This installer does not write anything to any other drive, it only [expands the compressed file and] clones to the target drive.

-o-

What happens? I mean is there any sign of life (for example any output to the screen), when you try to boot Trusty from the where it is installed?

.


Thanks for clarifiying the GRuB questions.

When I boot that NEC with the .iso installed  on it , all I get is a cursor.  I swapped the drive to another machine and it tells me BOOT DISK ERROR, Please ENTER .. etc..


 It is ... ummm 6:30 am EST (DST) here. Have to get ready for Sunday duties :) I'll be back at this soon. It looks very promising and ran quite fast from the CD so I can imagine that it is very thrifty on a real install.

Regards..

---

### Post by ventrical on 2014-03-09
> **sudodus said:**
> ... and in a more polished version, there should be a desktop icon that starts the installation (so that you need not mark and paste to get mkusb running).

What do you think of running as root?

root is just fine as an experimental.

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> There were no errors. The hdd will not boot from that bridge. I had the hdd connected during the install. It will not boot but PLOP does recognize the partitions.  I took the drive to another PC and tried to install GRuB but that will not work either.

I am going to try another hdd with EIDE cable (80) and go through the documents. There could be a hardware problem here at my end. I have also two more PI166HMZ systems in my shop . One with 128MB RAM.. so I'll be doing some swapping around. I'll keep at the original install too. I'll look over the docs again. Must be something I missed.

Regards..

I don't think you need to install grub ... I'll read the other posts too ...

---

### Post by sudodus on 2014-03-09
I suggest that you try with ***boot options*** according to post #39:

remove **quiet splash**
add **text** (I needed the mem option, you use all your RAM)

If you cannot access the grub menu (there might be a bug in that daily build of Trusty), you must do it when booted from another system, and change the file

```
/mount-point/boot/grub/grub.cfg
```

Or do it with the drive connected to a newer computer (and due to persistence and portability, the boot options should be there, when you move the drive back to the NEC.

If this is too complicated, I could make a Lubuntu Trusty non-pae system, that boots into a text screen (like the installer). That system can be tested with old systems to make sure that the kernel really works without PAE. There might be some other capability, that such old CPUs lack, who knows.

---

### Post by ventrical on 2014-03-09
> **sudodus said:**
> I suggest that you try with ***boot options*** according to post #39:

remove **quiet splash**
add **text** (I needed the mem option, you use all your RAM)

If you cannot access the grub menu (there might be a bug in that daily build of Trusty), you must do it when booted from another system, and change the file

```
/mount-point/boot/grub/grub.cfg
```

Or do it with the drive connected to a newer computer (and due to persistence and portability, the boot options should be there, when you move the drive back to the NEC.

If this is too complicated, I could make a Lubuntu Trusty non-pae system, that boots into a text screen (like the installer). That system can be tested with old systems to make sure that the kernel really works without PAE. There might be some other capability, that such old CPUs lack, who knows.

No.. not complicated at all. If fact .. that is exactly what I thought :) but you thought it first.

 Sounds like the right solution. I'll be back a little later.

---

### Post by ventrical on 2014-03-09
> **sudodus said:**
> I suggest that you try with ***boot options*** according to post #39:

remove **quiet splash**
add **text** (I needed the mem option, you use all your RAM)

If you cannot access the grub menu (there might be a bug in that daily build of Trusty), you must do it when booted from another system, and change the file

```
/mount-point/boot/grub/grub.cfg
```

Or do it with the drive connected to a newer computer (and due to persistence and portability, the boot options should be there, when you move the drive back to the NEC.

If this is too complicated, I could make a Lubuntu Trusty non-pae system, that boots into a text screen (like the installer). That system can be tested with old systems to make sure that the kernel really works without PAE. There might be some other capability, that such old CPUs lack, who knows.

Plop tells me "NO VALID BOOT SIGNATURE".

 However, my BIOS is telling me that I only have 8545MBs on a 30GBhdd so there must be something wrong with the disk size . I am going to try another hdd.

edit: I was able to edit the grub.cfg but to no avail.

---

### Post by ventrical on 2014-03-09
I put the hdd in another , more recent PC.

what is this?

```


tester-SATALLITE-PRO-C850-19w login:


```

edit :belay the above ^^^^^^^^^^^^^ and below

How do I login?

edit:; Let me know if this aspect is worth pursuing. I want to get on with another install attempt.

---

### Post by ventrical on 2014-03-09
> **ventrical said:**
> Plop tells me "NO VALID BOOT SIGNATURE".

 However, my BIOS is telling me that I only have 8545MBs on a 30GBhdd so there must be something wrong with the disk size . I am going to try another hdd.

edit: I was able to edit the grub.cfg but to no avail.

edit: Belay the above ^^^^^

---

### Post by ventrical on 2014-03-09
I am doing a fresh install using another hdd. A Western Digital 7.5 GB WD Caviar 75AA. There appears to have been a problem on my end here. I still think I can use the 30GB drive but I wanted to take a backstep first to a smaller drive.  There is a proceedure when installing hdds in BIOS and when choosing AUTO one has to  move back to setup and press enter for the new parameters to register correctly... so we will see. So far this new hdd is detecting correctly in BIOS.

so far so good ...

[http://www.youtube.com/watch?v=80_6CEK7Q5U&feature=youtu.be](http://www.youtube.com/watch?v=80_6CEK7Q5U&feature=youtu.be)

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> I put the hdd in another , more recent PC.

what is this?

```


tester-SATALLITE-PRO-C850-19w login:


```

edit :belay the above ^^^^^^^^^^^^^ and below

How do I login?

edit:; Let me know if this aspect is worth pursuing. I want to get on with another install attempt.

[I][B]user: tester
password: 123456[/B][/I]

The system was originally installed on my Toshiba SATALLITE-PRO-C850-19w with Intel i5, and now we are testing it on a machine several generations older :-)

It does work in my IBM Thinkpad T42 with Pentium M without a PAE flag.

The reason I installed in the Toshiba is that it is fast, almost no waiting, and since it it portable ...

Of course, a more polished system will not have a hostname reminding of that.

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> edit: Belay the above ^^^^^

I don't know why Plop doesn't like it. Maybe Trusty's grub is too modern for Plop to recognize it.

I have noticed that some versions of grub are better booters via USB. Grub of Ubuntu 13.04 is best so far in middle-aged HP laptops. Grub of 12.04 LTS and 13.10 do not boot (via USB, they boot from the internal drive).

---

### Post by ventrical on 2014-03-09
Could not get the WD (new install) hdd to boot.  Here are some pics that I took with my camera. I do not know why it will not boot up. I'll have to try another machine perhaps  but Win 95/98 works just fine on the NEC Ready.

Can you see where I may have done something wrong or missed a step?

---

### Post by Doug S on 2014-03-09
> **sudodus said:**
> The installation is done with **mkusb** (which comes with the iso file), a special method, that uses very little memory. It will be interesting to see if

- it boots at all from the CD with the Debian installer (or maybe chainloads from Plop on a floppy to the CD)
- you can install the image
- it boots with the installed Lubuntu
- the graphics work, or if you can only run the computer in text mode.

-o-

You can prepare reading these links and the attached file kappa.zip,I guess I am where ventrical was yesterday morning: It boots fine from the CD, and I am able to run graphically fine after entering "startx" and after remembering to find an old mouse to plug in. For ventrical's "what  /path/ ... what /filename/ ... keeps asking" part, miine told me what command to use at the end of the boot up sequence. However, it is complaing about an invalid partition table for sr0 (The CD-ROM drive). I'm confused and entered "q" a few times until I finally got out.

Edit: ventrical posted while I was typing. Seeing the pictures I tried just a what the hell "u" (even though there is no such thing as USB on the computer) and am making progress... Looks as though it is going to take about 30 minutes....

---

### Post by ventrical on 2014-03-09
> **Doug S said:**
> I guess I am where ventrical was yesterday morning: It boots fine from the CD, and I am able to run graphically fine after entering "startx" and after remembering to find an old mouse to plug in. For ventrical's "what  /path/ ... what /filename/ ... keeps asking" part, miine told me what command to use at the end of the boot up sequence. However, it is complaing about an invalid partition table for sr0 (The CD-ROM drive). I'm confused and entered "q" a few times until I finally got out.

Edit: ventrical posted while I was typing. Seeing the pictures I tried just a what the hell "u" (even though there is no such thing as USB on the computer) and am making progress... Looks as though it is going to take about 30 minutes....

  I think using the 'u' option actually toggles the USB option <off> and then goes right to hddisk.

---

### Post by ventrical on 2014-03-09
> **Doug S said:**
> 

Edit: ventrical posted while I was typing. Seeing the pictures I tried just a what the hell "u" (even though there is no such thing as USB on the computer) and am making progress... Looks as though it is going to take about 30 minutes....

My NEC Ready has two USB ports (believe it or not) version 1.1 or sumthing :)  I am going to use a Verbatim 8GB 3.0 USB and give that a whirl. But I would really like to get it working with hdds.

patience :)

@sudodus

Can I use 'mkusb' on a faster machine, ie; like the one I downloaded the iso to?

---

### Post by ventrical on 2014-03-09
> **Doug S said:**
> I guess I am where ventrical was yesterday morning: It boots fine from the CD, and I am able to run graphically fine after entering "startx" and after remembering to find an old mouse to plug in. For ventrical's "what  /path/ ... what /filename/ ... keeps asking" part, miine told me what command to use at the end of the boot up sequence. However, it is complaing about an invalid partition table for sr0 (The CD-ROM drive). I'm confused and entered "q" a few times until I finally.


I just close that window at the top-left and then proceed. I am currently trying the <Install to USB> method .. but looks like it will take a while on that old beater NEC :)lol

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> Could not get the WD (new install) hdd to boot.  Here are some pics that I took with my camera. I do not know why it will not boot up. I'll have to try another machine perhaps  but Win 95/98 works just fine on the NEC Ready.

And Ubuntu's mother Debian works well :-/
> 
Can you see where I may have done something wrong or missed a step?

You have copied all 4 GB (I recognize the exact number in bytes too), so I think you have cloned the whole system into the drive.

Did you continue at the text screen? with user=tester and password=123456 (Was it in a newer computer?)

I do not know what is the problem, but I can guess:

- Too low RAM for the boot process
- Some hardware that is not recognized: graphics card, ethernet card ... maybe even some capability of the CPU is missing

- Maybe you can try the boot option **nomodeset** (together with **text**)

---

### Post by Doug S on 2014-03-09
Seems to be working fine for me. I couldn't get the CD-ROM drive to release the CD, but did manage to do it during the re-boot cycle. It booted from hard disk just fine and is running, evidently, lubuntu.

This was on my Pentium pro, 200 Mhz computer. I haven't dusted off the 486-50 computer yet. It was also the LubuSaucy-pae2pm-4GB.iso
I am downloading the other iso now and will try it.

... Doug

---

### Post by sudodus on 2014-03-09
> **Doug S said:**
> I guess I am where ventrical was yesterday morning: It boots fine from the CD, and I am able to run graphically fine after entering "startx" and after remembering to find an old mouse to plug in. For ventrical's "what  /path/ ... what /filename/ ... keeps asking" part, miine told me what command to use at the end of the boot up sequence. However, it is complaing about an invalid partition table for sr0 (The CD-ROM drive). I'm confused and entered "q" a few times until I finally got out.

Edit: ventrical posted while I was typing. Seeing the pictures I tried just a what the hell "u" (even though there is no such thing as USB on the computer) and am making progress... Looks as though it is going to take about 30 minutes....

Yeah, I guess ventrical has identified some of the obstacles, that must be polished, before average users can use this installer. Anyway, if you read our conversation, I think you will catch up soon :-)

---

### Post by Doug S on 2014-03-09
> **sudodus said:**
> Did you continue at the text screen? with user=tester and password=123456 (Was it in a newer computer?)Huh? I never saw such a question. I seem to be running lubuntu fine, but have never entered a user name or password. Apparently, I am user "oem".

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> I think using the 'u' option actually toggles the USB option <off> and then goes right to hddisk.


the 'u' option actually toggles the USB-***only*** option <off/on>

It is there to make it safer for the standard usage of mkusb, to flash systems into pendrives. In other words, avoid overwriting internal drives by mistake. I have already made a second parameter 'all' that set the USB-only option <off>, so that internal drives as seen without toggling. But I have not uploaded any system with it yet. I will also make desktop icons to launch the installation directly (using that option).

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> My NEC Ready has two USB ports (believe it or not) version 1.1 or sumthing :)  I am going to use a Verbatim 8GB 3.0 USB and give that a whirl. But I would really like to get it working with hdds.

patience :)

@sudodus

Can I use 'mkusb' on a faster machine, ie; like the one I downloaded the iso to?

Sure, use it on an Intel i5 or i7 if you have one. mkusb is a simple shell-script using standard linux commands (plus pv, if you want to watch the progress).

---

### Post by ventrical on 2014-03-09
> **sudodus said:**
> the 'u' option actually toggles the USB-***only*** option <off/on>

It is there to make it safer for the standard usage of mkusb, to flash systems into pendrives. In other words, avoid overwriting internal drives by mistake. I have already made a second parameter 'all' that set the USB-only option <off>, so that internal drives as seen without toggling. But I have not uploaded any system with it yet. I will also make desktop icons to launch the installation directly (using that option).


Ok .. this is where it is not immediately clear to me.

What happens when I use the "u" option in your program <mkusb> That is to say when I copy and paste your script from terminal. Does it:

1. Initially turn off the USB option? or
2. Turn on the USB option?

The reason I ask is because if you leave it as default (don't put anything) then it will not recognize any harddrives. However , when you use the "u" option , it detects the harddrives and proceeds to install to the detected hdd (which so far have all been fails)..

---

### Post by sudodus on 2014-03-09
> **Doug S said:**
> Seems to be working fine for me. I couldn't get the CD-ROM drive to release the CD, but did manage to do it during the re-boot cycle. It booted from hard disk just fine and is running, evidently, lubuntu.

This was on my Pentium pro, 200 Mhz computer. I haven't dusted off the 486-50 computer yet. It was also the LubuSaucy-pae2pm-4GB.iso
I am downloading the other iso now and will try it.

... Doug

Great progress :KS

- How much RAM is there in that computer?
- Did you run in text mode or full graphics mode (LXDE)?
- How much RAM is used? Does it swap? (check with free -m or htop)

 -Lubuntu Saucy comes with zRAM, that helps a lot when there is low RAM. This has a PAE kernel.

- Lubuntu Trusty uses zRAM live, but not when installed. (You can configure it to use zRAM, but it is not by default). This has a non-pae kernel (the experimental one).

---

### Post by Doug S on 2014-03-09
My computer does not power off by itself. How do I know when it has halted and is ready for power off? My only other (recent) experience is via "sudo shutdown -h now" which tells me when the system has gone into a halted state. I couldn't use this method, because it wanted a password for user oem, and I don't know what the password is.
Anyway, it has been about 10 minutes, I guess I'll just turn it off.

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> Ok .. this is where it is not immediately clear to me.

What happens when I use the "u" option in your program <mkusb> That is to say when I copy and paste your script from terminal. Does it:

1. Initially turn off the USB option? or
2. Turn on the USB option?

The reason I ask is because if you leave it as default (don't put anything) then it will not recognize any harddrives. However , when you use the "u" option , it detects the harddrives and proceeds to install to the detected hdd (which so far have all been fails)..

The version that you have now (and which can be found in my tutorial thread) starts 'usb-only'. So you must toggle it to display the internal drives (and esata drives if you have such drives).

You can toggle it back and forth many times and watch what happens. It runs in text mode as well as in terminal windows, so it can be used when the graphics are not working for some reason (RAM or driver issue).

---

### Post by sudodus on 2014-03-09
Lubuntu Saucy password=changeme

---

### Post by sudodus on 2014-03-09
> **Doug S said:**
> Huh? I never saw such a question. I seem to be running lubuntu fine, but have never entered a user name or password. Apparently, I am user "oem".

Lubuntu Saucy has user=oem and password=changeme. After some tweaking you can click the desktop icon and make it ready for the end user. This one is more polished.

The experimental Lubuntu Trusty has user=tester and password=123456 (is not installed in oem mode).

---

### Post by Doug S on 2014-03-09
> **sudodus said:**
> - How much RAM is there in that computer?
- Did you run in text mode or full graphics mode (LXDE)?
- How much RAM is used? Does it swap? (check with free -m or htop)128 megabytes, but less is available to the OS. I was running graphics mode, and didn't even know I had an option to not. Memory: Total 115; Used 113; Free 2. Swap: Total 57; Used 13; Free 44.

---

### Post by sudodus on 2014-03-09
> **Doug S said:**
> 128 megabytes, but less is available to the OS. I was running graphics mode, and didn't even know I had an option to not. Memory: Total 115; Used 113; Free 2. Swap: Total 57; Used 13; Free 44.

It works with a 128 MB RAM stick which is great :-) Yes, some RAM is used for other tasks and not available (and displayed by mem).

Lubuntu cannot be installed with the standard installers (neither with the desktop installer nor with the alternate installer). I could install it with 160 MB from the mini.iso (which is similar to the alternate installer), as reported at this link

[https://help.ubuntu.com/community/Lubuntu/LowRamTesting](https://help.ubuntu.com/community/Lubuntu/LowRamTesting)

I think ventricals problems could be that 80 MB is to low RAM. Or maybe that Trusty lacks zRAM, or that some driver doesn't cooperate with the hardware.

---

### Post by sudodus on 2014-03-09
There is a better description of the Lubuntu Saucy system, that you are installing. See this link

[https://help.ubuntu.com/community/InstalledSystemFakePAE#f._Boot_and_log_in_as_guru_in_13.04_and_oem_in_13.10._The_password_is_changeme.2C](https://help.ubuntu.com/community/InstalledSystemFakePAE#f._Boot_and_log_in_as_guru_in_13.04_and_oem_in_13.10._The_password_is_changeme.2C)

---

### Post by Doug S on 2014-03-09
I am doing the trusty iso version now and will report on it later...

I started up my 486-50 box, but is just not up to this. It only has 32 megabytes of memory and the disk is only 516 megabytes.
Before today, the last time I powered it up was 2006.03.30, or 8 years ago. It seems to run just fine, but I can not recall my password.

---

### Post by sudodus on 2014-03-09
> **Doug S said:**
> I am doing the trusty iso version now and will report on it later...

I started up my 486-50 box, but is just not up to this. It only has 32 megabytes of memory and the disk is only 516 megabytes.
Before today, the last time I powered it up was 2006.03.30, or 8 years ago. It seems to run just fine, but I can not recall my password.

You are right, it can be nice to revive such an old computer, but it cannot run what we want to test now. I'm sure that we need more than 32 MB, maybe 3x32 might work. And there might be other limiting factors too. By the way, what OS is it, can you see that without logging in?

---

### Post by ventrical on 2014-03-09
> **sudodus said:**
> It works with a 128 MB RAM stick which is great :-) Yes, some RAM is used for other tasks and not available (and displayed by mem).

Lubuntu cannot be installed with the standard installers (neither with the desktop installer nor with the alternate installer). I could install it with 160 MB from the mini.iso (which is similar to the alternate installer), as reported at this link

[https://help.ubuntu.com/community/Lubuntu/LowRamTesting](https://help.ubuntu.com/community/Lubuntu/LowRamTesting)

I think ventricals problems could be that 80 MB is to low RAM. Or maybe that Trusty lacks zRAM, or that some driver doesn't cooperate with the hardware.

 That seems about it for now. The USB experiment failed also. It finished the install (after 2 hours) but it will not boot (not even on faster more recent machines). Ill keep at it.

---

### Post by Doug S on 2014-03-09
The trusty iso installation went fine, and the computer boots fine. However, I think it is pretty marginal and on the harry edge, and can easily bog down with swapping and getting not much else done. I made the mistake of trying to open another terminal window while trying to install open-ssh server with the other terminal session (which didn't work, by the way). I had to have a nap while the disk light was on constantly for a long time.

Memory: Total 115; Used 112; Free 3
Swap: Total 319; Used 39; Free 280

The 486-50 computer is running Red Hat Linux version 5.2 (Apollo) Kernel 2.0.36 on a i486.

---

### Post by sudodus on 2014-03-09
> **ventrical said:**
> That seems about it for now. The USB experiment failed also. It finished the install (after 2 hours) but it will not boot (not even on faster more recent machines). Ill keep at it.

You have really tried hard. I think we can conclude that the capability of your NEC machine is below the limit to run a modern Ubuntu based system. It might be as simple as too low RAM, but we will not know for sure.

These systems boot on faster more recent machines, so I think the installation failed for some reason. *If you want to reduce the overhead of the installation to a minimum*, use the following commands (modify the name of the compressed image file for the Trusty image)

```
[COLOR=#696969]sudo -s                                     # enter superuser prompt (if a regular user)[/COLOR]
xzcat dd-LubuSaucy-pae2pm-4GB.img.xz | dd bs=4096 of=/dev/sdx
sync                 # and wait for the command prompt (while writing to the USB drive)
[COLOR=#696969]exit                                        # exit superuser prompt[/COLOR]

```
where x is the target drive.

from [https://help.ubuntu.com/community/InstalledSystemFakePAE#e.2.2.2_and_run_the_zcat_command_line_as_superuser](https://help.ubuntu.com/community/InstalledSystemFakePAE#e.2.2.2_and_run_the_zcat_command_line_as_superuser)

---

### Post by sudodus on 2014-03-09
> **Doug S said:**
> The trusty iso installation went fine, and the computer boots fine. However, I think it is pretty marginal and on the harry edge, and can easily bog down with swapping and getting not much else done. I made the mistake of trying to open another terminal window while trying to install open-ssh server with the other terminal session (which didn't work, by the way). I had to have a nap while the disk light was on constantly for a long time.

Memory: Total 115; Used 112; Free 3
Swap: Total 319; Used 39; Free 280

The 486-50 computer is running Red Hat Linux version 5.2 (Apollo) Kernel 2.0.36 on a i486.

I think you had better luck than ventrical concerning the horsepower and memory of the testing machine. I think too, that it is very close to the low limit, where this Lubuntu Trusty with a non-pae kernel can run. I recognize the symptoms you describe: 'it can easily bog down with swapping and getting not much else done'.

If I understand correctly, Lubuntu Saucy was more vital in the same computer, not quite as close to the limit. Is that so, or am I jumping to conclusions?

---

### Post by Doug S on 2014-03-09
> **sudodus said:**
> If I understand correctly, Lubuntu Saucy was more vital in the same computer, not quite as close to the limit. Is that so, or am I jumping to conclusions?No, we can not make that conclusion. I did not try as much stuff on the Saucy computer. I did open some card game, just to see, but that's about it. On my Trusty machine I tried "sudo apt-get update" and "sudo apt-get dist-upgrade", but after over an hour and much swapping it seems to have given up. Ya, it seems update manager has crashed. I think you have two good data points from ventrical and I. Ventrical @ 166 Mhz and 80 Megabytes is not enough. Me at 200 Mhz and 115 Megabytes right on the edge, and while installation was fine, operationally probably not enough.

---

### Post by sudodus on 2014-03-09
*ventrical* and *Doug S*,

Thank you very much for helping us (the Lubuntu community) find the low limit of our current flavours of Ubuntu :KS
It's very late here in Sweden, so I'd better get some sleep now.

Best regards
sudodus alias nio-wiklund at launchpad

---

### Post by bcschmerker on 2014-03-09
Sorry I can't help you here - I once had a full-tower packing an Intel® A80503-200 and matching PCIset™, but that had been scrapped years ago (as of 2014).  I also had a Leading Edge® system built around an Intel® N80286-12 and matching chipset (mfd. for Intel Corporation by ZyMOS) on a Daewoo® mobo at one time, but that wouldn't have met minimum system requirements for LinUX.

---

### Post by ventrical on 2014-03-10
> **sudodus said:**
> You have really tried hard. I think we can conclude that the capability of your NEC machine is below the limit to run a modern Ubuntu based system. It might be as simple as too low RAM, but we will not know for sure.

These systems boot on faster more recent machines, so I think the installation failed for some reason. *If you want to reduce the overhead of the installation to a minimum*, use the following commands (modify the name of the compressed image file for the Trusty image)

```
[COLOR=#696969]sudo -s                                     # enter superuser prompt (if a regular user)[/COLOR]
xzcat dd-LubuSaucy-pae2pm-4GB.img.xz | dd bs=4096 of=/dev/sdx
sync                 # and wait for the command prompt (while writing to the USB drive)
[COLOR=#696969]exit                                        # exit superuser prompt[/COLOR]

```
where x is the target drive.

from [https://help.ubuntu.com/community/InstalledSystemFakePAE#e.2.2.2_and_run_the_zcat_command_line_as_superuser](https://help.ubuntu.com/community/InstalledSystemFakePAE#e.2.2.2_and_run_the_zcat_command_line_as_superuser)

Will try this later. Also I think I may have some RAM upgrade but will have to dig:)

---

### Post by ventrical on 2014-03-10
> **Doug S said:**
> No, we can not make that conclusion. I did not try as much stuff on the Saucy computer. I did open some card game, just to see, but that's about it. On my Trusty machine I tried "sudo apt-get update" and "sudo apt-get dist-upgrade", but after over an hour and much swapping it seems to have given up. Ya, it seems update manager has crashed. I think you have two good data points from ventrical and I. Ventrical @ 166 Mhz and 80 Megabytes is not enough. Me at 200 Mhz and 115 Megabytes right on the edge, and while installation was fine, operationally probably not enough.


Nice work Doug S.

---

### Post by sudodus on 2014-03-10
> **ventrical said:**
> Will try this later. Also I think I may have some RAM upgrade but will have to dig:)

That would be nice - to find out if it is a 'low RAM' issue or something else, maybe more fundamental, that prevents Lubuntu Trusty to work in your NEC.

Good luck digging for some more old RAM :-)

---

### Post by Doug S on 2014-03-10
Just in case we want to come back and try something, I'll keep my computer the way it is now, with the trusty version, for about a week. At some point I will do a new Ubuntu Server install from the daily as it has been a few months since I last did it, and the computer is an excellent minimum requirements (actually less than minimum) test bed.

By the way, I did play a bit more before turning it off. I tried the web browser, but it eventually crashed and the system said "not enough free memory to make a report".

---

### Post by sudodus on 2014-03-10
I'm polishing the 9w installer, but I do not plan to polish the compressed images (Lubuntu Saucy and Trusty), so I would be happy if you can try the installation procedure again, but not necessarily in an extremely old computer (we know what works, and the polishing will not change the memory usage significantly).

The changes are due to your complaints about

-the usb-toggle and the lack of easily available information about things like
- 'root user so no sudo',
- user name and login to the installed systems

plus a few things that I wanted to improve:

- There will be desktop icon(s) for the compressed image(s), 1 in CD size iso files, maybe several in larger iso files.
- and some recommended commands are high-lighted in red in the text screen and terminal window ...

---

### Post by phillw on 2014-03-10
you may also like to try with core-install, it really is lubuntu stripped to the bone (e.g. you'll have to choose a low-resource browser such as xombrero) That requires the minimal (net) install. [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by sudodus on 2014-03-12
> **phillw said:**
> you may also like to try with core-install, it really is lubuntu stripped to the bone (e.g. you'll have to choose a low-resource browser such as xombrero) That requires the minimal (net) install. [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

That's a good idea. I made such a tarball for the OBI, but it was Saucy, and I can make a new one for Trusty. So from the master installation, I can make one compressed 'dd-image' file and one OBI-tarball. And the  'dd-image' file is to be used with the installer that we test in this thread, 9w. Would you suggest that it should boot into a text screen or directly into graphics mode (LXDE)?

---

### Post by sudodus on 2014-03-15
Hi again :-)

I'm close to uploading a ***polished version of the experimental 9w installer***. And according to *phillw*'s suggestion, there are updated compressed images with his ***nonpae kernel***.


1. An ultra-light ***text*** only system made from the Ubuntu Trusty beta 1 mini.iso[FONT=courier new]**  dd_TrustyB1npae-text.img.xz**[/FONT]

This system should run with 80 MB RAM, so it should be possible to test it with a pre Pentium II CPU (that the non-pae properties really work). I hope you have time to test it *ventrical* :-)


2. A very light ***Lubuntu Core*** system made from the Ubuntu Trusty beta 1 mini.iso[FONT=courier new]** dd_TrustyB1npae-LubuCore.img.xz**[/FONT]

This system is lighter than the previous 'Ltrusty' and might run with 128 MB RAM ... I hope you have time to test it *Doug S* :-)


3. And for comparison the ***Lubuntu Saucy*** system available last time too


*. Finally a 'DVD sized' iso file with [I][B]all these three compressed images in the same installer.
[/B][/I]
This container is convenient if you want to install from a DVD or USB pendrive (but is obviously oversized for an old system which only understands CDs).

---

### Post by sudodus on 2014-03-15
The ***polished version of the experimental 9w installer*** including new compressed images is uploaded to

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

```

[COLOR=#008080]1_Help-to-run-experimental_9w-installer.txt -> README.txt[/COLOR]
1477443584 mar 15 13:45 [COLOR=#0000ff]9w_multi-install_trusty-n-saucy.iso[/COLOR]
    439461 mar  7 10:23 GrowIt.pdf
       343 mar 14 20:39 login-n-password.txt
 708837376 mar 15 13:22 [COLOR=#0000ff]LubuSaucy-pae2pm-4GB.iso[/COLOR]
       991 mar 15 14:22 md5sums.txt.asc
    101211 mar  6 17:40 mkUSB-quick-start-manual.pdf
      4421 mar 13 21:53 README.txt
 660602880 mar 15 12:44 [COLOR=#0000ff]TrustyB1npae-LubuCore.iso[/COLOR]
 530579456 mar 15 08:49 [COLOR=#0000ff]TrustyB1npae-text.iso[/COLOR]

```

---

### Post by Doug S on 2014-03-15
> **sudodus said:**
> 2. A very light ***Lubuntu Core*** system made from the Ubuntu Trusty beta 1 mini.iso [FONT=courier new]**dd_TrustyB1npae-LubuCore.img.xz**[/FONT]
This system is lighter than the previous 'Ltrusty' and might run with 128 MB RAM ... I hope you have time to test it *Doug S* :-)

*. Finally a 'DVD sized' iso file with [I][B]all these three compressed images in the same installer.
[/B][/I]This container is convenient if you want to install from a DVD or USB pendrive (but is obviously oversized for an old system which only understands CDs).O.K. downloading the "multi install" now. It will probably be sometime later tomorrow before I report back.

---

### Post by ventrical on 2014-03-15
> **sudodus said:**
> Hi again :-)

I'm close to uploading a ***polished version of the experimental 9w installer***. And according to *phillw*'s suggestion, there are updated compressed images with his ***nonpae kernel***.


1. An ultra-light ***text*** only system made from the Ubuntu Trusty beta 1 mini.iso[FONT=courier new]**dd_TrustyB1npae-text.img.xz**[/FONT]

This system should run with 80 MB RAM, so it should be possible to test it with a pre Pentium II CPU (that the non-pae properties really work). I hope you have time to test it *ventrical* :-)
[FONT=courier new][/FONT]

 I couldn't find any extra RAM  (but I know I have it- I need 2x32MB- currently 32x32x8x8=80MB).

Yes, I will test it. (with 80MB)

Regards..

---

### Post by ventrical on 2014-03-15
> **sudodus said:**
> Hi again :-)

I'm close to uploading a ***polished version of the experimental 9w installer***. And according to *phillw*'s suggestion, there are updated compressed images with his ***nonpae kernel***.


1. An ultra-light ***text*** only system made from the Ubuntu Trusty beta 1 mini.iso[FONT=courier new]**dd_TrustyB1npae-text.img.xz**[/FONT][FONT=courier new][/FONT]
This container is convenient if you want to install from a DVD or USB pendrive (but is obviously oversized for an old system which only understands CDs).

 The NEC non-pae Ready will not recognize DVD.. err.. unless I try sumthing .. :) I'll be back l8r

Can minixxx.iso be dLed by itself?

---

### Post by Doug S on 2014-03-15
> **ventrical said:**
> The NEC non-pae Ready will not recognize DVD.. err.. unless I try sumthing .. :) I'll be back l8r

Can minixxx.iso be dLed by itself?Yes, there are the 3 .iso files individually. also. so you can do a CD, if that is all you have. For my case, I checked and have a DVD reader in the old old test computer, so thought I would just get the 3 in one .iso

Edit: I think you want this one: 
530579456 mar 15 08:49 [COLOR=#0000ff]TrustyB1npae-text.iso

[/COLOR]

---

### Post by pqwoerituytrueiwoq on 2014-03-15
> **sudodus said:**
> The ***polished version of the experimental 9w installer*** including new compressed images is uploaded to

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

```

[COLOR=#008080]1_Help-to-run-experimental_9w-installer.txt -> README.txt[/COLOR]
1477443584 mar 15 13:45 [COLOR=#0000ff]9w_multi-install_trusty-n-saucy.iso[/COLOR]
    439461 mar  7 10:23 GrowIt.pdf
       343 mar 14 20:39 login-n-password.txt
 708837376 mar 15 13:22 [COLOR=#0000ff]LubuSaucy-pae2pm-4GB.iso[/COLOR]
       991 mar 15 14:22 md5sums.txt.asc
    101211 mar  6 17:40 mkUSB-quick-start-manual.pdf
      4421 mar 13 21:53 README.txt
 660602880 mar 15 12:44 [COLOR=#0000ff]TrustyB1npae-LubuCore.iso[/COLOR]
 530579456 mar 15 08:49 [COLOR=#0000ff]TrustyB1npae-text.iso[/COLOR]

```
still interested in testing that old hp i have?
it has 128 or 256 MB of ram minus the 2 or 3mb shard video ram and a awfully slow cpu
if you can get sound working on it i will be impressed, it is integrated onto a dail-up modem
which version should be tested on it?

---

### Post by sudodus on 2014-03-15
> **ventrical said:**
> I couldn't find any extra RAM  (but I know I have it- I need 2x32MB- currently 32x32x8x8=80MB).

Yes, I will test it. (with 80MB)

Regards..

Great! I'm looking forward to your result with the ultra-light ***text*** screen version ...

---

### Post by sudodus on 2014-03-15
> **Doug S said:**
> O.K. downloading the "multi install" now. It will probably be sometime later tomorrow before I report back.
Great! I'm looking forward to your result ... my own experience of the beta1 version of Lubuntu Trusty is much better than the previous version. I can update/upgrade it, and I hope can do it too (at least in text mode). Lubuntu Core runs [idle] with significantly less RAM than standard Lubuntu.

---

### Post by sudodus on 2014-03-15
> **pqwoerituytrueiwoq said:**
> still interested in testing that old hp i have?
it has 128 or 256 MB of ram minus the 2 or 3mb shard video ram and a awfully slow cpu
if you can get sound working on it i will be impressed, it is integrated onto a dail-up modem
which version should be tested on it?

You are very welcome to test it :-)

Depending if you have CD or DVD you can download the 'single installers' or the 'multi-installer'. At 128 MB I think you are close to the limit, so it is interesting with the ultra-light text screen version as well as Lubuntu Core version of Trusty Beta1.

Some rough edges are removed (in the installer as well as in Trusty), so I think the experience will be smoother now compared to one week ago.

---

### Post by sudodus on 2014-03-15
> **Doug S said:**
> Yes, there are the 3 .iso files individually. also. so you can do a CD, if that is all you have. For my case, I checked and have a DVD reader in the old old test computer, so thought I would just get the 3 in one .iso

Edit: I think you want this one: 
530579456 mar 15 08:49 [COLOR=#0000ff]TrustyB1npae-text.iso

[/COLOR]

+1

---

### Post by ventrical on 2014-03-15
> **Doug S said:**
> Yes, there are the 3 .iso files individually. also. so you can do a CD, if that is all you have. For my case, I checked and have a DVD reader in the old old test computer, so thought I would just get the 3 in one .iso

Edit: I think you want this one: 
530579456 mar 15 08:49 [COLOR=#0000ff]TrustyB1npae-text.iso

[/COLOR]


thnx ! :)

---

### Post by QDR06VV9 on 2014-03-15
> **ventrical said:**
> thnx ! :)
  Hey Vent I think I have some Old Memory just laying around.
Tell me what you want, I will see if I have it.:D

---

### Post by Doug S on 2014-03-15
> **sudodus said:**
> ... I can update/upgrade it, and I hope can do it too (at least in text mode)...Forgive my ignorance (I am mainly a server guy (which I conveniently mention when I don't know something that I really should know)), but if I am running in graphical mode, how do I drop down to text only mode? Or is it some boot option?
Before messing with my setup from last week, I thought I might try update/upgrade again in text mode.

---

### Post by ventrical on 2014-03-15
> **sudodus said:**
> Great! I'm looking forward to your result with the ultra-light ***text*** screen version ...


So far ...

1. It was very difficult to boot the .iso from CD on the NEC Ready non-pae. It booted just fine on other PCs. I went through a stack of cdrom-drives and finally it booted. This may just be a hardware problem with my machine.

2. startx gave me the 9W GUI (very impressive) :) and I used your Installer Icon to install. This time I did not have to choose the 'u' toggle .. so it is installing to the same hdd as I was using the last time and it is almost halfway done. Will have to wait and see if it boots from hdd.

Regards..

---

### Post by sudodus on 2014-03-15
1. I think that updating/upgrading in the old version 'Ltrusty' is borked somehow, so I wouldn't spend time with it.

2. Text mode in graphical Ubuntu flavours:

- You can use the boot option ***text***

- If you are running in graphics mode and do not want to reboot, you can start a text screen with the hotkey combination ***ctrl + alt + F1 ... F6*** and return to graphical desktop with ***ctrl + alt + F7***. When in text mode you can shut off the graphics with

```
sudo service lightdm stop
```
do something for example change to a proprietary graphics driver and start the graphics again with
```
sudo service lightdm start
```
```
startx
``` will often work too. I don't remember if it needs sudo.

In this case, if you want to use less RAM while updating/upgrading, it should help to shut off the graphics.

---

### Post by sudodus on 2014-03-15
> **ventrical said:**
> So far ...

1. It was very difficult to boot the .iso from CD on the NEC Ready non-pae. It booted just fine on other PCs. I went through a stack of cdrom-drives and finally it booted. This may just be a hardware problem with my machine.

2. startx gave me the 9W GUI (very impressive) :) and I used your Installer Icon to install. This time I did not have to choose the 'u' toggle .. so it is installing to the same hdd as I was using the last time and it is almost halfway done. Will have to wait and see if it boots from hdd.

Regards..

I tried to improve it to avoid the problems you had one week ago. I'm glad you noticed the difference :-) Next, it will be interesting to see how the Ubuntu mini system works.

1. Boot problems: I have not changed anything that should make it harder to boot (at least not by intention). Maybe the quality of CD disks or burning  makes a difference. Did you use the minimum burning speed?

Do I understand correctly, that 9w built on Debian Wheezy works for you with LXDE with only 80GB RAM? Or was that in another computer?

---

### Post by ventrical on 2014-03-15
> **runrickus said:**
> Hey Vent I think I have some Old Memory just laying around.
Tell me what you want, I will see if I have it.:D

Ok ... will do .. but right now  I am installing the text version. I'll have to pull those dimms er simms hehehe and take a look.

---

### Post by ventrical on 2014-03-15
No X

I was able to install to hdd, I got Grub and tried both kernels (and recovery mode also). Result= No X. Just a blinking cursor. No terminal .. nothing.. but I have some other ideas.

---

### Post by sudodus on 2014-03-15
I think you get some data by visual inspection, but you get other information from the lshw command, information that might or might not show outside.

```
sudo lshw|less
```

Example: the RAM in my Dell Dimension 4600 with a Pentium 4 CPU is listed like this:

```
*-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 2
             slot: CHANNEL A DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 3
             slot: CHANNEL B DIMM 1
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
```

---

### Post by ventrical on 2014-03-15
> **sudodus said:**
> I tried to improve it to avoid the problems you had one week ago. I'm glad you noticed the difference :-) Next, it will be interesting to see how the Ubuntu mini system works.

1. Boot problems: I have not changed anything that should make it harder to boot (at least not by intention). Maybe the quality of CD disks or burning  makes a difference. Did you use the minimum burning speed? 

Yes.

> 

Do I understand correctly, that 9w built on Debian Wheezy works for you with LXDE with only 80GB RAM? Or was that in another computer?

Yes .. it works correctly from the  liveCD but not after it is installed to hdd. Below is pic of it in action on 80MB liveCD.

---

### Post by sudodus on 2014-03-15
> **ventrical said:**
> No X

I was able to install to hdd, I got Grub and tried both kernels (and recovery mode also). Result= No X. Just a blinking cursor. No terminal .. nothing.. but I have some other ideas.

So it seems Trusty does not run even in this very simple installation without any graphics. It would certainly be interesting to find out if it is 'only' a RAM issue, or if it is something else related to the kernel and the CPU or some other hardware, so let us hope *runrickus* will find some suitable RAM for you.

---

### Post by sudodus on 2014-03-15
> **ventrical said:**
> 
Yes .. it works correctly from the  liveCD but not after it is installed to hdd. Below is pic of it in action on 80MB liveCD.

Nice screenshot :-) The installation seems successful.

So Debian Wheezy works but not Ubuntu Trusty in this very old computer with only 80 MB RAM.

---

### Post by ventrical on 2014-03-15
> **sudodus said:**
> So it seems Trusty does not run even in this very simple installation without any graphics. It would certainly be interesting to find out if it is 'only' a RAM issue, or if it is something else related to the kernel and the CPU or some other hardware, so let us hope *runrickus* will find some suitable RAM for you.


If it works ok from the live CD then why will it not work from the installed image? I do not think it is RAM problem.. I think it is matter of installation proceedure. I will have to trick it or clone it some other way  but then thats  not the prerequisite for the test, so, if it does not install correctly from standard CD to non -pae 80MB then it has to be determined as a failed install, not a failed .iso copy/download.

  I'll work on this. I'll be back later :)

---

### Post by sudodus on 2014-03-15
> **ventrical said:**
> If it works ok from the live CD then why will it not work from the installed image? I do not think it is RAM problem.. I think it is matter of installation proceedure. I will have to trick it or clone it some other way  but then thats  not the prerequisite for the test, so, if it does not install correctly from standard CD to non -pae 80MB then it has to be determined as a failed install, not a failed .iso copy/download.

  I'll work on this. I'll be back later :)

The live system is Debian Wheezy. The installed system is Ubuntu Trusty. Both have i486 kernels, but many things are different.

You can check the md5sum of the download, but I do not suspect an error there. I do not suspect an error in the installation. I think that the HDD with the installed system will run when moved to another computer (if it can be connected). Or you can try in a more powerful computer (of age similar to the one tested by Doug S or newer).

I think that this computer cannot run Ubuntu Trusty. At least not with only 80 MB RAM. Maybe there is something else, some capability of the CPU, that is missing, but the kernel wants. Or maybe some hardware driver that does not cooperate with the actual hardware, and it gets stuck at the blinking cursor.

---

### Post by sudodus on 2014-03-15
... or is there some start-up text, that is mixed with the login prompt? In that case, press Enter, and you should get a fresh login prompt.

```
nonpae login:
```

where you should enter guru and get the password prompt, where to enter the password 'changeme'.

```
nonpae login: guru
Password:

```

*Edit*: the text version installed from [SIZE=3]**[FONT=courier new]TrustyB1npae-text.iso[/FONT]**[/SIZE] uses only 38 MB when idling in my IBM Thinkpad T42, reported by ```
free -m
```

*Edit2*: I removed quiet splash and added the boot option ***mem=80M***. The Thinkpad boots and mem reports 68 MB available and now only 31 MB used when idling. So I suspect that there is some other thing than RAM, that might be the show stopper for you, *ventrical*.

---

### Post by ventrical on 2014-03-15
> **sudodus said:**
> Nice screenshot :-) The installation seems successful.

So Debian Wheezy works but not Ubuntu Trusty in this very old computer with only 80 MB RAM.

Nope. Installation not successful. Only live CD.

---

### Post by ventrical on 2014-03-15
> **sudodus said:**
> The live system is Debian Wheezy. The installed system is Ubuntu Trusty. Both have i486 kernels, but many things are different.


Ahh .. I see. Thanks for that clarification.

---

### Post by ventrical on 2014-03-15
> **sudodus said:**
> [SIZE=3]**[FONT=courier new][/FONT]**[/SIZE]

*Edit2*: I removed quiet splash and added the boot option ***mem=80M***. The Thinkpad boots and mem reports 68 MB available and now only 31 MB used when idling. So I suspect that there is some other thing than RAM, that might be the show stopper for you, *ventrical*.

Yes .. I think this could very well be it or it may be the mkusb script that is not cooperating with this vintage machine's hardware. I'll keep at it. :)

---

### Post by Doug S on 2014-03-15
My system is defiantly working better than last week. I was able to update/upgrade from a xterm window in graphics mode. I am able to use the web browser, but it does crash often. I think it just runs out of memory and quits. There is no /var/crash log file. I was able to browse my own web site no problem (mostly hand coded html). I am also able to open ubuntuforums.org (at 48 % memory used by the browser) and the Ubuntu+1 forums (at 51% memory used by the browser), but it would always crash when I tried to open this thread (I would see 53% memory used, then crash). I tried several times. However, by trying to open page 12 directly (which was short at the time) it did open. I was thinking it would be pretty cool to reply to this thread from that computer, but the browser crashed again when I tried to login via SSO.

I did install ssh server, which makes it easier to cut and paste the below from my puTTY session:```
guru@nonpae:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           115         98         17          0          1         59
-/+ buffers/cache:         37         78
Swap:          319         26        293
```Edit: added some "top" stuff (it seems to be using less memory this time):```
top - 22:13:56 up  1:13,  2 users,  load average: 0.39, 0.28, 0.30
Tasks:  84 total,   1 running,  83 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.0 us,  1.3 sy,  0.0 ni, 97.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:    118652 total,   115720 used,     2932 free,     2220 buffers
KiB Swap:   327676 total,    22032 used,   305644 free.    55856 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND
 3597 guru      20   0  396324  49548  30676 S  0.0 [COLOR=#ff0000]41.8[/COLOR]   0:29.69 [COLOR=#ff0000]x-www-browser[/COLOR]
  884 root      20   0  129588  12900   3864 S  0.0 10.9   4:51.77 Xorg
 1022 guru      20   0  235640   5652   4128 S  0.0  4.8   0:26.03 lxpanel
 3475 root      20   0   10936   3440   2712 S  0.0  2.9   0:01.28 sshd
 3494 root      20   0   29496   3280   2644 S  0.0  2.8   0:00.29 console-kit-dae
```

---

### Post by QDR06VV9 on 2014-03-15
> **ventrical said:**
> Ok ... will do .. but right now  I am installing the text version. I'll have to pull those dimms er simms hehehe and take a look.
  I'm not sure on this one? But have a look and let me know.
I think that's as old as I get any-more.

---

### Post by ventrical on 2014-03-15
> **runrickus said:**
> I'm not sure on this one? But have a look and let me know.
I think that's as old as I get any-more.


 I got tons of that memory :) The NEC Ready is a vintage machine that has the old simm setup any DDR or SDRAM will not fit.

Thanks for trying.

Regards..

---

### Post by ventrical on 2014-03-15
I finally got the hdd and cd to sync up in BIOS as both MASTER on my NEC Ready. That is the only way it will work. Otherwise it is very finicky with CS and SLAVE.

 Here is what I get when I boot up with the text.iso (and then just blinking cursor).

---

### Post by Doug S on 2014-03-15
ventrical: You seem to need what we used to simply call "EDO" memory, and that is the same memory I am using. 32 meg ones are not that common, as typically newer technology was used as memory requirements increased. Just a year ago I surveyed my friends for looking for 32 Meg EDO memories (or even 64 meg, which are really rare) and came up with none. I only have the 4 32 meg ones in my old test machine.

---

### Post by ventrical on 2014-03-15
> **Doug S said:**
> ventrical: You seem to need what we used to simply call "EDO" memory, and that is the same memory I am using. 32 meg ones are not that common, as typically newer technology was used as memory requirements increased. Just a year ago I surveyed my friends for looking for 32 Meg EDO memories (or even 64 meg, which are really rare) and came up with none. I only have the 4 32 meg ones in my old test machine.


Yes .. "EDO" that what is says in the pic I uploaded. I got some around. I'll just have to look for it.  I'll get back at it Monday.

Have great weekend you guys ! :) lol

---

### Post by Doug S on 2014-03-15
Notes from my install experience:
At the "Do you want to clone..." step: I suggest that "Y" be permitted as well as"y".
At the CD ROM error, not partition-able step: It was not obvious to me that I was in some VI editor mode and that I needed to type "q" to exit VI and continue.
Otherwise installation is trivial.

Note from desktop experience:
When I open "system tools" there is "Htop" and "UXterm" and "Xterm" in the list. If I click on "Htop" I get a UXterm console only.
However, I can run htop manually from a local terminal or my SSH session. I attach a frame from an htop session (note: I have never used htop before, I always use top).

Anyway, amazing that such a pathetic computer can run a GUI.

Edit: It seems to have re-sampled the attachment, which both made the file size bigger (was .png) and fuzzy.

---

### Post by sudodus on 2014-03-16
> **Doug S said:**
> My system is defiantly working better than last week. I was able to update/upgrade from a xterm window in graphics mode. I am able to use the web browser, but it does crash often. I think it just runs out of memory and quits. 

I think you are right.
> 
There is no /var/crash log file. I was able to browse my own web site no problem (mostly hand coded html). I am also able to open ubuntuforums.org (at 48 % memory used by the browser) and the Ubuntu+1 forums (at 51% memory used by the browser), but it would always crash when I tried to open this thread (I would see 53% memory used, then crash). I tried several times. However, by trying to open page 12 directly (which was short at the time) it did open. I was thinking it would be pretty cool to reply to this thread from that computer, but the browser crashed again when I tried to login via SSO.

I did install ssh server, which makes it easier to cut and paste the below from my puTTY session:```
guru@nonpae:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           115         98         17          0          1         59
-/+ buffers/cache:         37         78
Swap:          319         26        293
```Edit: added some "top" stuff (it seems to be using less memory this time):```
top - 22:13:56 up  1:13,  2 users,  load average: 0.39, 0.28, 0.30
Tasks:  84 total,   1 running,  83 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.0 us,  1.3 sy,  0.0 ni, 97.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:    118652 total,   115720 used,     2932 free,     2220 buffers
KiB Swap:   327676 total,    22032 used,   305644 free.    55856 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND
 3597 guru      20   0  396324  49548  30676 S  0.0 [COLOR=#ff0000]41.8[/COLOR]   0:29.69 [COLOR=#ff0000]x-www-browser[/COLOR]
  884 root      20   0  129588  12900   3864 S  0.0 10.9   4:51.77 Xorg
 1022 guru      20   0  235640   5652   4128 S  0.0  4.8   0:26.03 lxpanel
 3475 root      20   0   10936   3440   2712 S  0.0  2.9   0:01.28 sshd
 3494 root      20   0   29496   3280   2644 S  0.0  2.8   0:00.29 console-kit-dae
```

Nice that you were able to install ssh server :-)

Trusty is swapping, and far from using all the swap space. Obviously it works for you, but needs more RAM to be useful.

---

### Post by sudodus on 2014-03-16
> **ventrical said:**
> I finally got the hdd and cd to sync up in BIOS as both MASTER on my NEC Ready. That is the only way it will work. Otherwise it is very finicky with CS and SLAVE.

 Here is what I get when I boot up with the text.iso (and then just blinking cursor).

Not quite what I get in my Thinkpad, when I reduce RAM via the boot option until too low RAM to run. It would be nice if you could find some more EDO memory card and get a chance to test with more RAM.

---

### Post by sudodus on 2014-03-16
> **Doug S said:**
> Notes from my install experience:
At the "Do you want to clone..." step: I suggest that "Y" be permitted as well as"y".
This should be easy to fix in mkusb.

*Edit*: But how important is this change? And should it include all replies (also n+N, g+G, q+Q ...)? In that case I think it might be best to assume bash version 4.x+ and use 'Uppercase to lowercase or vice versa', 

```
y="this Is A test"
echo "${y^^}"
y="THIS IS a TeSt"
echo "${y,,}"
```

> 
At the CD ROM error, not partition-able step: It was not obvious to me that I was in some VI editor mode and that I needed to type "q" to exit VI and continue.
Otherwise installation is trivial.

I'm not sure I understand. The help text window shown by mkusb is displayed with the viewer ***less***. You exit from less with q. It is possible to get into VI editor mode from less, but definitely not the intention in this case.

It seems both of you are bothered by this help window. I switched it off in the desktop files but it is still available and active when you run mkusb from the terminal window (with the second parameter all). I could change that and use the second parameter **[COLOR=#ff0000]anh[/COLOR]** (meaning show [COLOR=#ff0000]**a**[/COLOR]ll mass storage devices, show [COLOR=#ff0000]**n**[/COLOR]o [COLOR=#ff0000]**h**[/COLOR]elp text).
> 
Note from desktop experience:
When I open "system tools" there is "Htop" and "UXterm" and "Xterm" in the list. If I click on "Htop" I get a UXterm console only.
However, I can run htop manually from a local terminal or my SSH session. I attach a frame from an htop session (note: I have never used htop before, I always use top).

That menu entry was created automatically, when I installed htop. I checked now, and it is the same problem for me. Obviously, htop creates a buggy menu entry in Lubuntu Core Trusty. Maybe I can fix it. The reason I have not fixed it is that I did not notice it. I usually run htop in a text screen or terminal window anyway (start it with the command htop).
> 
Anyway, amazing that such a pathetic computer can run a GUI.
Yes :KS

---

### Post by jerrylamos on 2014-03-16
Likely not of any use to you.  As far back as I go is a year 2000 IBM NetVista which does have pae.

With 320 MB of storage (max installable), the 9W live accessed the CD like fury and was very slow (!) in running iceweasel and gmail to save the data below.

It's a backup pc for my wife the 10 GB hard drive is cram full of her documents and pictures so I can't do an install without putting in another hard drive.

I do have an IBM Thinkpad which has an "M" processor, no pae as I remember, however this forum said the "M" was of no use to you.

vendor_id    : GenuineIntel
cpu family    : 6
model        : 8
model name    : Celeron (Coppermine)
stepping    : 6
microcode    : 0x8
cpu MHz        : 734.698
cache size    : 128 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pse36 mmx fxsr sse
bogomips    : 1469.39
clflush size    : 32
cache_alignment    : 32
address sizes    : 36 bits physical, 32 bits virtual
power management:

root@9w_dd_TrustyB1npae-LubuCore:~#

---

### Post by sudodus on 2014-03-16
> **jerrylamos said:**
> Likely not of any use to you.  As far back as I go is a year 2000 IBM NetVista which does have pae.

With 320 MB of storage (max installable), the 9W live accessed the CD like fury and was very slow (!) in running iceweasel and gmail to save the data below.

It's a backup pc for my wife the 10 GB hard drive is cram full of her documents and pictures so I can't do an install without putting in another hard drive.

I do have an IBM Thinkpad which has an "M" processor, no pae as I remember, however this forum said the "M" was of no use to you.

vendor_id    : GenuineIntel
cpu family    : 6
model        : 8
model name    : Celeron (Coppermine)
stepping    : 6
microcode    : 0x8
cpu MHz        : 734.698
cache size    : 128 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pse36 mmx fxsr sse
bogomips    : 1469.39
clflush size    : 32
cache_alignment    : 32
address sizes    : 36 bits physical, 32 bits virtual
power management:

root@9w_dd_TrustyB1npae-LubuCore:~#

Hi *jerrylamos*,

Your wife's computer will not define the lowest specs possible. It is not a computer without PAE capability. But it is still interesting at this stage, when we have found which computer can boot and run idle, but not really do much work.

So it can be interesting to find if your wife's computer can do some work, or boot Trusty from USB :-)

I suggest that you use 9w and try to install Lubuntu Core Trusty beta 1 to a USB {pendrive or HDD} of at least 4 GB. You can use any suitable computer for that task.

Then it would be very interesting to try booting both computers you describe from that USB drive:

- ***your wife's computer*** might **boot directly**, or it might need chainbooting via a **Plop** CD.

- ***your IBM Thinkpad***. (I have a T42, it boots happily from USB, and it works well with this **non-pae** kernel as well as grub booting with the Trusty PAE kernel and **fake-PAE** or the new boot option **forcepae** for updating/upgrading the kernel. The lowest level of RAM in my T42 is 80 MB, set via the boot option mem=80M using the Trusty text screen version.)

---

### Post by ventrical on 2014-03-17
@sudodus , all

  I'm on my way to see if I can pick up some extra EDO. :)

---

### Post by ventrical on 2014-03-17
I got it up to 97MB EDO RAM (from 80MB) but it tells me now that NTLDR is missing ! :)lol

---

### Post by ventrical on 2014-03-17
Update:

 Concerning NEC Ready non-pae system. I have determined through much examination that the hardware , paticularly the motherboard, is defective (will not hold BIOS settings - battery dead warning), and although it has had some sparks of promise to boot, I have to consider the downtime involved. I have other motherboards  and , time permitting, I'll check them out.

 Regards...

---

### Post by sudodus on 2014-03-17
> **ventrical said:**
> I got it up to 97MB EDO RAM (from 80MB) but it tells me now that NTLDR is missing ! :)lol

It seems something is very wrong!

It is Debian (the 9w installer) or Ubuntu Trusty (the installed program), that is longing for Windows?

---

### Post by sudodus on 2014-03-17
> **ventrical said:**
> Update:

 Concerning NEC Ready non-pae system. I have determined through much examination that the hardware , paticularly the motherboard, is defective (will not hold BIOS settings - battery dead warning), and although it has had some sparks of promise to boot, I have to consider the downtime involved. I have other motherboards  and , time permitting, I'll check them out.

 Regards...

Yes, now I think something else is wrong, 96 MB RAM should be OK, at least it should give another error message. There is probably some hardware, than cannot be managed by Trusty, or something that is defective. Anyway, it has been very interesting to follow your experiments with the old NEC.

Thank you very much for sharing these results :KS

... and if you have the time and find a second candidate (a suitable motherboard) ...

---

### Post by jerrylamos on 2014-03-17
Here's another semi old one, an IBM Thinkpad R31 circa 2003:

tpaduser@ThinkpadR31:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 11
model name	: Intel(R) Celeron(TM) CPU                1066MHz
stepping	: 1
cpu MHz		: 1066.483
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
bogomips	: 2132.96
clflush size	: 32
cache_alignment	: 32
address sizes	: 36 bits physical, 32 bits virtual
power management:

Currently running 10.04

Let me see if the 9W CD will boot;

First set of messages displays, runs for a little, screen goes blank and no CD activity.  Dead.
Probably not worth pursuing since it isn't old enough to be on-topic.

---

### Post by sudodus on 2014-03-18
> **jerrylamos said:**
> Here's another semi old one, an IBM Thinkpad R31 circa 2003:

tpaduser@ThinkpadR31:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 11
model name    : Intel(R) Celeron(TM) CPU                1066MHz
stepping    : 1
cpu MHz        : 1066.483
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
bogomips    : 2132.96
clflush size    : 32
cache_alignment    : 32
address sizes    : 36 bits physical, 32 bits virtual
power management:

Currently running 10.04

Let me see if the 9W CD will boot;

First set of messages displays, runs for a little, screen goes blank and no CD activity.  Dead.
Probably not worth pursuing since it isn't old enough to be on-topic.

Sad result :-(

Your result does not fit in the pattern, that IBM Thinkpads are easy to boot and run, but on the other hand, there is a reason why you are running 10.04 instead of a newer version of the Ubuntu family (for example Xubuntu 12.04 LTS).

- Did you check the md5sum of the downloaded iso file?
- Did you try the 9w CD in another PC (any age and kind except UEFI)? - Was burning the CD successful?
- Do you think it is a problem with a hardware driver, for example the graphics driver?

---

### Post by Doug S on 2014-03-18
> **sudodus said:**
> *Edit*: But how important is this change?Not very. I just did is all, I realized quickly that it needed a "y" and moved on.

> **sudodus said:**
> I'm not sure I understand. The help text window shown by mkusb is displayed with the viewer ***less***. You exit from less with q. It is possible to get into VI editor mode from less, but definitely not the intention in this case.I guess it was in "less" then. I am not familiar with "less" and mistook it for VI.

---

### Post by Doug S on 2014-03-18
Only now did I shutdown my old old test computer. It dropped down into text mode at the end and clearly left a message that the system was halted. I knew it was safe to turn the power off. Thanks very much, that part is much improved. My system ran for over two days without any issues.

---

### Post by sudodus on 2014-03-19
> **Doug S said:**
> Not very. I just did is all, I realized quickly that it needed a "y" and moved on.

I guess it was in "less" then. I am not familiar with "less" and mistook it for VI.

Do you think, that the help window (using the viewer less) should be given lower priority, for example, it could be activated on demand, not starting by default?

---

### Post by sudodus on 2014-03-19
> **Doug S said:**
> Only now did I shutdown my old old test computer. It dropped down into text mode at the end and clearly left a message that the system was halted. I knew it was safe to turn the power off. Thanks very much, that part is much improved. My system ran for over two days without any issues.

Thank you for great testing and sharing your test results :-)

I intend to wait a while and then

- do some improvements to to 9w installer and mkusb
- add a new version of Trusty non-pae, if available

---

### Post by Doug S on 2014-03-20
> **sudodus said:**
> Do you think, that the help window (using the viewer less) should be given lower priority, for example, it could be activated on demand, not starting by default?I do not know.

---

### Post by Doug S on 2014-03-20
My old old test computer failed to install the Trusty 14.04 32 bit server daily ISO!!!! It installs 13.10 Server fine.

Further testing with VM's shows that approximately an additional 64 (+ or - approximately 1 megabyte) Megabytes are needed for the installer between 13.10 and 14.04.

The error out message is: "Failed to load installer components".

The minimum requirements specification is changing from 128 Megabytes to 196 Megabytes.

I guess I am now more interested in this thread and the text only installation option.

Edit: Refined the extra memory requirement.

---

### Post by sudodus on 2014-03-20
The kernel is growing, and we need new methods to install the systems into computers with low RAM ...

It will make me happy if this 9w installer can help some people installing the text only Trusty system and build servers.

---

### Post by jerrylamos on 2014-03-20
> **sudodus said:**
> Sad result :-(

Your result does not fit in the pattern, that IBM Thinkpads are easy to boot and run, but on the other hand, there is a reason why you are running 10.04 instead of a newer version of the Ubuntu family (for example Xubuntu 12.04 LTS).

- Did you check the md5sum of the downloaded iso file?
- Did you try the 9w CD in another PC (any age and kind except UEFI)? - Was burning the CD successful?
- Do you think it is a problem with a hardware driver, for example the graphics driver?

This 9W CD runs on two other pc's.  O.K. on a 3.3 mHz Celeron, rather (!) slow for internet and yahoo on a NetVista 320 MB CD live.

Could be a problem with software support of the Intel graphics.  Ubuntu ran through months/years of poor Intel graphics support, a lot of it from Compiz trying things that didn't work.

Someplace I've got some notes on boot options to keep Compiz and other ubuntu kernel code from trying things that don't work.  I could try digging them up but not sure that Ubuntu development is at all interested.  

Runs in my mind that no Ubuntu past 12.04 will run on the Thinkpad perhaps something about memory addressing bits.  I forget maybe I've got some notes somewhere.

---

### Post by sudodus on 2014-03-21
> **jerrylamos said:**
> This 9W CD runs on two other pc's.  O.K. on a 3.3 mHz Celeron, rather (!) slow for internet and yahoo on a NetVista 320 MB CD live.

Could be a problem with software support of the Intel graphics.  Ubuntu ran through months/years of poor Intel graphics support, a lot of it from Compiz trying things that didn't work.

Someplace I've got some notes on boot options to keep Compiz and other ubuntu kernel code from trying things that don't work.  I could try digging them up but not sure that Ubuntu development is at all interested.  

Runs in my mind that no Ubuntu past 12.04 will run on the Thinkpad perhaps something about memory addressing bits.  I forget maybe I've got some notes somewhere.

I see. The problem is specific for this IBM Thinkpad R31. I agree, it could be poor support of the Intel graphics chip/card or maybe some other hardware issue. I don't think you need to search your old notes about it.

Thank you for testing and sharing your results :-)

---

### Post by Doug S on 2014-03-22
Out of curiosity, I made a virtual computer as similar as possible to my old old test computer, with 115 Megabytes of memory, and severely limited CPU allocation. The resulting machine has less usable memory and less cpu performance than my real computer. It seems to be working fine, and I have not been able to crash the web browser.

Myself, I think an interesting data point would be pq...'s computer with 128 Megabytes, but a faster CPU.

Stuff:```
Tasks:  88 total,   1 running,  87 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.3 us,  0.0 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:    105448 total,   102912 used,     2536 free,      812 buffers
KiB Swap:   327676 total,    31680 used,   295996 free.    31560 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND
 1168 guru      20   0  345512  49632  21260 S  0.0 47.1   0:54.35 x-www-browser
  836 root      20   0   71532  11768   3336 S  0.0 11.2   0:40.38 Xorg
  996 guru      20   0  171908   5808   4272 S  0.0  5.5   0:06.96 lxpanel
  997 guru      20   0  177376   4264   3224 S  0.0  4.0   0:34.07 pcmanfm
  993 guru      20   0   22276   3464   2328 S  0.0  3.3   0:01.08 openbox
  981 guru      20   0   48040   2416   1956 S  0.0  2.3   0:01.10 lxsession
 1001 guru      20   0   42368   2212   1840 S  0.0  2.1   0:02.99 notification-da
  778 root      20   0   34104   1504   1096 S  0.0  1.4   0:00.01 lightdm
  839 root      20   0   34820   1432   1044 S  0.0  1.4   0:00.02 accounts-daemon
  530 root      20   0   51784   1428   1004 S  0.0  1.4   0:01.02 NetworkManager
 1280 guru      20   0    5452   1364    972 R  0.0  1.3   0:00.02 top
  540 root      20   0   33772   1252   1024 S  0.0  1.2   0:01.01 polkitd
 1073 root      20   0   29512   1172   1172 S  0.0  1.1   0:00.00 console-kit-dae
``````
guru@nonpae:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           102         99          3          1          0         30
-/+ buffers/cache:         68         34
Swap:          319         31        288
```

---

### Post by sudodus on 2014-03-22
I think there are many computers around withe reasonably powerful CPUs but only 128 RAM. I agree, that it is worthwhile to try installing Trusty in such computers (using ***9w***).

I added this text to the opening post:

***Edit***: After testing for a couple of weeks we  have found that pre-pentium computers are not really an alternative for  Trusty. We have also found, that Trusty needs more RAM to be installed  via the conventional installers. Even the Ubuntu ***mini.iso ***will have problems at 128 MB RAM, trying to install a basic server.

I  think there are many computers around with 'more powerful' CPUs  (for example Pentium III, some old Celerons, and corresponding AMD  CPUs), but only 128 GB RAM. It is worthwhile to try installing  Lubuntu Core Trusty or the plain text version of Trusty in such  computers using ***9w***.

---

### Post by sudodus on 2014-04-26
A new version of the 9w installer has been uploaded as

[http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso](http://phillw.net/isos/linux-tools/9w/Trusty-npae124-text.iso)

 It uses *phillw*'s non-pae kernel '124' and is based on the released and updated/upgraded version of Ubuntu mini 14.04 LTS. See more details at this link

[http://ubuntuforums.org/showthread.php?t=2216356&page=2&p=13003216#post13003216](http://ubuntuforums.org/showthread.php?t=2216356&page=2&p=13003216#post13003216)

---

### Post by sudodus on 2014-05-15
There is a new wiki page for the ***9w*** installer can install systems with 80 MB RAM to install and run the Ubuntu mini.iso based text system.
[B]
Lubuntu Core Trusty[/B] needs 128 MB RAM to run and at least 256 MB RAM to be really useful. 

See this wiki page [https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w) 

and this page, where you can download the 9w iso files [URL="http://phillw.net/isos/linux-tools/9w/"]http://phillw.net/isos/linux-tools/9w/

[/URL]
Examples of non-pae CPUs

1. ***Early Pentium M with 1.2 GHz*** clock frequency. (The later Pentium M CPUs have PAE capability even if they lack a PAE flag).
2. ***Old ViA-processors around 1GHz***
3. ***Transmeta Crusoe***
(4. Pre Pentium II CPUs are too old and weak to be tested for this purpose)

You can test for the PAE flag with the following command

```
grep --color pae /proc/cpuinfo
```

If you are a happy owner of such a jewel, please help us test that the   non-pae kernel really works in a computer without PAE capability.[URL="http://phillw.net/isos/linux-tools/9w/"]
[/URL]

---

### Post by sudodus on 2014-05-20
There is a new version of the 9w installer, the [OBI-9w installer]("https://help.ubuntu.com/community/9w#Ubuntu_14.04_LTS_text_non-pae_.27Trusty-npae124-text.iso.27_and_.27obi_Trusty-npae124-text-9w.iso.27")

The One Button Installer in run from the 9w installer's debian system. Now there is a super light-weight installer, that can

- install from CD, DVD and USB
- create not only single boot but also dual boot systems.

Prepare partitions with Gparted and run the One Button Installer at the advanced level to create dual boot or multi boot system.

There are special tarballs for the 9w installer, and these tarballs come with the iso file.

---

