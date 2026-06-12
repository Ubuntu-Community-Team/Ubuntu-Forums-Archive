---
title: "questions on First install for a linux/ubuntu newb"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by theinvictus on 2005-08-01
Hi, I've been reading a lot about Ubuntu and linux in general lately, and I've come to the conclusion that I would like to try it out. However there are several questions that I have that have prohibited me from simply trying to install it myself.

I think I should explain my situation first, so that anybody who would be kind enough to help me out has a good base of knowledge to work with. I'll start with my system specs:

HP pavillion a640n 
Win XP Pro 
AMD Athalon 64 3400+
512 MB PC2700 DDR SDRAM
160 GB 7200RPM Ultra DMA hard drive
DVD+RW/CD-RW 8x DVD+R/RW
CD-ROM Drive 48x max. speed
NVIDIA GeForce FX5200XT AGP 8x graphics card 
with 128 MB DDR Video Memory and TV Out
Sound Blaster Value

Okay, since this is going to be my first experience with linux I would like to install it in addition to Windows XP, so that I can slowly learn how to use Ubuntu, while still being able to do whateverelse I need to. So the first thing I need to learn how to do is dual boot my computer. It is currently configured so that there are 2 partitions on one physical drive

HP_Pavilion (C:), total size 144Gb, 48.7 Gb Free Space
HP_RECOVERY (D:), Total size 4.84Gb, 744Mb

Then my DVD+RW/CD-RW drive is E:
my CD-ROM drive is F:
G-J: are taken up by removable media drives (USB 2.0, CompactFlash, etc.,)

So, how do I go about creating an additional partition on which to install Ubuntu Linux, without losing the information that is currently on my C drive,  and how do I configure my computer to dual boot.

Next, I'm asuming that since I have an AMD Athalon 64 processor, that I have the option of doing and AMD 64 Install, while still being able to do an x86 install, as is the case with Windows. Correct me if I am wrong about this. Which install should I do, and what are the Pros and Cons of each install.

Then...I already ran Ubuntu once using the live DVD, and it failed to access the internal clock, Ubuntu still booted fine, but I'm wondering what caused the failure, and whether or not this issue would impact my install. Also, when I ran Ubuntu off of the live disc, it took a long time to load (in comparison to WinXP), was this simply because essentially I was running the OS off the DVD, or does Ubuntu actually load slower than Windows?

Finally, I currently connect to the internet via a wireless internet connection, using a: Linksys 2.4 Ghz 802.11b Wireless USB Network Adapter. How do I configure linux in order to access the internet using this device. I noticed while running the live disc that it couldn't access the internet, and I assumed its because linux probably didn't recognize my USB adapter. Also, I will only be accessing the internet via this method for approximately one month more, at which point I will be going back to school, and connection via a LAN connection (what with the network cable and the jack and all), will I have to do anything special to be able to configure to my school's network?

That's the extent of my essential questions that I need answered before I attempt an install of Ubuntu linux. However, I also have a few other more trivial questions. 

I mostly use my computer for word processing, internet browsing, listening to music, and playing computer games.

Is there any software or any way to configure Ubuntu to be able to play the games I currently own (Half-Life 2, Counter Stike: Source, Warcraft III: Frozen Throne, Call of Duty, MVP Baseball 2005) ?

Alrite, that was a pretty hefty post, and I'd like to thank anyone who took the time to read it, and especially thank anyone who would be willing to take some time out of their busy lives to answer some of my questions.

- TheInvictus ](*,)

---

### Post by jasmuz on 2005-08-01
Hello there!

First off all, for you to install Ubuntu, you will need to repartition your drive in order to make space for Ubuntu's Ext3 root partition and a swap partition, this can be acomplished via any partition software (ie. Partition Magic).

Here is a graphical step-by-step guide on the install:

[http://mrbass.org/linux/ubuntu/install/](http://mrbass.org/linux/ubuntu/install/)

Depending on the CD image you download you will be able to do a 32 bit or 64 bit install. 

The actual speed of the Ubuntu system installed (at least for my case) is faster than a Windows install, but hey! dont take my word for it...try it yourself. :)

About your multiple connection issues read here:

[http://www.ubuntuforums.org/showthread.php?t=24994](http://www.ubuntuforums.org/showthread.php?t=24994)

For executing games designed for Windows you could try out WineCVS, read about that here:

[http://www.ubuntuforums.org/showthread.php?t=29996](http://www.ubuntuforums.org/showthread.php?t=29996)

I hope those links help you a bit.

---

### Post by mingus on 2005-08-02
*how do I go about creating an additional partition on which to install Ubuntu Linux, without losing the information that is currently on my C drive,  and how do I configure my computer to dual boot*

The resizing can be done by the partitioner within the Ubuntu installer, and most of the time this works fine.  Sometimes, safety checks fail and the partitioner will not resize.  So, many prefer to use PartitionMagic in advance.  It is highly advisable to first run chkdsk with both the /f and /r options, and then defrag, before partitioning - especially with a large partition like yours.  The Ubuntu installer will automatically install grub and setup the dual-boot.  Again, this usually works fine but there can be glitches especially given f the weirdness sometimes done by MS and manufacturers with the boot process.  So before installing make sure you have either XP/2K install media or a bootable W98/ME/DOS floppy (downloadable).

*Next, I'm asuming that since I have an AMD Athalon 64 processor, that I have the option of doing and AMD 64 Install, while still being able to do an x86 install, as is the case with Windows. Correct me if I am wrong about this. Which install should I do, and what are the Pros and Cons of each install.*

Search the forums to get a feel for this.  While the Linux kernel is ahead of W$ with 64-bit, there are still issues with both.   Personally, I would consider doing the initial install with 32-bit and thereafter install/setup the 64-bit alternative.   

*when I ran Ubuntu off of the live disc, it took a long time to load (in comparison to WinXP), was this simply because essentially I was running the OS off the DVD, *

Yes.

*or does Ubuntu actually load slower than Windows?*

If you mean boot, then the answer is "depends".  Each does some things faster than the other.  But with your rig, any diff should be negligible.  

*Finally, I currently connect to the internet via a wireless internet connection, using a: Linksys 2.4 Ghz 802.11b Wireless USB Network Adapter. How do I configure linux in order to access the internet using this device. I noticed while running the live disc that it couldn't access the internet, and I assumed its because linux probably didn't recognize my USB adapter.*

Yes, there are two considerations here, the card and the adapter.  If you search the forums and google this, you should find your answer.  Search for your particular Linksys model number; you need to know the chipset in the card because that is what the driver is written for.  I had to install a kernel module for my Linksys card to work.  

*connection via a LAN connection (what with the network cable and the jack and all), will I have to do anything special to be able to configure to my school's network?*

The wireline ethernet is no problem.  Depending on your school's network and security architecture, you may need to do some configuring.  Just make sure there isn't anything like some funky W$-only applet required to log-in, etc.

*Is there any software or any way to configure Ubuntu to be able to play the games I currently own (Half-Life 2, Counter Stike: Source, Warcraft III: Frozen Throne, Call of Duty, MVP Baseball 2005) ?*

Some games run under Wine.  For serious gamers, Cedega is great - the subscription is very inexpensive and the nbr of games supported very good.
[http://www.transgaming.com/](http://www.transgaming.com/)

Good luck!

---

### Post by theinvictus on 2005-08-02
Yes, there are two considerations here, the card and the adapter.  If you search the forums and google this, you should find your answer.  Search for your particular Linksys model number; you need to know the chipset in the card because that is what the driver is written for.  I had to install a kernel module for my Linksys card to work.  


After some googling I found some results, but I can't really make heads or tails of them, I'll post the links to see if any of you can translate them for me into something less involved. My model numbers is WUSB11 Ver. 2.6 and from my googling it appears that the chipset is Atmel

the sites that I found that appeared somewhat promising were:
[http://atmelwlandriver.sourceforge.net/usbtable.html](http://atmelwlandriver.sourceforge.net/usbtable.html)
[http://freewebhosting.hostdepartment.com/b/brounich/](http://freewebhosting.hostdepartment.com/b/brounich/)

If you could take a look at those and let me know what I need to do in order to get my USB adapter to work it would be much appreciated.

Thnx, 
- TheInvictus

---

### Post by mingus on 2005-08-03
There are 3 Atmel kernel modules (drivers) already in Ubuntu.  One is for a PCI card and another for pcmcia, so "atmel" may be it. 
$modinfo atmel (verifies module is present)
$sudo modprobe atmel (loads module for this session)
$sudo gedit /etc/modules (add "atmel" for load the module at boot)
$sudo iwconfig (shows if any wireless adapters are recognized)
$sudo iwconifg wlan0 up (activates the adapter)
$lsusb (shows what usb devices are recognized)
If this doesn't work straightaway, you're gonna have to do some searching.  Some adapters need tweaks in a config file, some need to be compiled from source instead.  I have several pcmcia and pci wireless cards, 1 of which is Linksys, but none using the Atmel chipset so I can't be more specific (they all automatically  installed and were recognized no problem).

---

