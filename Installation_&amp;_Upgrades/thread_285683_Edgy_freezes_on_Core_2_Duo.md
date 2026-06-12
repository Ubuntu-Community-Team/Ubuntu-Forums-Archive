---
title: "Edgy freezes on Core 2 Duo"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by the kaz on 2006-10-27
Hello all, 
I have a Core 2 Duo system that simply won't work stably with Ubuntu. I have tried the betas and dailies over the last few weeks, and installed the Edgy final last night, but all versions have the same problem: the installed system just randomly freezes.

My system is a E6600, 2GB RAM, 400G SATA HD, PATA DVD-ROM connected to a JMicron chip on the Foxconn P965 board. The on-board ethernet is a Marvell chip which isn't supported by the installed kernel (that's one of the reasons I try to compile another kernel), but whether the network interface is active or not does not seem to matter in regard to the freezes. By freeze, I mean a complete standstill of all operations - the VGA output is still visible, but doesn't change anymore, keyboard and mouse don't work anymore, the system doesn't respond to ping etc. 

This can happen at any time after a minute or after an hour, but it doesn't happen when the system is idle, only when I start something like synaptic, or a kernel compile, or just an apt-get update. When it happens, absolutely nothing is written to any log file. This happens with the generic kernel image, with the i386 kernel image, with a self-compiled 2.6.17.13 ubuntu kernel source, and with a self-compiled 2.6.19-rc2-mm2 from kernel.org. Yet, under Vista RC1 and XP SP2, the system runs without any problems for hours on end. 

I am completely out of ideas what to do next - I'm actually close to abandoning linux altogether for this machine, as I've spent more than 20 hours now it seems to be impossible to get it running on this system. Therefore, any help whatsoever is appreciated. 

Greetings, kaz.

---

### Post by cosmix64 on 2006-10-27
I've been having the same issue here. Although I've been running Edgy RCs for  several days with no problem whatsoever and 2.6.17-10-generic, one (or more) of the latest software updates introduced this instability on my system too. 

If you're certain that the hardware is fault free you can try one or more things to see if it improves: First give 'dpkg-reconfigure --all' a try, so as to make sure that it's not some package that's not configured properly. This is especially useful if you upgraded from Dapper. There may also be some ACPI/APIC issue at hand, although I haven't tried fiddling with either the BIOS or kernel parameters, but you may want to give any (or both) a try. 

Finally, try having your machine do stuff, but not in X. go to a tty, stop gdm and run some things on the machine without having X running. I am suspecting the nvidia module (yet again).

Good luck.

---

### Post by the kaz on 2006-10-27
> **cosmix64 said:**
> I've been having the same issue here. Although I've been running Edgy RCs for  several days with no problem whatsoever and 2.6.17-10-generic, one (or more) of the latest software updates introduced this instability on my system too. 

I've had the freeze problem with **all** Edgy pre-versions I've tried out. 

> Finally, try having your machine do stuff, but not in X. go to a tty, stop gdm and run some things on the machine without having X running. I am suspecting the nvidia module (yet again).


I haven't installed the nvidia module yet, the system runs with nv. I wanted to get the system stable before installing 3rd-party extensions. 

And for a while, I too expected X to be the problem - until this morning, when I got a system freeze in rescue mode (where I was trying out an apt-get update). Therefore, the problem doesn't seen to be connected to X/Gnome or any gfx card server running under X. 

I'll try out the reconfigure idea later today, though - as about half a dozen Snyaptic package updates/installs couldn't be completed due to the frozen system, there could be quite a few config errors. 

Greetings, kaz.

---

### Post by cosmix64 on 2006-10-27
No luck. System just froze again after doing a dpkg-reconfigure. Let's gather some more info and file a bug report on this.

I'm thinking of doing a clean install.

---

### Post by kamstrup on 2006-10-27
I've tried installing Edgy "stable" on my AMD64 machine but havent been able too. I've tried i386-desktop, amd64-desktop, and amd64-alternate all crashed/stalled during installation.

The i386 desktop cd boots up to the desktop just fine, but at some point during the installation X just freezes hard. I even tried the vesa driver for X, but still had hard freezes. I guess Edgy is just not for this box.

Dapper runs fine though.

---

### Post by the kaz on 2006-10-27
> **cosmix64 said:**
> No luck. System just froze again after doing a dpkg-reconfigure. Let's gather some more info and file a bug report on this.

I'm thinking of doing a clean install.

I hope you fare better than I did - all my installation attempts of the last two weeks where clean installs. As my machine is only 15 days old, I had no previous Ubuntu installed, and as I wanted to make sure to leave no part of the freezing system on disk, I reinstalled from scratch each time. And my system still freezes. 

Greetings, kaz.

---

### Post by cosmix64 on 2006-10-27
I am afraid I didn't. It's strange.

I upgraded my hardware about 10 days ago. I've had Edgy ? software running for ages with no problem, even after the upgrade. Up until yesterday I had no problems with Edgy RC whatsoever. First lock up was yesterday morning. It's been getting more frequent. I just bought a Zalman 9700LED to make sure it's not cooling, although with the stock HSF the temp. never exceeded 50ºC. The machine froze a few minutes later. 

I just experienced something very worrying though that got me thinking: the machine just froze, immediately after booting, during POST, after I hard reset it from a previous crash. This does not necessarily translate to a hardware problem, but it's weird. My hardware checks out ok, memory was found ok by memtest86, hard disks are ok, the temps are very low (mid 30s for the CPU, 25-35 for the board, around 60 for the Graphics core -- a 7600GT). 

Since you've already clean installed ubuntu I'm at a loss here. While I haven't compiled my own on this machine, I am not very much willing to invest the time to do so after reading about your experience. 

We need more information about this; more people sharing their experiences on the platform. 

Can you be a bit more specific on your hardware? Which motherboard do you have (model), BIOS options re: ACPI, etc. Once we gather enough info, let's file a bug.

---

### Post by punx45 on 2006-10-27
I was just browsing the ubuntuguide.org wiki on Edgy and noticed this howto for enabling multicore support:  [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Multicore_Support]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Multicore_Support")

not sure if that is your problem or solution.   just throwing it out there.

---

### Post by Paul Dufresne on 2006-10-27
>PATA DVD-ROM connected to a JMicron chip on the Foxconn P965 board.
Then this would really looks like bug #57502
See [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)

---

### Post by cosmix64 on 2006-10-27
Paul and Punx, your messages are unrelated to the problems described in this thread I'm afraid.  

Kaz, do you have any additional PCI cards on the board? I had an Creative SB Audigy 2 ZS and I removed it. I haven't had any freezes since. Maybe that was it. I can live with HDAudio for now anyway, it's not like I'm using any of the Audigy's capabilities with ALSA.

---

### Post by cosmix64 on 2006-10-27
Spoke too soon. Reading into this, at least my Asus board (P5B Deluxe) seems to have a whole lot of problems on its own, irrespectively on how bad the support for 965P/Jmicron/Core2Duo thermal is in 2.6.17-10.

I'll update if/when I have more news.

---

### Post by amorangi on 2006-10-27
Crashing under load would indicate to me a heat problem with one of the components. Especially on a new system that isn't proven I would check the components as a first step. 
Crashing on POST is definitely a hardware issue.

---

### Post by cosmix64 on 2006-10-27
> I would check the components as a first step

Done that. They all check out in my case, as I wrote earlier.


> Crashing on POST is definitely a hardware issue.

Nope. Apparently, the P5B board (The one I'm using) is notorious for its buggy BIOS. It's had 8 revisions in 10 weeks. Check <a href="http://www.short-media.com/forum/showthread.php?t=50712">this page out</a> and especially read the section with the unresolved functionality issues. Warm Reset failure is one of them. 

In the past 20 or so years, I recall more than one case where extension cards or controllers were left in a bad state and caused system malfunction after a warm reset. And while it's true that such phenomena are rare, you cannot be as absolute as your comment suggests you are. It's actually surprising that Asus released such a board to the market, if all I'm reading online about it are true.

Nevertheless, I am not excluding faulty hardware just yet and you do have a point, however I am not certain yet and need to look at this further.

If anyone has any ideas, please share.

---

### Post by the kaz on 2006-10-27
> **cosmix64 said:**
> Kaz, do you have any additional PCI cards on the board? I had an Creative SB Audigy 2 ZS and I removed it. I haven't had any freezes since. Maybe that was it. I can live with HDAudio for now anyway, it's not like I'm using any of the Audigy's capabilities with ALSA.

Apart from the XFX 7950GT graphics card in the PEG slot, the only other card is also PCI audio card, in my case an Audigy 4. I haven't tried removing it, but as your system also freezes when using the onboard HD Audio, I'm not that eager to try it out. 

My board is a Foxconn P9657AA-8EKRS2H (I'm not kidding, that's the actual name), BIOS version F1P28 (latest from website, dated Aug 31st). ACPI is enabled, Power saving is at "User Define" with the actual powerdown settings for HDD etc. all disabled. 

Greetings, kaz.

---

### Post by the kaz on 2006-10-27
> **amorangi said:**
> Crashing under load would indicate to me a heat problem with one of the components. Especially on a new system that isn't proven I would check the components as a first step.
At least for my PC, I seriously doubt that. First of all, the system runs fine under load when I boot XP or Vista RC1. I've run quite a few benchmarks under XP and had no problem whatsoever. 

Addtionally the Sonic Tower CPU cooler doesn't even get warm; the graphics card is warmer, but not hot. The PC is currently running open, ruling out any heat buildup inside the case. 

As I even got a freeze while running in rescue/single-user mode, I'm wondering if there might be any SMP-related problem that needs a certain load to surface. Maybe I should try out a kernel without SMP support?

Greetings, kaz.

---

### Post by thedude2k on 2006-10-27
> **the kaz said:**
> At least for my PC, I seriously doubt that. First of all, the system runs fine under load when I boot XP or Vista RC1. I've run quite a few benchmarks under XP and had no problem whatsoever. 
...
As I even got a freeze while running in rescue/single-user mode, I'm wondering if there might be any SMP-related problem that needs a certain load to surface. Maybe I should try out a kernel without SMP support?


My Edgy also freezes with a Core2Duo (Gigabyte 965P DS3 board...) but only when I try booting the SMP kernel (linux-image-generic).  Its not a random freeze, though... my system locks up hard on bootup.  As I did an upgrade from Dapper, *generic was not enabled by default so I did not notice any problems till I switched to the *generic kernel.

You might want to try the 386 kernel for shits and giggles... you'll lose a core, but its been stable for me...

(... now to figure out which kernel bootup flags will get me my 2nd core back...)

---

### Post by Cynical on 2006-10-27
I have a Gigabyte DS3 board and I've had 0 problems with edgy. Just make sure your SATA drive is connected to the ICH8 controller. (If you have an IDE hard drive and cdrom drive then you're in trouble)

---

### Post by the kaz on 2006-10-28
> **thedude2k said:**
> My Edgy also freezes with a Core2Duo (Gigabyte 965P DS3 board...) but only when I try booting the SMP kernel (linux-image-generic).  Its not a random freeze, though... my system locks up hard on bootup.

Well, maybe the problems are related - my Core2 runs fine without freezes (so far, after ten hours), first with the stock i386 and then with a self-compiled non-SMP version of the 2.6.17.13 sources Ubuntu installs when you select the kernel source package (I compiled this with one modification to get the Marvell ethernet chip on the Foxconn mainboard to work). 

That's far from an ideal solution, as I can only use half the CPU - but at least it works for now. Also, we now have a possible source for the problems: there might be a bug in the SMP implementation of the kernel in regard to Core2 processors. 

cosmix, could you try out if you still get freezes when booting with the 386 kernel (the package name is linux-image-386)?

Greetings, kaz.

---

### Post by thedude2k on 2006-10-28
> **Cynical said:**
> I have a Gigabyte DS3 board and I've had 0 problems with edgy. Just make sure your SATA drive is connected to the ICH8 controller. (If you have an IDE hard drive and cdrom drive then you're in trouble)

Not sure its the board itself that is causing the problem... it freezes only when I use the *generic (SMP) kernel, and more precisely right after it finds the 2 cores.  I have no problems with my drives (it even finds my PATA DVD drive that Dapper couldn't find... finally!).  You using a dual core processor?

> **the kaz said:**
> Well, maybe the problems are related - my Core2 runs fine without freezes (so far, after ten hours), first with the stock i386 and then with a self-compiled non-SMP version of the 2.6.17.13 sources Ubuntu installs when you select the kernel source package (I compiled this with one modification to get the Marvell ethernet chip on the Foxconn mainboard to work). 

Looks like the non-SMP kernels work A-OK.  Interesting bit about the Marvell chip though... my Gigabyte board also has one (8053 Gigabit LAN Controller) and I haven't had a single issue with it in any <1 yr old kernels...

> **the kaz said:**
> That's far from an ideal solution, as I can only use half the CPU - but at least it works for now. Also, we now have a possible source for the problems: there might be a bug in the SMP implementation of the kernel in regard to Core2 processors. 

Agreed, guess I'll boot up FC5 or SLED10 (both working dual core on my box, but with older kernels) to do processor-intensive stuff :-)

Wonder if all 2.6.17 kernels have issues, or only Ubuntu versions...

---

### Post by the kaz on 2006-10-29
> **thedude2k said:**
> Looks like the non-SMP kernels work A-OK.  Interesting bit about the Marvell chip though... my Gigabyte board also has one (8053 Gigabit LAN Controller) and I haven't had a single issue with it in any <1 yr old kernels...

The Foxconn P9657AA uses a different Marvell chip (88E8056) which isn't recognized by kernels before at least 2.6.18. The Mavell driver (sky2) works fine with this chip, but it doesn't know that i can handle the chip because it has a different device ID number. Therefore the vanilla kernel module doesn't even try to initialize the chip and simply passes on the 8056. 

You just need to add one line of code to the sky2.c source (the device SubID of the 8056) to get it working. That's why I tried to compile a custom kernel in the first place. :)

Greetings, kaz.

---

### Post by the kaz on 2006-10-29
> **thedude2k said:**
> Wonder if all 2.6.17 kernels have issues, or only Ubuntu versions...

I had tried out 2.6.19-rc2-mm2 from kernel.org during one of my tests with the Edgy RC DVD ca. ten days ago and experienced freezes as well. But now that I've got a stable install, I will try that out again later today. The support for both the ICH8 and the JMicron is said to have improved with the newer kernels, anyway. I'll report the results here. 

Greetings, kaz.

---

### Post by cosmix64 on 2006-10-29
Hello,

I think I now have enough information to call this a hardware problem with my board, so disregard my previous comments here. 

Specifically, the first thing worth mentioning is that my memory modules (2x Supertalent DDR2-533 1GB) seem to be incompatible with the Asus P5B Deluxe board. That is, besides the grief they've been giving me, they are not included in Asus' QVL or Supertalent's web site under the compatible modules for that board. I am not 100% certain that this the reason for the failure and that it is not a faulty board (the latter is very hard to diagnose without swapping everything), but the first thing to do is to return the DIMMs to the store and get replacements. For the curious, I've already tried 2 different PSUs to no avail. 

It is very strange that the machine worked fine for a week before starting to freeze randomly. Yesterday it kept running for more than 8-9 hours before it froze again (everytime with 2.6.17-10-generic). I've also noticed that I'm getting "bad page state"s occasionally in dmesg, so this is bound to be hardware. memtest86+ checked out ok almost every single time, however.

kaz, I will revisit the issue and try 2.6.17-10-386 after replacing the RAM with 'compatible' modules.

Regards

---

### Post by amorangi on 2006-10-29
That's the first thing I ran into with my Asus P5B - memory modules - normally boards are a little more forgiving (QVL taken as a guide not gospel), but this is VERY fussy about what it takes. This I discovered to my $ cost.

---

### Post by garrath on 2006-10-29
I don't usually post here, but I have found something perhaps you would find interesting or at least be able to shed light on for me. I posted this on a gentoo forum a few minutes ago [http://forums.gentoo.org/viewtopic-t-511742.html]("http://forums.gentoo.org/viewtopic-t-511742.html") I'll just cut and paste here :

>  have a gigabyte ga-965p-ds4 with an ich8 and JMicron controller and I was suffering from random hangs every now and then. Sometimes a complete hang, other times I would be able to use the mouse and toggle the num lock led on the keyboard. syslog showed nothing. I left dmesg running in a console (watch 'dmesg | tail -n 50') and open on the main screen and began using my system. The hanging issue was kind of random, but I eventually saw errors about the sata port freezing and it being soft reset. Soft reset seemed to be okay (sometimes the app using the hd at the time crashed) but the hard resets seemed to freeze the system.

Anyway, my system has 4 sata disks set up in AHCI mode. 3 of the 4 are sata2, and the kernel messages at startup tell me the 3 sata2 disks are running at 3.0GBs. Long story short, it was only the 3 sata2 drives that were causing the errors I saw on dmesg. Forcing the hard disks to 1.5GBs (by using jumpers on the hard disks) solved the problem completely (well, I have tested it for the past few hours and no crashes or error messages yet).

I have seen posts about random crashes using the ich8 controller around so perhaps this is the reason for some of them. Please let me know if it helps. I'm not entirely sure why it is working, but I assume there is some libata problem when the drives are running at 3.0GBs. Can anyone shed any light on this or a better solution?

Any helpful insight is appreciated.

---

### Post by bohne on 2006-10-31
Just installed Edgy-Eft AMD64-desktop on my E6600 core 2 duo without problem. :D  I'm running an Asus P5B Deluxe board, with the version 0711 bios update.  The only card I have installed on the board is an XFX 7900GT. The Nvidia drivers (off of Nvidia's site) installed and seem to be working fine.

In the bios 0711 change log, there are mention of fixes for memory compatibility and even a memory stability fix.  Might be part of the freeze issue.  I'm running Corsair XMS2 memory on the board (it was on Asus's approved mem list).  

I have not tired to get the second Marvell NIC working yet, but the one does work fine.  Still running with the generic kernel.  Both cores are working and are listed in /proc/cpuinfo

Also of note, I have a SATA HD and a PATA (IDE) DVD-ROM.  When I tried installing Dapper a few weeks ago, it wouldn't work (JMicron issue).  But the install went fine with Edgy.

---

### Post by the kaz on 2006-11-02
> **bohne said:**
> Just installed Edgy-Eft AMD64-desktop on my E6600 core 2 duo without problem. :D  
I'm using a 32bit kernel (for 3rd-party software compatibility reasons). Perhaps it really depends on the architecture? 

> **bohne said:**
> Also of note, I have a SATA HD and a PATA (IDE) DVD-ROM.  When I tried installing Dapper a few weeks ago, it wouldn't work (JMicron issue).  But the install went fine with Edgy.

Yes, that's what I experienced as well. Now, if I only could get rid of these freezes... :mad: 

Yesterday, I compiled the brand-new 2.6.19-rc4-mm1 kernel with SMP enabled. Froze again after about 30 minutes. :( So far, I haven't experienced **any** freezes with non-smp kernels, so I'm still fairly sure the problem is located (or at least triggered) in the SMP code. 

If I get to it, I will install Fedora Code 6 over the weekend and see how far I can get with that. XP never freezes on the system, even with 100% CPU load for several hours. :-k 

Greetings, kaz.

---

### Post by galileon on 2006-11-02
in edgy, smp is handled by the -generic kernel, try that one out...

---

### Post by the kaz on 2006-11-02
> **galileon said:**
> in edgy, smp is handled by the -generic kernel, try that one out...

Look above - I *started* with the -generic kernel, which froze on me. So far, only kernels (from ubuntu oder kernel.org, that doesn't matter) in which I disable SMP core work without freezes. 

Greetings, kaz.

---

### Post by ghepburn on 2006-11-03
I had a problem that seems similar to one that a number of poeple have described about on this thread and it may also have some bearing on some of the seemingly less related problems. I upgraded my Dell D620 from Dapper to Edgy (final release). This computer has an Intel Duo so in Dapper I had the SMP kernel so that I could use the second processor.

After the upgrade I noticed that the second processor was not showing up when I checked using KInfoCenter or by mousing over the new power manager. I then noticed that I was booting with the Linux-image-2.6.17-10-386. I understood that the Linux-image-2.6.17-10-generic was the one I should be using for SMP support, so I tried to boot with that as well--it had been installed but was not being used as the default kernel. It froze to a blinking cursor at the beginning of the boot process.

I booted up with the Linux-image-2.6.17-10-386 kernel, fired up adept and check the kernel packages out. I had both the Linux-image-2.6.17-10-386 and Linux-image-2.6.17-10-generic installed but when I checked the description of the generic image, I noticed this bit of information relating to a change in the way Ubuntu was going to deal with kernels:

[INDENT]"You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."[/INDENT]

I then noticed that the Linux-generic package was not installed. It appeared that the upgrade had installed the Linux-image-2.6.17-10-generic package when it actually should have installed the Linux-generic package in order to avoid potential problems. 

Since I was booted with the Linux-image-2.6.17-10-386 kernel, I was able to fix things up by uninstalling the Linux-image-2.6.17-10-generic package and installed the Linux-generic in its place.

I was then able to boot with the generic kernel and had the use of both processors. I also changed the sequence of the kernel listings in the grub file called 'menu.lst' so that the Linux-image-2.6.17-10-generic was at the top of the list. This allowed the generic kernel to boot by default.

Hope that helps some of you.

---

### Post by xp_newbie on 2006-11-03
kaz & cosmix, please attach here a copy of your /var/log/demsg file. Don't copy & paste it, just use the attach facility (paper clip icon next to the smiley icon), as to not clutter the message thread.

The demsg file can reveal a lot about the problems you're having.

Alex

---

### Post by galileon on 2006-11-04
> **the kaz said:**
> Look above - I *started* with the -generic kernel, which froze on me. So far, only kernels (from ubuntu oder kernel.org, that doesn't matter) in which I disable SMP core work without freezes. 

Greetings, kaz.

btw have you tried passing the magic words 'noapic nolapic' into your kernel parameters? it shud look like thus:

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro quiet splash noapic nolapic
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

---

### Post by onuca on 2006-11-04
Hi,

I am running dual boot Win XP & Edgy AMD-64 on Asus P5B Deluxe/Wifi, E6300 and Corsair DDR2 TWINX 2GB PC6400 of RAM. SATA2 HDD and PATA DVD. BTW RAM is definitely compatible with motherboard - according to both ASUS and Corsair.

Unfortunatelly I am getting random freezes in Ubuntu as well as DVD tends to dissapear - again randomly - JMicron issue?.

If Linux freezes than after rebooting to XP, windows also gets into troubles with JMB363 and cannot recognize JMicron as well - I have to restore system to revert to previous settings. 

I wonder though if that is not a faulty JMB363...

Any ideas?

---

### Post by clinteas on 2006-11-06
Hi,
 im writing this from a Core2Duo 6600 system running Kubuntu 6.10 with Kernel 2.6.17-10-generic,with a P5B-Deluxe-WiFi board,! SATA drive for boot and one for data(not in any RAID),a IDE DVD-Rom,and the notorious Marvell Yukon 88E8001 Eth controller,in a dual-boot with WinXP.
It took me 2 weeks to figure out,so I thought Id let the public know how I managed to get it running,and lightning-fast at that !
  1. Optical drive on IDE and JMicron controller:Many people reported problems with this,but the issue is resolved as of Edgy,so install from LiveCD went fine and fast.I booted into the new systen and got:
  2.Grub error 17 (with only the 1 SATA disk),or error 21 (with 2 disks).
Grub is the worst piece of software ever written,and I still dont know why the major distributions changed to that thing from lilo.Anyway,the bottom line is GRUB will not pick up the correct partition/drive settings from your BIOS,so e.g. my boot screen showed /dev/hda1 as root partition,when it should have read /dev/sda5.You have to know where you installed the root partition to,and then change the settings in the boot menu via the "e" command(as in edit).For my situation,I had to edit the "root (hdx,y)line to make it the fifth partition on the first disk,so it has to read (hd0,4).Enter brings you back to the boot screen,then go into the kernel line and make sure your root partition is correct,if not edit it as above.Hit "b" to boot what youve selected,that worked for me.
  3.Marvell Yukon Ethernet Controller : Dont try installing the sk98lin-module unless you want to edit header-files for a day ! It detected the WLAN and ETH0 interfaces just fine on my system,and assigned an IP via DHCP,worked out of the box.The secret is the "skge"module,make sure you have it loaded,if not,theres posts around discussing the issue.

Thats it,here I am enjoying....

Cheers,
Mike

---

### Post by pony-tail on 2006-11-06
> Grub is the worst piece of software ever written,and I still dont know why the major distributions changed to that thing from lilo.Anyway,the bottom line is GRUB will not pick up the correct partition/drive settings from your BIOS,so e.g. my boot screen showed /dev/hda1 as root
I am not sure that this is caused by grub . I have a similar issue with the onboard nVidia sata controller on my A64 - works fine in some other Distros (Gentoo / SLAMD64 / Debian 32bit stable ) completely mis-detects in K/Ubuntu and SuSE detects it as a sil3112 raid and cannot be installed . If it was grub I would think the error would be consistant across all Distros that use grub - I will have to try lilo and see if that fixes it - the big issue is that the Ubuntu installer detects  the first sata as sda on restart the installed os calls it sdc . I got around it by booting a Mepis disk (ubuntu live disk will not work with my X850XT pci-e card ) and editing /boot/grub/menu.list and /etc/fstab to correct the anomolies .

---

### Post by the kaz on 2006-11-07
> **xp_newbie said:**
> kaz & cosmix, please attach here a copy of your /var/log/demsg file. .

No problem - this one's from my most recent boot w/SMP, using the 2.6.19-rc2-mm2 kernel I compiled from vanilla sources. 

Greetings, kaz.

---

### Post by Necreia on 2006-11-08
I seem to be having this problem as well (Core 2 Duo freezes), but I was unable to determine what was wrong.

I've gotten random freezes (complete lock up) while trying to install all the following: 6.10 Ubuntu and Kubuntu 64 bit, 6.10 Ubuntu 32 bit, 6.06 Ubuntu 64 bit, and 6.06 Ubuntu 32 bit.

I've eventually (after trying enough times) have gotten both a 6.10 and a 6.06 Ubuntu installed.  But it'll freeze at random times.

Memory tests, video tests, and hard drive checks all come back clean.  Here are my system specs. 

Intel Core 2 Duo E6600 Conroe 2.4GHz LGA 775
DFI INFINITY 975X Socket T
eVGA 512-P2-N573-AR GeForce 7900GTO
pqi TURBO 240-Pin DDR2 SDRAM 667 (4 gig -- 4 x 1 gig chips)

I connect 2 hard drives to SATA and DVD-ROM to IDE.

---

### Post by the kaz on 2006-11-08
> **galileon said:**
> btw have you tried passing the magic words 'noapic nolapic' into your kernel parameters?

I tried that last night - and it seems to work so far, though I couldn't test it for more than 110 minutes yet. During this time, however, there were no freezes regardless of how much load the two cores had to cope with. 

Necreia, could you try whether this works on your platform, too?

Greetings, kaz.

---

### Post by Snocrash on 2006-11-08
I'm getting the same freeze problem. But my box is an older AthlonXP 2800+ with a Gig of ram and a GForce 5700 ultra.

If I remember correctly, it's a KT400 chipset and it has run all past versions of Ubuntu without any problems. As well as Gentoo, Slackware, and Fedora. So I'm pretty sure it's a problem with Edgy and not the box.

I did not have any problems until I installed the nvidia-glx module, although I did not run that long with the nv driver. Only a couple of hours.

I think I'm going to compile a new kernel from vanilla source and then build the nvidia driver and see if the problem goes away.

Any other ideas would be helpful.

Thanks,

-Sno

---

### Post by Necreia on 2006-11-08
> **the kaz said:**
> I tried that last night - and it seems to work so far, though I couldn't test it for more than 110 minutes yet. During this time, however, there were no freezes regardless of how much load the two cores had to cope with. 

Necreia, could you try whether this works on your platform, too?

Greetings, kaz.

Sure thing.  How do I pass that command? (just pop into terminal and type it?)

Also, is there a way to set this during the install process when booting from CD?  If so, I can test to see if this would resolve install issues (like I've been having).

---

### Post by galileon on 2006-11-08
when you turn on the computer, as soon as grub appears, press ESC until it gives the list of OS if its on automatic boot, or if its already on the list, press 'e' to edit the entry for the default OS...

look for the line where it says 

kernel /boot/vmlinuz...-generic... ... ... splash quiet

, etc, and add the magic words 'noapic nolapic' to the line, then press ESC, then 'b' to boot..

please read the screens carefully, they will tell you the exact instructions, because I can't reboot to try it right now...

---

### Post by Necreia on 2006-11-08
> **galileon said:**
> when you turn on the computer, as soon as grub appears, press ESC until it gives the list of OS if its on automatic boot, or if its already on the list, press 'e' to edit the entry for the default OS...

look for the line where it says 

kernel /boot/vmlinuz...-generic... ... ... splash quiet

, etc, and add the magic words 'noapic nolapic' to the line, then press ESC, then 'b' to boot..

please read the screens carefully, they will tell you the exact instructions, because I can't reboot to try it right now...

Great, I'll try that when I get home and post results.

Is there a way to append that flag to the CD-boot (like, if you were trying to install it for the first time, and can't append it through GRUB)?

---

### Post by galileon on 2006-11-08
look on the first screen that appears when the cd loads - it gives the option to modify kernel parameters...when you press the corresponding function key, it will give a line similar to the grub one...

btw, if it works well on the cd and hdd installation (when using grub), you can add it permanently to your grub configuration like thus:

sudo gedit /boot/grub/menu.lst

look for the entry for your default OS, and add the words to the kernel line...

---

### Post by Necreia on 2006-11-08
> **galileon said:**
> look on the first screen that appears when the cd loads - it gives the option to modify kernel parameters...when you press the corresponding function key, it will give a line similar to the grub one...

btw, if it works well on the cd and hdd installation (when using grub), you can add it permanently to your grub configuration like thus:

sudo gedit /boot/grub/menu.lst

look for the entry for your default OS, and add the words to the kernel line...

You have been most helpful.  Thank you.

I'll test the install-stuff tonight as well.

---

### Post by fazavon on 2006-11-08
i had the same issue with a P4 3.06 Hyper thread...

i just installed smp i686 and it works fine now

---

### Post by theyost on 2006-11-08
If your motherboard has integrated graphics but you are using an nVidia graphics card sometimes they don't play nice.  

[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated]("http://doc.gwos.org/index.php/Nvidia_Intel_Integrated")

Now the bad news...  If you follow this how-to and you are using a 64bit kernel it will solve your stability problems, but will also disable AGP and slow down your graphics.  Agpgart is  *inside* the 64bit kernel to address memory > 4GB.

[http://ubuntuforums.org/showthread.php?t=25080]("http://ubuntuforums.org/showthread.php?t=25080") (terrax's February 2nd, 2006 post)

Later today I am going to see if installing the smp-i686 kernel (which I think is 32 bit) will address the issue.  If not, I will try to compile my first custom kernel (wish me luck).

My thread tracking my specific problem:
[http://ubuntuforums.org/showthread.php?t=295133]("http://ubuntuforums.org/showthread.php?t=295133")

---

### Post by cormega on 2006-11-08
I've been having almost exactly the same problems as everybody else on this thread except for one thing. My edgy only seems to freeze when surfing the net (!) At first i thought it was a firefox bug so I switched to Opera but that had no effect, then I thought maybe the freeze was caused by the excessive content on some of the sites I was surfing because the bug seemed, at one point, only to occur on the same page. But I have dismissed that theory now as edgy froze several times just reading this page. It seems to be when the browser is loading a page, that the freeze usually occurs.
I installed edgy today, clean install, and have been having this problems since - but only when surfing the net.

I am running edgy on a Dell Inspiron 1705 :
 Intel® Core&#153; 2 Duo processor T7400 (4MB Cache/2.16GHz/667MHz FSB)
	
Memory 	2GB Shared Dual Channel DDR2 SDRAM at 533MHz
	
Video Card 	256MB NVIDIA® GeForce&#153; Go 7900 GS
	
Hard Drive 	120GB 5400RPM SATA Hard Drive 

I've tried to add the noapic nolapic commands to the grub file and haven't had a crash since, but since I added those - a lot of programs have been responding unusually slow. For instance when I am writing this post. i can type for about ten seconds before the text appears, and when i am scrolling down a webpage the scrolling movement is extremely "choppy" and sometimes it freezes on one point for several seconds so I am really looking for another solution here.

---

### Post by Necreia on 2006-11-08
Results with Edgy (64 bit):

Well, using the "noapic" flag I was unable to even start the install.  It would hang up right after loading the tan screen (right where the GUI usually appears).  It did this in both normal and safe graphic mode, as well as with and without the "nolapic" flag.  

Using just the "nolapic" flag didn't change anything.  It still freezes randomly during install.  Damn, I'm getting pretty close to giving up on Linux.

A note about the first problem.  The mouse was responsive the whole time, and when I hit the power button Ubuntu would do normal shutdown (flip to closedown screen and then eject disk).  Is there a way, from that tan screen that is doing nothing, that I can get some sort of debug output to try and figure out 'why' it isn't doing anything?

---

### Post by Necreia on 2006-11-08
Okay, I went into the BIOS and set "APIC Mode" to "Disabled".  It causes the same problem to occurr:  Right after the main loading screen goes, it just sits at a tan screen.

Hmmm.

---

### Post by drtvasudevan on 2006-11-08
> **Necreia said:**
> Results with Edgy (64 bit):

Is there a way, from that tan screen that is doing nothing, that I can get some sort of debug output to try and figure out 'why' it isn't doing anything?

i am not very sure but i think while installing you can hit alt F3 and it will show what is going on.
alt F1 to come back.

---

### Post by Necreia on 2006-11-08
> **drtvasudevan said:**
> i am not very sure but i think while installing you can hit alt F3 and it will show what is going on.
alt F1 to come back.

Okay, this works up until it switches to the GUI portion (screen turns tan).  At that time, I can only move the mouse, and no button combinations work at all.  The only thing I can do and can get any result, is to push the power button and have it shut down (through normal means).

Before that though, it seemed fine.

---

### Post by cosmix64 on 2006-11-09
Kaz, I've had no single freeze or other crash on that machine since replacing the memory with DIMMs 'compatible' with it. The machine has been rock solid, and very fast at that, with the 'standard' 2.6.17-10-generic kernel and  uptimes in excess of 2 days. 

It was memory in my case. This Asus board is unbelievably picky. You may want to check your components --- it might be a hardware problem/incompatibility that manifests itself only under specific runtime conditions that are triggered by the linux kernel.

Note that I'm using the 32bit kernel.

Good luck,

cosmix.

---

### Post by the kaz on 2006-11-16
> **cosmix64 said:**
> Kaz, I've had no single freeze or other crash on that machine since replacing the memory with DIMMs 'compatible' with it. 

So it seems we have had two different problems resulting in the same symptom. 8) -- Great to hear that your system runs fine now, too. As for myself, I've used the Core2Duo system under both XP and Ubuntu for about 48 hours straight each, with no freezes whatoever and no apparent performance dropoff from the "noapic nolapic" options under Ubuntu. Therefore, I'm inclinde to say the problem's fixed for me, too. :) 

ncreia, have you tried a text-mode based install of Ubuntu?

Greetings, kaz.

---

### Post by Pravus Pestis on 2006-11-18
I too have found that the problem is apparent in the generic smp aware kernels. I've been having a few random hangs a day, but have yet to have one after having flipped to the 386 non smp kernel. I tried the noapic fanciness with the generic kernel but to no avail. 

It looks as if I'm stuck with only half my processing power for a bit. As much as it pains me to hobble the machine, stable beats crashing hands down.

Cheers

---

### Post by Pravus Pestis on 2006-11-19
> **Pravus Pestis said:**
> I too have found that the problem is apparent in the generic smp aware kernels. I've been having a few random hangs a day, but have yet to have one after having flipped to the 386 non smp kernel. I tried the noapic fanciness with the generic kernel but to no avail. 

It looks as if I'm stuck with only half my processing power for a bit. As much as it pains me to hobble the machine, stable beats crashing hands down.

Cheers

BTW, still no crashes with the non smp kernel. Also, I'm running Kingmax ram which is fully supported by the board. I'm not into overclocking, so there wasn't much need to buy more expensive ram. 

I had tried flipping back to the generic kernel having uninstalled it and re-installed it, and crashed within 30 minutes of running it. Flipped back to the 386 kernel and have remained completely stable since. 

The 386 kernel is noticeably slower though. Hopefully someone can get to the bottom of this. Is there somewhere/someone I should be sending my syslog to?

Cheers

---

### Post by Crakie on 2006-11-19
I also have these freezes and like one poster above, they seem to occur when using the internet connection, browsing in particular.

I just added noapic nolapic acpi=off pci=noacpi to the bootparameters, but I cannot tell whether they have any effect.

---

### Post by Pravus Pestis on 2006-11-20
> **Crakie said:**
> I also have these freezes and like one poster above, they seem to occur when using the internet connection, browsing in particular.

I just added noapic nolapic acpi=off pci=noacpi to the bootparameters, but I cannot tell whether they have any effect.

Tried again with the apic/apci options set as well as disabling it at the bios level, but ran into the same problem overnight. I'm pretty damn sure I wasn't hitting the second proc at all as I was just downloading a few torrents. I'm beginning to wonder if it isn't the second proc that's a factor as opposed to accessing devices. It might simply be that the generic kernel has a slightly different set of code for supporting the JMicron ICH8R and I965 bits. 

Of course, I could be completely mistaken which would not surprise me in the least.

---

### Post by galileon on 2006-11-20
hi all,

if someone can boot into both kernels (even though the -generic crashes after some time), could you try to do a lsmod in each?

it would give you the list of modules loaded for each kernel, and by comparing them, you might be able to detect if one the driver modules is loaded/not loaded...

---

### Post by Pravus Pestis on 2006-11-20
> **galileon said:**
> hi all,

if someone can boot into both kernels (even though the -generic crashes after some time), could you try to do a lsmod in each?

it would give you the list of modules loaded for each kernel, and by comparing them, you might be able to detect if one the driver modules is loaded/not loaded...

One from each kernel. I'll attach my syslog once I crash in a few hours. 

Cheers

---

### Post by galileon on 2006-11-21
hmmm...the archive seems empty when im opening it... :(

---

### Post by Crakie on 2006-11-22
> **Crakie said:**
> I also have these freezes and like one poster above, they seem to occur when using the internet connection, browsing in particular.

I just added noapic nolapic acpi=off pci=noacpi to the bootparameters, but I cannot tell whether they have any effect.

Well, a couple of days later and so far so good. The system has been active all the time, downloading when I was away and normal use the rest of the time. Nothing is sure in life, but it certainly seems to help for me.

---

### Post by Morientes on 2006-11-27
Those things that you added to the kernel (noapic etc)..what do they do?

---

### Post by galileon on 2006-11-27
[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

---

### Post by deleriux on 2006-11-29
I am not actually using Ubuntu myself (fedora) however I have similar difficulties with random lockups.

I once caught a glimpse of a kernel panic dumping crash infomation to the screen and it seems to refer to a lot of IDE related calls, also most lockups for me occur when the disk is accessed.

Either way, I have been using the NOAPIC options as suggested above and that has had a lasting effect. So far after 3 days no crash - I normally get around 4 a day.

---

### Post by Morientes on 2006-11-30
I have noapic nolapic acpi=off pci=noacpi and I still get a freeze now and then. Also the other day I got something about a "bus error" and a "read only file system"...see this thread: [http://ubuntuforums.org/showthread.php?t=308103](http://ubuntuforums.org/showthread.php?t=308103) .

I hope a new kernel will soon be out or something and that it will solve the problems...

---

### Post by Necreia on 2006-12-19
I've been trying off and on, and still no success.  (I haven't tried text-based install yet)

I have a 6600 Core 2 Duo, and really want to use Ubuntu.  Is there anyone here with that processor and have had great success with a clean install?  If so, what motheboard are you using and I'll just buy that.  (ATX form factor)

---

### Post by dukeleto on 2006-12-22
I'm not sure whether this will help anyone, but I had random freezes on my core 2 duo 
dell laptop under edgy (64bit), until I appended "-notsc" to the kernel boot line under grub (if you search for notsc on the forums, you 'll see other posts about this), and since then it has  worked like a charm. It's also worth noting that the most recent kernels, i.e. those being tested in feisty at the moment, should not need this treatment. 
Regards,

Olivier

---

### Post by ambrosa on 2006-12-30
For NECREIA: my system is like yours: DFI Infinity 975X/G , E6600 , 2 GB RAM (2 x 1024 Corsair XMS DDR2 PC6400 800MHz), Nvidia 7900GT, no other PCI cards.
And I've the same problem also WITH OPENSUSE 10.2

During Ubuntu install, system freeze (with Edgy 6.10  32 and 64 bit). I cannot install Ubuntu 6.10 Edgy. It freeze when "Installing System" window reach about 10%. I've tried many times.
I can install Opensuse 10.2 (32 and 64 bit) correctly but after installation randomly system freeze (after 1 minutes or after many hour: totally random).

Perhaps I've found a solution.
For Opensuse 10.2 I've supposed that the problem is the kernel SMT scheduler that manage HyperThreading.
In the past I had big problems with SMT and HT CPUs (example: IBM xSeries server). With some mainboard/cpu sometimes SMT freeze system, sometimes not. Where there is the problem, I  disable SMT (recompiling kernel removing SMT option) and all is right. Doing this, my Opensuse 10.2 run for days without any problem. Only SMT is disabled: SMP is still enabled.
It's a very strange problem that affect only some hardware.
Intel Core 2 Duo (Conroe) CPUs HAVE NOT HYPERTHREADING technology so the scheduler SMT I suppose should be inactive.
But with SMT enabled I've problem. Disabling it with "noht", all works fine. SMT scheduler crazy ??????
I'm an Ubuntu new user. Can someone tell me if SMT is enabled in kernel configuration ?

With Ubuntu adding "notsc" (thanks DUKELETO) in kernel options (since loading livecd and then modifying /boot/grub/menu.lst after installation) is not the total solution: sometimes after installation the system crash. But I can do the installation correctly :-)
Adding "noht" also (disable SMT scheduler) I've no more crash.
My Ubuntu system is up since 20 hours without any problem.
My /boot/grub/menu.lst  :
-----------
(...omissis...)
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic notsc noht root=/dev/sda3 ro splash quiet
initrd          /boot/initrd.img-2.6.17-10-generic
(...omissis...)
-----------
If I remove "notsc" or "noht" after a while randomly my system freeze.

I've supposed that a problem can be dynamic CPU frequence switching (governor ondemand) but forcing 2400 MHz and removing "noht" the problem appears again.

I've found this TSC: [http://lwn.net/Articles/208632/](http://lwn.net/Articles/208632/)
In multiprocessor system TSC can create problem and in kernel 2.6.19 will be disabled by default.
And  freq. switching can be problematic with TSC and multiple CPUs
Mmmhhhhhhhhhhh now I try to force 2400 MHz removing powernowd during boot (it setup ondemand governor) and removing notsc ....

---

### Post by tqft on 2006-12-30
ok I have searched and found a kernel patch which is of not much use to me and not much in the way of documentation.

Is it no tsc, not sc  ?

What is tsc/sc?   Related to SCSI?

Thanks.

Right now I have a massive string of boot options which get my 2 cores running and a working optical drive, but I can't get 2nd optical drive up without borking the system.  If I could drop a lot of the the options I might get some more functionality back.
irqpoll all-generic-ide noapic nolapic ht=on

---

### Post by xtknight on 2006-12-30
Make sure you have DMA enabled on the JMicron controller.  Otherwise, any I/O operation will take up tons of CPU and cause freezing for up to 10 minutes at a time.  Check it before enabling it to see if that may have been the problem (use -d instead of -d1 to check it).  -d1 will enable DMA.

$ sudo hdparm -d1 /dev/hda
$ sudo hdparm -d1 /dev/hdb

etc...do it for all drives on the JMicron controller.  I believe it'll take effect immediately.  These freezes may be accompanied by errors like "lost some ticks due to interrupt/stuck driver" or "soft __irqlock" (something like that).  DMA will take them out of PIO mode.  Also enable the system monitor GNOME applet and watch for I/O activity (default dark green) during these freezes.  I've noticed during my freezes some things still work but windows get out of focus permanently.  Alt-tab seems to fix that after the freezing period is done.

tsc is the time stamp counter in the CPU.  It can get desynchronized among both cores of the CPU and may cause freezes and other time-related issues.

Try enabling the HPET counter in your BIOS, that may help.  I think it is used instead of TSC.

**Anyone who is having any problems with their Core 2 Duo, please post your complete dmesg!**  It'll immensely help in debugging the issue.

I would take it easy on the "irqpoll all-generic-ide noapic nolapic ht=on" etc, none of it did anything to help my JMicron problems.  But maybe you are experiencing other issues.  I haven't tried the ht option.

Updating your BIOS may fix broken BIOS irq routings which can cause trouble.  Also, you may need to blacklist pata_jmicron and use libata instead.  libata is a more stable module.  Details here: [http://www.ubuntuforums.org/showpost.php?p=1947596&postcount=262](http://www.ubuntuforums.org/showpost.php?p=1947596&postcount=262)

---

### Post by tqft on 2006-12-31
Both posts quite helpful.

the irq confused is really bugging me

My search skills seemed to have failed me before
a rather good list
[http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html)

I haven't tried the blacklist yet - but is setup for next reboot

---

### Post by Crakie on 2006-12-31
Well, the noapic nolapic acpi=off pci=noacpi worked for me. My system was up for weeks without a single crash. 

The strange thing is, I completely reinstalled yesterday and adding the parameters back into menu.lst was one of the first things I did. But now my mouse started responding with a delay. As usual, there was a ton of updates available right after the install, so I did those first before trying to remove the parameters. As it turns out, the updates removed them for me and even when using my system intensively, I haven't seen a crash. 

Problem solved? Not completely. I have a widget which among other things is supposed to show the clockfrequency of the CPUs. It's showing it wrong, which used to be the case in my previous install *without* the parameters in menu.lst.

I have an Abit AB9 Pro, with ICH8R chipset and JMicron controller.

---

### Post by ambrosa on 2006-12-31
Forget my post.
The problem is not "notsc noht". Sorry :cry: 

Yes, after using "notsc noht" I'm been able to install Ubuntu Edgy without problem and the system is stable.
But just for fun I've reinstalled Ubuntu from scratch (always using "notsc noht") three times.
I want be sure about my solution.
The first and second time installation was ok. The third time it freeze around 15%.
SGRUNT !!!!
Then I've tried another way: disable dynamic frequence switching.
So, I've start livecd without any extra parameters (no "notsc noht").
After livecd boot I've disable powernowd: it sets "ondemand" governor and my CPU (E6600) switch dynamically from 1.6 GHz to 2.4 GHz (you can see this adding the "CPU Frequency scaling monitor" applet to the panel).

I've opened a terminal and:
  $ sudo /etc/init.d/powernowd stop

Now the governor is "perfomance" and CPU is always to 2.4 GHz without any switching.
I've done 3 installation with powernowd stopped: all ok without any problem.

Then after the third installation before rebooting, I've mounted my installation partition and I've modified the original /etc/init.d/powernowd installed on my harddisk:

------------ original ---------------------
use_ondemand() {
        for x in /sys/devices/system/cpu/*; do
            echo -n ondemand >$x/cpufreq/scaling_governor;
---------------------------------------------

------------- modified ------------------
use_ondemand() {
        for x in /sys/devices/system/cpu/*; do
            #echo -n ondemand >$x/cpufreq/scaling_governor;
            echo -n performance > $x/cpufreq/scaling_governor;
-----------------------------------------------

So during harddisk boot powernowd starts but it set "performance" governor instead of "ondemand"

Well, after 4 hours there is no any problem at all.
Ubuntu Edgy run very fine.

Do not Core 2 Duo+Linux Kernel like frequency switching ?

---

### Post by tqft on 2006-12-31
ian@tqft:~$ more /proc/cmdline
root=/dev/hda1 ro irqpoll all-generic-ide noapic nolapic ht=on notsc


The notsc option appears to have borked /dev/hdb - main optical drive - responds to commands but only very slowly - 3 to 5 minutes to eject cd.  I also am getting some laggy weirdness.

Next reboot notsc will be removed
I have tried removing various pieces of irqpoll all-generic-ide noapic nolapic ht=on but all seem to give me grief.

My Bios is latest - as at 24 Nov 2006 for Asus P5lD2-VM motherboard.

---

### Post by ambrosa on 2007-01-01
After 1 day of hard work and after again 2 installation from scratch (32 bit version, till now I've installed the 64 bit version) I've NO PROBLEM at all.

So, for me, forcing "performance" governor ( equal to stopping powernowd ) is the correct solution.
My pc is running very very fine.

I'm very happy O:)

I hope this tips will be useful to Necreia, that has the same mobo and cpu.

---

### Post by cheruiyot on 2007-01-04
Hey there! I am having the same problem running ubuntu on Core 2 Duo E6300 1.86ghz - Skt775 on a ASUS P5V-VM DH motherboard . I think the problem is to do SMP. I installed Dapper which work fine until I installed SMP the it kept freezing the same thing happen on all other distro that are SMP aware...
My Specs are
Core 2 Duo E6300 1.86ghz - Skt775
ASUS P5V-VM DH motherboard

Anyone got the same problem?

---

### Post by ambrosa on 2007-04-21
I've just downloaded the new UBUNTU 7.04 Feisty and I've tried to install it from scratch.
Same problem like 6.10: during install the system crash.
I've tried 5 times with different boot kernel parameters without any success.
So I've tried my solution as explained some post ago: **DISABLE POWERNOWD**.

Well, installation was ok without any problem and the system is very stable (I've totally disable powernowd service after installation).

Try to disable powernowd (the problem is well known: dual core cpu + smp kernel + frequency switching there are MANY problems).

---

### Post by ambrosa on 2007-04-21
Update.

If you want to see how is scaling your cpu, add to panel the "CPU frequency scaling monitor" applet.
An E6600 cpu can have two freq: 1.60 GHz and 2.40 GHz
"ondemand" governor set cpu at lower speed (1.60 GHz). When the system is under heavy load, "ondemand" increases cpu freq (2.40 Ghz) and there is an high probability that the system crash (due to SMP code).

For disabling "ondemand" governor there are 2 mandatory steps:

1)
After installation I've disable (using menù SYSTEM / ADMINISTRATION / SERVICES) "powernowd" service, but this is NOT ENOUGH !
Without powernowd the default scaling_governor is "ondemand" (switch cpu freq. up and down), and this is the problem.
It's better to leave service "powernowd" enabled and then to modify /etc/init.d/powernowd as described in my previous post.

With a text editor open (as root with "sudo") /etc/init.d/powernowd and change "ondemand" woth "performance" (CPU always at max freq).

------------ original ---------------------
use_ondemand() {
     for x in /sys/devices/system/cpu/*; do
     echo -n [COLOR="Red"]ondemand[/COLOR] >$x/cpufreq/scaling_governor;
---------------------------------------------

------------- modified ------------------
use_ondemand() {
     for x in /sys/devices/system/cpu/*; do
     echo -n [COLOR="Lime"]performance[/COLOR] > $x/cpufreq/scaling_governor;
-----------------------------------------------


2)
Gnome-power-manager also sets "ondemand" governor.
Launch a terminal, run "gconf-editor" (as normal user), go in APPS -> GNOME-POWER-MANAGER and change the key "cpufreq_ac_policy" from *ondemand* to *perfomance*


The cpu now is always at 2.40 Ghz (max freq.) and system is very stable, without crash.

---

### Post by Necreia on 2007-04-21
Ambrosa - Your information helped me with both Edgy AND Feisty.

I am now a Linux user (hurray!)  Thanks for ALL your help!  Been running over 24 hours now without 1 crash!

Edit::  What I did (which is slightly different) was to actually REMOVE powernowd (sudo apt-get remove powernowd), instead of tweaking it.  It's stopped the crashing, but was this a good thing to do?

---

### Post by spludge on 2007-04-25
For those with the Foxconn P975AA, if you are not using any IDE devices, disable the JMicro IDE controller as well as ACPI until after Ubuntu has been loaded.

---

### Post by HunGable on 2007-05-23
HI,

I'm very new to Linux, how can I set the noacpi boot parameter? I have a live CD, loads up the selection screen where i can choose to install bla bla, when i go for the install, i always freeze after a little while! I just bought a Conroe with a Gigabyte 965G-DS3, i only have SATA devices. I have read here that addig nolapic noapic acpi=off helps, but how am i supposed to do that? 

Thanks!

EDIT: Sorry, I have read the whole topic now I can see where I can modify the line for the nolacip bla bla things, but they didn't help, I always hang up at the beginning of the installation... how can i change this POWEROWD thing on a clean system, before installation, only having the menu of the install CD?:) 

Thanks a lot!

---

### Post by tqft on 2007-05-23
"addig nolapic noapic acpi=off helps, but how am i supposed to do that? "
if you get a working install - you need to modify /boot/grub/menu.lst

 sudo gedit /boot/grub/menu.lst

and change the line [may not be exactly the same]

kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda1  ro quiet splash 

to

kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda1  ro quiet splash nolapic noapic acpi=off

If you don't have an installed file system:

when the machine boots and you see the grub menu come up enter the grub menu - if it says booting in so many secs hit the esc key and it will take you to the grub menu).

Highlight the entry you want to edit, press "e"  [for edit]
Highlight the line
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda1  ro quiet splash 
press "e" again
type the boot parameters in
hit <enter>
press "b" [for boot]

Good luck

---

### Post by szr4321 on 2007-08-02
I'm running Ubuntu Gutsy amd64 with kernel 2.6.22-9-generic on an Asus P5B-Plus board and an Intel Quad Core Q6600 CPU.

After installing Ubuntu using the nosplash noacpi noapic kernel options, I experienced random freezes when copying large files over the network. There were no error messages in syslog.

For me the solution was to *disable the onboard LAN chipset* (Attansic L1 chipset) in the BIOS and use an old Realtek PCI network card instead. There even are some Linux drivers on the CD that comes with the mainboard, but I didn't bother to install them.

There also is a BIOS upgrade available on the Asus support site. It can even be installed off an USB stick directly from the EZ BIOS update utility.

---

### Post by szr4321 on 2008-01-26
> **szr4321 said:**
> For me the solution was to *disable the onboard LAN chipset* (Attansic L1 chipset) in the BIOS and use an old Realtek PCI network card instead.
[Here]("http://ubuntuforums.org/showthread.php?t=498778") and [there]("http://lkml.org/lkml/2007/6/21/435") seem to be more details on this issue (and the problem matches perfectly since I have 4 GB of RAM as well).

---

### Post by ambrosa on 2008-04-25
> **ambrosa said:**
> Forget my post.
The problem is not "notsc noht". Sorry :cry: 

Yes, after using "notsc noht" I'm been able to install Ubuntu Edgy without problem and the system is stable.
But just for fun I've reinstalled Ubuntu from scratch (always using "notsc noht") three times.
I want be sure about my solution.
The first and second time installation was ok. The third time it freeze around 15%.
SGRUNT !!!!
Then I've tried another way: disable dynamic frequence switching.
So, I've start livecd without any extra parameters (no "notsc noht").
After livecd boot I've disable powernowd: it sets "ondemand" governor and my CPU (E6600) switch dynamically from 1.6 GHz to 2.4 GHz (you can see this adding the "CPU Frequency scaling monitor" applet to the panel).

I've opened a terminal and:
  $ sudo /etc/init.d/powernowd stop

Now the governor is "perfomance" and CPU is always to 2.4 GHz without any switching.
I've done 3 installation with powernowd stopped: all ok without any problem.

Then after the third installation before rebooting, I've mounted my installation partition and I've modified the original /etc/init.d/powernowd installed on my harddisk:

------------ original ---------------------
use_ondemand() {
        for x in /sys/devices/system/cpu/*; do
            echo -n ondemand >$x/cpufreq/scaling_governor;
---------------------------------------------

------------- modified ------------------
use_ondemand() {
        for x in /sys/devices/system/cpu/*; do
            #echo -n ondemand >$x/cpufreq/scaling_governor;
            echo -n performance > $x/cpufreq/scaling_governor;
-----------------------------------------------

So during harddisk boot powernowd starts but it set "performance" governor instead of "ondemand"

Well, after 4 hours there is no any problem at all.
Ubuntu Edgy run very fine.

Do not Core 2 Duo+Linux Kernel like frequency switching ?

Good news !
I've just installed Ubuntu 8.04
Problem is disappeard and now frequency switching works fine.
CPU now switch 1.60 GHz <-> 2.40 Ghz without any problem.

---

### Post by plasmafusion on 2008-04-30
i've been using debian etch for ages since i could never get ubuntu to work on my setup (e6600, foxconn board, 2gd ram) and even the latest 8.04 versions of xubuntu and ubuntu froze on boot.
got xubuntu installed and running by passing the "noapic nolapic acpi=off pci=noacpi" parameters to the kernel.
will try ubuntu later today.
this thread has been a great help so thanks to all who have contributed :)

**EDIT**
ubuntu 8.04 now installs ok but only works correctly with the nv drivers. the official nvidia drivers crash x (both the version installed through ubuntu & the version available from the official nvidia site) so no compiz :(
no make matters worse my soundcard (onboard realtek) crashes and goes into a strange loop which means i have to restart the system. i'm buying a cheap soundblaster online so will try that...
anyone got any ideas? maybe i could leave out the "pci=noacpi" parameter?

---

