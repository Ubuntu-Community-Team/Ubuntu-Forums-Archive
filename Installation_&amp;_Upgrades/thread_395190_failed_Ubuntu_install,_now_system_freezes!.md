---
title: "failed Ubuntu install, now system freezes!"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by luigi6699 on 2007-03-27
Hello all - my first post to this forum!

I've been using Ubuntu 6.x at work for awhile now, and here i thought it would be cool to try out the new beta on my home system, as a dual boot.  I burned (and verified) the disk, and booted to it.  Started the installer OK, and everything seemed to work perfectly, until it tried to load the kernel - which failed.  Once modprobe failed, job control was turned off, and I was SOL.

OK, I thought, no biggie - I'll just install 6.10 for now.  Nope!  Same problem - and a quick  glance around google showed that I wasn't the only 965 chipset owner with a headache.  I don't have much patience with my home system (it's there for fun, not for work!), so I decided to give up until feisty final comes out.  

Well, whaddaya know - now WinXP hangs.  It seems related to the amount of data sent to the video card; ie loading up Counterstrike Source will hang the system almost right away, while browsing the web gets me probably 2 minutes of hang-free time.  Bear in mind, this is a system used EXCLUSIVELY for gaming.  Literally nothing installed except AVG, firefox, counterstrike, second life, and my drivers.

Here are the troubleshooting steps I took, in no particular order:

- check component temperatures/manually set all fans to max/add a room fan pointing into the case - no difference

- underclock the CPU, up the voltage on RAM, CPU and FSB - no difference

- try with only one stick of RAM (tried different sticks and different slots too) - no difference

- Replace the video card (changed bus too, from PCIe to PCI) - no difference

- change the hard drive (and bus from SATA to ATA) - no difference

- reinstalled Windows - installer runs fine, but once the system is up and running... no difference

- booted Ultimate Boot CD:
    - individually tested both hard drives with manufacturer utilities
    - ran memtest for over 6 hours without errors
    - ran CPU burn-in for 5 minutes without errors
    - ran Merseine Prime test for an hour without errors

To my mind, the only component left is the motherboard.  But why would the motherboard crash in windows, but not in the installer or any of the UBCD tools?  Heavy load to the CPU/RAM seems to be no problem, so long as the graphics mode is VGA.  But the video card isn't the problem - I still get freezing when I replace it!  

So here's the solution I've come to - something in my failed Ubuntu install messed with my PCI bus (or perhaps with hdparm on my HDDs).  Once a certain amount of information is passed over that bus, I get a crash.  But why on earth would Ubuntu touch my bus?

Anyone care to lend an opinion on my diagnosis?  Better still, anyone have any ideas on a test I could do to confirm it?  Even better - does anyone have an alternate theory?  This is a system that worked brilliantly under high load for 3 months, and is now crappy after a failed Ubuntu install.

Thanks!

---- My system ---
Intel Core 2 duo e6400
Gigabyte ga-965p-ds3
2gb Wintec RAM in 512MB sticks
WD 80gb SATA HD
Seagate 80gb ATA HD
ATI X1950XTX 256mb video card
Hiper 580W PSU

---

### Post by buba on 2007-03-29
Hello

I told myself that I will not buy a new computer because of startup glitches hardware and software. So I waited for a while and bought Gigabyte 965p-ds3 rev.3.3 motherboard. 

And here is where the fun begun.

The damn thing didn't even wanted to start at the beginning. I couldn't boot it. I had to place ram in different slot. And after a while it started working in all slots. ?!?

Then I couldn't install Ubuntu because of kernel problem with jmicron thing. Now daily snapshot sort of works. At least it boots. But when I try to upgrade feisty my comp freezes all the time. In desktop mode I get a signal "network disconnected" like I would unplug the cable. In recovery mode, in the middle of update process it starts displaying errors that there is a problem with network hardware and my network hangs. The third thing I noticed is that the cooler on graphic card gets really really hot. I can't touch the card, but when I'm in windows it gets to approximate 40°C so I can hold it with out problem. 

Like I said graphic card is ok in windows. But the problem with network exist in windows too only it doesn't hang that often. I downloaded 1GB of data and it hang only twice in 24 hour period. But in Ubuntu it hangs after a few minutes.

Now I don't know if this is hardware problem or problem with drivers. The graphic card seems to me like the driver problem, but who knows. 

You cold try disabling network in bios and try using PCI ethernet card, and see if it helps. That is what I'm gonna do when I get home from work.

Good luck


---- My system ---
Intel Core 2 duo e6300
Gigabyte ga-965p-ds3 rev3.3
1GB KINGMAX RAM
Seagate 320GB SATA HD
NVIDIA 7600GT SilentPipe2 256mb video card

---

### Post by Ubuntiac on 2007-04-16
I seem to have the same thing.

I just upgraded (with dist-upgrade) from Edgy. Terminal seemed to be saying everything was fine until right near the very end when it kept saying that this one folder was missing again and again about 6 times. At the end of the upgrade I restarted and Feisty seems to work fine except for that it keeps freezing. If I leave it alone it goes for a long time no problems. The more I use it the faster it freezes.

The wierd thing is that the *instant* it freezes the Caps Lock light on my keyboard (M$ Multimedia 1.0A) starts blinking on and off.

Even if anyone could suggest where to find the logs from the dist-upgrade I'm sure it could shed some light...

I'm on:

Intel Pentium IV
ATI Radeon 9600
2 x slots of 512mb sdram
A recent, but cheap ASRock motherboard
A seagate baracuda 30gig drive
A seagate baracuda 200gig drive (where ubuntu is running from)
A Maxtor Diamondmax 80 gig drive

Running:
Feisty Beta
Using the ATI driver (not fglrx)

---

### Post by buba on 2007-04-21
Finally!

I got it working with different NIC with Feisty final version.

The onboard device (lspci gave this *Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)* and manual says *Marvell 88E8056*) didn't work it kept disconnecting and sometimes the computer rebooted (powered off) in the middle of work. This happened approximately 5 min after start. It even happened in the middle of installation process. The same thing was with Debian 4. Then when I rebooted into Windows the computer friezed a couple of times but there was no network disconnect. 

But after disabling the onboard NIC (Marvell) in BIOS and plugging in old PCI network card I was able to install Feisty and use it for 2 days now without any problems.

So I was wondering does anyone else have this problem with Marvell on Gigabyte 965P-DS3 rev3.3 or is it just my brand new mother board fu**** up!

Nice to see Feisty running at last though.

@Ubuntiac
Can you give output of command "lspci" that we can see if you have the same network card as I do. You can try it my way and see if it helps.
Good luck

---

### Post by shirsch on 2007-04-21
I'm trying to install Feisty on an ASUS P5B Deluxe motherboard (Core Duo E6600, Intel 965 chipset, Marvell ethernet).  For some reason, although Edgy had problems at all with the ethernet chips, Feisty just refuses to cooperate and I have no networking.

Certainly didn't expect this to regress.  Anyone figured a workaround?

---

### Post by twin_cylinder on 2007-04-23
You are not the only one. I have the exact same version, Gigabyte 965P-DS3 rev3.3!!!!
NIC would not work. So, I disabled it in the BIOS. Now using a 3com NIC.
 But I cannot run feisty at all. It goes through the installation fine. But modprobe dies with a page fault upon initial reboot. I tried both Feisty server 64 bit and 32bit. I'm going to try edge install then upgrade to feisty. I hope it works. I'm very close to replacing the MB. Anyone have an recommendation on a replacement MB? 


> **buba said:**
> Finally!

I got it working with different NIC with Feisty final version.

The onboard device (lspci gave this *Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)* and manual says *Marvell 88E8056*) didn't work it kept disconnecting and sometimes the computer rebooted (powered off) in the middle of work. This happened approximately 5 min after start. It even happened in the middle of installation process. The same thing was with Debian 4. Then when I rebooted into Windows the computer friezed a couple of times but there was no network disconnect. 

But after disabling the onboard NIC (Marvell) in BIOS and plugging in old PCI network card I was able to install Feisty and use it for 2 days now without any problems.

So I was wondering does anyone else have this problem with Marvell on Gigabyte 965P-DS3 rev3.3 or is it just my brand new mother board fu**** up!

Nice to see Feisty running at last though.

@Ubuntiac
Can you give output of command "lspci" that we can see if you have the same network card as I do. You can try it my way and see if it helps.
Good luck

---

### Post by buba on 2007-05-02
Hi there.

I'm not having any more problems with Feisty and Gigabyte motherboard. All I did was update BIOS to version F10 and there was a option in BIOS I had to disable to get my computer working. It was *HPET Support * - something for Vista operating system _[Wiki]("http://en.wikipedia.org/wiki/High_Precision_Event_Timer")_.
Other than that I didn't changed nothing except disabled the on-board Ethernet controller as I said above.

You could try that and there is a new bios on Gigabyte support site F11B beta. 

Do not give up. If it is working for me it should work for you too.

---

### Post by cocopop on 2007-05-02
> **luigi6699 said:**
> Hello all - my first post to this forum!
-snip-
Well, whaddaya know - now WinXP hangs.  It seems related to the amount of data sent to the video card; ie loading up Counterstrike Source will hang the system almost right away, while browsing the web gets me probably 2 minutes of hang-free time.  Bear in mind, this is a system used EXCLUSIVELY for gaming.  Literally nothing installed except AVG, firefox, counterstrike, second life, and my drivers. 


I got the same motherboard (Gigabyte DS3 rev 3.3 F10) and same problem as well. Whenever I went into a kubuntu session, subsequent Windows XP sessions will suffer from network card problems. However this works for me:

   - Disconnect PC power cord.
   - press "power" button on PC to discharge electricity in PC.
   - Reconnect power and Windows boots up fine with absolutely no issue with network card, untill the next time I log in to kubuntu again...

Also thanks to this thread, at least I know I am not the only one with the problem (was considering returning the motherboard). I don't have a spare network card around but I mainly use windows so should be fine. Its a pity becasuse in kubuntu I already went thru the trouble of installing beryl (even with the flaky LAN) and its awesome.. 

This does not fix the problem in ubuntu/kubuntu, but it fixed windows xp. hope this works for you too...

---

### Post by cocopop on 2007-05-03
I have my problem resolved! It was caused by bad driver (sky2) for  the marvell on board NIC, we need to use the driver <sk98lin> for this NIC for it to work properly, as reported here:

  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104929](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104929)


Here's exactly what I did that worked for me:
==================================
[LIST]
make a simlink in /usr/src from linux-headers-<your linux version> to linux (sudo ln -s /usr/src/linux-headers-`uname -r`  /usr/src/linux). Not sure if this step is necesarry, but  did it anyway.
[/LIST]

[LIST]
download the driver as described here:
   [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104929](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104929)
  
   or go to the download page directly:
   [http://www.marvell.com/drivers/search.do](http://www.marvell.com/drivers/search.do)
[/LIST]

[LIST]
Unpack the driver and change into that directory and run install.sh as root - at the prompt, enter option '1' = installation  -> '2' = deactivate old module

    * I am not sure if this only affected me, but I got an "(" unexpected error when executing install.sh. I have to change the first line of the script from #!/bin/sh to #!/bin/bash. Then it executed fine..
      (I have kubuntu 7.0.4).
[/LIST]

[LIST]
Maybe it is a newer version driver that I downloaded, I don't have to manually remove the old module (sky2) and load (sk98lin), as described in many other threads. I just choose "2" = deactivate old module as described in the previous step, and it took care of everything.
[/LIST]

[LIST]
power down PC, remove power cord from PC, and discharge  electricity by switching on PC with power cord remain disconnected.  Reconnect power  and boot up PC. I have no issue whatsoever with the on board NIC now with either kubuntu or XP. Tried downloading very large file in kubuntu, works perfect now :)
[/LIST]

---

### Post by Rohan on 2007-05-29
Has anyone been able to get Feisty 64 to boot? I'm on F10, disabled HPET, and the onboard ethernet. When I go into the recovery mode it detects the chipset as 965G and just hangs.

---

