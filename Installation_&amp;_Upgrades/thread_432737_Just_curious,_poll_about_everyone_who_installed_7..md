---
title: "Just curious, poll about everyone who installed 7.04 : worked, fine or buggy ?"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2007-05-04
Seeing so many threads about people that have problems or had problems with 7.04, I was thinking "Cheeee, how many have no problems or fixed them versus those who didn't?".  So I am just curious to see what's the actual ratio with 7.04 for :

people that had no problems at installation time
people that had problems but fixed them
people that still have problems

---

### Post by hatstand on 2007-05-04
I had to uninstall and get back Edgy on one computer with Ubuntu. Fiesty Kubuntu at home works fine, and better than any Kubuntu I've had before.

---

### Post by FozzyB on 2007-05-04
I only have good things to say about 7.04, i installed it on my main machine which i am also dual booting with XP and everything i have tried so far has worked, (single core AMD with abit mobo and 7900GTO)

the biggest problem was installing the nvidia drivers however it turned out i needed to add in another line to my xorg.conf to get the restricted drivers to load,

however now they are working fine and i have installed beryl, cedega, open office, skype, swiftfox, ntfs write support, xmms, VLC and all are running fine with no problems,

the only thing i am using XP for now are the games i havn't managed to get running through ubuntu so far and my life is so much better.

Big thank you for everyone involved in making everything happen.

---

### Post by HobbitTR on 2007-05-04
I have been using Ubuntu for two years, during that time it has given me superb and almost flawless performance and ease of use.  I tried unsuccessfully to install Feisty and reinstalled Edgy until I am satisfied that Feisty is better.  I like the new features but I see too many forum entries about overheating, slow running and especially install/no boot problems.

I had the problem below. :confused: 

My machine booted into the LiveCD just fine and all went well during the install. I checked the CD Disk for errors, no errors found.

When I rebooted it stalled at the opening splash screen and the speedometer did not progress at all across the screen as normal.  I rebooted into the safe mode and it ran all text mode startup and I saw this message:

 /bin/sh: can't access tty; job control turned off (initramfs)

and then the boot stopped at:
SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

MY Drive Info:
hda: ST330013A, ATA DISK drive
hdb: Maxtor 6Y080L0, ATA DISK drive
hdc: CD-RW 52X24, ATAPI CD/DVD-ROM drive
hdd: PHILIPS DVDR1660P1, ATAPI CD/DVD-ROM drive

The bug reports say the system seems to see the second HD as a SCSI device.

I have disconnected my second HD, then it does not even start the boot sequence. 

I checked all my UUID's, they match with my fstab.

I tried the following but it did not work either:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)

Adding :
 libata
 pata_jmicron
 ata_piix
 ahci
 ata_generic

 to my /etc/initramfs-tools/modules

 and running : update-initramfs -u

 I may try to disconnect my extra HD next weekend and try to install again.  If anyone has a solution I would be pleased.

---

### Post by bellscott on 2007-05-04
I have had no problems with the download upgrade.....in fact this latest version solved quite a few problems that I had with 6.10!  It automatically found my old hp deskjet 3820 printer that I had attached to my home built pc.....it also automatically found and conected, without any assistance, my bt voyager 2110 adsl wired router.  I have it operating on both firefox and MS voyager 6.  I can also listen to all major radio stations in Scotland, both bbc and commercial.  Downloading and watching tv podcasts is no problem now, using Movie Player.

So far, so good.  Let's hope it continues - this from a brainwashed MS man!!!

---

### Post by davemiles871 on 2007-05-04
Installed onto VMware Worstation 5.5.4 without much trouble. Sound did'nt seem to work with the default (Alsa) settings but changed it to specifically use the Ensoniq devices and that made it make some recognisable noise (VMware passes sound through to the hosts sound system and provides an emulated hardware environment for the guest O/S to use).

One gotcha here is that the sound configuration tool has a test feature which when you use it produces a whistling noise - this noise came out even with ALsa or Ensoniq selected, but other applications made more musical tones once the correct device was selected.

Dave

:)

---

### Post by neiby on 2007-05-04
I don't use Ubuntu yet but I wanted to install 7.04. I can't even boot the live CD. I get the following messages:

/bin/sh: can't access tty; job control turned off

I'm then dropped into a (initramfs) prompt, followed by these messages:

ata2.01: failed to set xfermode (err_mask=0x4)
ata2.00: failed to set xfermode (err_mask=0x40)

I currently have PCLinuxOS on that PC, but that shouldn't matter because I'm booting to the Ubuntu CD.

---

### Post by LDRoamer on 2007-05-04
I have no sound. My old Compaq laptop uses an es1869 chip and it won't work (yet) under Feisty. It worked perfectly under Edgy. I have tried all the fixes I can find but no luck. I see there is a bug report on Launchpad about this so hopefully it will get fixed. Everything else seems to work fine though. However since most of what I use this machine for requires sound I am now back to booting Windows almost exclusively. Hopefully a fix isn't too far off.

---

### Post by williammanda on 2007-05-04
I just finished installing feisty on four computers. Core 2 duo, AMDx2, PIV 3 G, and PIV 2.8 G. All the installs went fine except for the Core 2 Duo. I had to use the alternate method due to a partitioning problem. Feisty wouldn't let me partition the last of the free space on the drive. It kept giving me an error "can't put the end before the start". I'm very satified so far.
Thanks

---

### Post by williammanda on 2007-05-04
> **neiby said:**
> I don't use Ubuntu yet but I wanted to install 7.04. I can't even boot the live CD. I get the following messages:

/bin/sh: can't access tty; job control turned off

I'm then dropped into a (initramfs) prompt, followed by these messages:

ata2.01: failed to set xfermode (err_mask=0x4)
ata2.00: failed to set xfermode (err_mask=0x40)

I currently have PCLinuxOS on that PC, but that shouldn't matter because I'm booting to the Ubuntu CD.

Download and install with the alternate cd.

---

### Post by Browser_ice on 2007-05-05
Only 41 replies ?

---

### Post by jml on 2007-05-05
I never like to be one of the first to do a dist-upgrade.  So I waited a few days and my patience paid off.  I run Ubuntu on a Darter I purchased from System 76.  Carl, one of the sub-forum moderators warned that there were issues with the Darter, so I waited until there was a final fix for the problem.  Well I had to wait a little over a week for the fix to come down from System 76, but the wait was worth it.  After reviewing information from System 76, these forums and other third party sites (Automatix,) I was able to upgrade successfully.  It hung a few times, and at least twice during the process my Darter froze up hard enough to force a shut down.  But in the end, after about three hours of effort, I had a fully functioning system, with everything working.  Just one geek's experience.

Joe

---

### Post by Browser_ice on 2007-05-05
I forgot to mention that upon installing 7.04 over 6.10, I only had a very minor problem (didn`t import my firefox bookmars from XP when I asked it to do so). Everything else went smoothly. I even have access to all my XP drives.

---

### Post by DarkN00b on 2007-05-05
Feisty itself worked perfectly "out of the box" for me. 

The only problem I have is with Beryl. Apparently Beryl doesn't play well with xorg 7.2. On my laptop  with Intel integrated graphics, there is a problem with blur effects which causes artifacting around and behind windows. The same thing happens with my desktop with nvidia graphics.

---

### Post by merlinus on 2007-05-05
Overall, I am extremely pleased, especially to now live in a land without gates, windows, jobs, or apples.

But....

My cd burner has not been detected, and no forum suggestions have made it so.

The power-off-monitor-after-x-minutes feature does not work.

I am unable to access ubuntu from my win2000 box, although it works fine the other way round.

I still need my dual-boot in order to run one important program and burn cds, but otherwise I am very grateful.

-merlin

---

### Post by aysiu on 2007-05-05
> **Browser_ice said:**
> Only 41 replies ?
There were 1262 replies to [this poll](http://ubuntuforums.org/showthread.php?t=414935&highlight=feisty+upgrade).

You're posting in the user support area where people give user support. The community cafe is the place for polls and discussion.

---

### Post by jcg on 2007-05-05
> **hatstand said:**
> I had to uninstall and get back Edgy on one computer with Ubuntu. Fiesty Kubuntu at home works fine, and better than any Kubuntu I've had before.

The installation went smoothly; the system works well, however, it shut itself down after a couple of hours, no reason given.
I have double boot ; XP hasn't have this behaviour.
any suggestions?
jcg

---

### Post by Rognalf on 2007-05-11
> **neiby said:**
> I don't use Ubuntu yet but I wanted to install 7.04. I can't even boot the live CD. I get the following messages:

/bin/sh: can't access tty; job control turned off

I'm then dropped into a (initramfs) prompt, followed by these messages:

ata2.01: failed to set xfermode (err_mask=0x4)
ata2.00: failed to set xfermode (err_mask=0x40)

I currently have PCLinuxOS on that PC, but that shouldn't matter because I'm booting to the Ubuntu CD.

I have a somewhat similar problem although the ata2* might be ata3* for me. I see the suggestion for downloading alternate cd. 
I don't think this will solve anything. I first encountered this after upgrading from edgy to feisty. Then I downloaded and ran the Feisty LiveCD. My system does eventually start, and I can install, but the problem persists after reboot.

I'm running on a MSI 915P Combo mainboard
2 gigs ram, 3ghz intel emt64 processor
sata hard drive

Edgy is running like a dream. I've installed Feisty onto a machine I use on a TV and that runs fine.
Is there any chance my mainboard isn't supported by the new kernel. FC6 with the same 2.6.20 kernel gave the same result.

Ah..found a possible solution. The error is connected to the optical disk drive. Edit boot arguments for system in grub menu. Press e on default kernel and append irqpoll to the boot arguments.

---

### Post by anarchitecton on 2007-05-11
> **HobbitTR said:**
> 
I had the problem below. :confused: 

My machine booted into the LiveCD just fine and all went well during the install. I checked the CD Disk for errors, no errors found.

When I rebooted it stalled at the opening splash screen and the speedometer did not progress at all across the screen as normal.

I'm having exactly the same problems.... still haven't been able to install Ubuntu 7.04.... :(

---

### Post by kelvin spratt on 2007-05-11
no problems for me

---

### Post by zdude on 2007-05-11
I upgraded from Edgy using the update-manager, pushing the update button. All went fine except the nvidia drivers that I had to manually fix. Only strange thing occurring was compiz was using my beryl theme that I had running in edgy but installing beryl corrected that. Wine 0.96 did not work correctly with some programs so I reverted back to the edgy 0.94 version which actually seems to work even better than under edgy. 
Only problem I have is when using suspend on my desktop it does work (edgy suspend did not) but it reassigns my ethernet dev from eth0 to eth1. I've yet to find a solution for this but others are having this problem as well. Everything seems equal to or better, than edgy.
My $0.02

---

### Post by Billy_McBong on 2007-05-11
[COLOR="Blue"]i did a fresh install of feisty yesterday on my new computer that i just finished building.
barely any problems.

feisty is amazing:) :) [/COLOR]

---

### Post by trinity! on 2007-05-11
I got an error right away.  Couldn't mount CD.  I tried and tried to get past it.  Did get any answers from the forums.  Then I gave up and installed the beta 3 of Longhorn.  That worked with no problems:confused:

---

### Post by littlelmo on 2007-05-11
Downloaded the Ubuntu cd last night and installed it on an older computer (1.2 mhz cpu)  tonight. Everything loaded like a charm. It looks great and already like what I see. Thanks to all who made this possible.

---

### Post by Browser_ice on 2007-05-18
I thought this thing would get more votes then this by now.

Kinda disapointed ...

---

### Post by theDaveTheRave on 2007-06-29
I've loaded edgy onto my Desktop (dual boot0 and upgraded from Edgy to feist on an old Compaq laptop (and it ran a lot quicker).

Only downside.

My college course requires NetBeans 4.1 - and I can't get it too run on Edgy? so I've got NetBeans 5.5 instead - doesn't seem to have any backward compatibility issues (yet!)


The Laptop is so old it won't run NetBeans (shame really) - when I compile the program it takes for ever.....

I recently got a new laptop (Vista installed) - I surprised how nice Vista looks - but it isn't half slow - my 4 year old desktop runs faster (with less memory) -  so I'm going to dual boot Feisty onto it.

I hope that watching DVD's will be better with Feisty than with Vista - it does get a bit "jerky" sometimes - bit like watching old WW2 newsreel! I fully expect to have to play to get the wirless functioning, but as I have a wireless USB key that I know I can get to work I will use that if I have to in the interim.

Otherwise I'm more than happy and only log into the windows box when I want to uplink the photo's from my phone -  I really must find a solution for that one.

Dave

---

### Post by CheeseEatingBulldog on 2007-06-29
On my desktop it went fine, after upgrading and b0rking it I just fresh installed and all worked out of the box. My laptop however had a wifi driver that was blacklisted for boot up, and the network manager needs an extra character on the end of the ESSID to work, but it is very stable now.

---

### Post by EvilRusk on 2007-06-29
I'm getting the same problem as a number of people I have seen. After install, the splash screen loading bar does not progress as normal. It's like the cpu time is being chewed up as the HDD lights are barely flashing.

6.10 produced a similar problem. Previous to this I never had any new install problems with any linux I tried. I'm a bit disappointed really. Didn't expect it all to work out of the box (xp doesnt either!) but I did expect it to boot the system...

---

### Post by Kubunteando on 2007-06-29
I upgraded fine, no major issues. Some" minor" issues:

- can only download photos with digiKam if I am root (it was working fine in Edgy)
  It took me a couple of months to find out the solution. It seems to be a bug, solution found in Ubuntu bugzilla.

- when I activate the WiFi I get 3 error messages related to DCOP. Just annoying, WiFi works

- the WiFi is not so stable with the bcm43xx driver, I get the kernel error of IRQ_TIMOUT, and I have to reboot the coimputer, only way to fix it

Luckily I don't have to use the WiFi that often, not yet...

The fixes are slow, although the problems are severe. But if we think that most of the times no Linux drivers are released by the manufactures, we should be happy.

Even so, Feisty is the best Linux I have had so far, and the best Kubuntu version (worked with Dapper, Edgy and Feisty). So definitely the direction is very much the right one.

---

### Post by ubuntujonez on 2007-07-02
I had recently done 2 debian dist-upgrades with amazing success and when I saw the blinky button on my ubuntu desktop I had no worries and clicked. Boy what a stupid idea that was. I've been using Linux for over 10 years and Ubuntu for 3. I'm really mad now.

Why did this poll close so fast? Were the successes dropping fast and it was getting more and more embarassing?

Anyway, my ps2 keyboard and my usb dvd RW no longer work. 

Putting a flashy upgrade button on the desktop is clearly a really bad idea; unless the goal is to drive people to Fedora.

---

### Post by oiler920 on 2007-07-02
My Feisty install was garbage. X failed the first time I booted up, so I had to upgrade from Edgy. :(

---

### Post by ubuntujonez on 2007-07-03
I reinstalled (7.04 server) from scratch then installed ubuntu-desktop. It worked ok but still the same problems. (keboard broken via attaching to x11vnc session). 

3rd install from scratch (7.04 desktop) sort of works ok.

Sorry... Feisty is NOT for human beings... it's for geeks like us with no need for friends and would rather waste days reinstalling in every possible way ;-)

---

### Post by Browser_ice on 2007-07-12
Hummm, almost as many people had no problems then those that had major problems.

Is it a safe assumption that it is the case worldwide ?

---

### Post by ubuntujonez on 2007-07-12
I wouldn't assume anything with just over 100 responses. I ended up having to go back to 6.10 due to a slow system with a 2.6.20 kernel bug with my motherboard/onboard IDE bus and several lost days of troubleshooting (Dell Dimension 4600).

---

