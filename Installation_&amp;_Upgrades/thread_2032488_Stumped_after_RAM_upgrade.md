---
title: "Stumped after RAM upgrade"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by Zander21510 on 2012-07-24
Okay, so I have been having some problems with a recent upGrade I did on an older computer I'm using as a kind of file server...anyways I'm baffled and getting quite annoyed at all the problems I'm having that seem to have just appeared out of thin air.

Motherboard specs here: [http://h10025.www1.hp.com/ewfrf/wc/d...name=c00683218](http://h10025.www1.hp.com/ewfrf/wc/d...name=c00683218)

Ubuntu 12.04 x64 dual boot with Windows 7 Ultimate x32
Integrated Nvidia 6150le (see mobo specs)
IDE hard drives
AMD Athlon x2 3800+ dual core @2.0ghz
Railink rt2561 WLAN card

Upgrade:
Before: 1.75 GB total of different speed and size hodge podge ****** ram; pc2100

After: 3GB pc3200 3x1gb (got four sticks, one was DOA so sending it for exchange)

For the record beforehand ubuntu and windows were both installed updated and tweaked with no major problems and were fully working before the switch

That was the only change. First I booted into Ubuntu, and it was like pissing its pants...it seemed to boot and logged in fine but apps started crashing I couldn't get anything to open and my network cards disappeared both Ethernet and WLAN. Ok, weird, I guess I will just reinstall.

Also, I've never had a significant problem installing from The normal desktop iso on USB...I had to be connected to the Internet to download extra stuff to get my nvidia graphics working but other than that it installs with no problem.

This time though, I pop in my USB, boot and I get the black screen. It completely booted but no x server. I tried all the different switches even burned to a cd to try that way, nothing. So I tried the alternate ISo install. Got that to install finally, booted, same black screen! Had to goto fail safe X, try a few times because it kept freezing, and finally got to the desktop. I added the x-updates ppa as I have to to get gnome 3d to work correctly, and ran the general update. Not only do I find out as I'm waiting for everything to download and install that the nvidia driver that usually installs and allows me to use unity 2d was never activated, the damn update fails and one package breaks and now I have to start over again....

Here's the kicker: through all of this, before during and after, windows 7 booted like nothing happened. It just ran faster from the ram as I expected. No weird graphics or errors or anything. It's completely baffling....as I thought if anything would blow up it would be windows...

So I ask...what the hell is going on??? Is there some relationship between my graphics card and the RAM? I was under the impression that there was 64mb of graphics memory separate from the physical ram. And as most branded mobos are I can't do **** in the bios...so what am I supposed to do? Just fight Ubuntu until I can get it to play nice? Even the installer acts differently now with the upgrade. It just doesn't make any sense to me

Please she'd some light? Thanks.

Edit: ok read a little more on the 6150le...it was a piece of garbage...but I don't care cuz I'm not playing videos or games with it...it gets 64mb of shared memory from the ram...great so why does faster ram make it unusable with Ubuntu?

---

### Post by dino99 on 2012-07-24
i've read your comments but still dont know which ubuntu is used and if its a 32 or 64 bits installation  :confused:

as you are using 3 ram sticks over a 4 banks, maybe your mobo cant works  with incomplete dual banks (2 or 4, but not 1 or 3), so try with only 2 ram sticks following the mobo doc to know the good order to plug in the ram sticks. And check the ram detection into the bios (default ram settings, auto detection, not overclocked)

---

### Post by UltimateCat on 2012-07-24
By no means am I the expert here but I can tell you what I've learned and perhaps it may assist you-;)

Video adapters (graphics cards too) rely on their own onboard memory that they use to start video images while processing.  Systems with integrated cards use the universal memory architecture feature to share main systems memory.  Memory on the card or memory borrowed from the system performs the same task.

The amount of memory; resolution and color depth is based on a mathematical equation.  Like I said before I'm not the expert as I'm still learning but it is possible that the RAM and your graphics card might not be getting along. There may be conflict-

The chipset is like the engine in your car and represents the drive train and chassis. It's the frame, suspension, steering wheels. tires, transmission, drive shaft and brakes.  The chipset represents the connection between the processor and everything else.  The processor can't talk to the adapter boards, devices, memory and so on w/o going thru it.  It's like the spinal cord and the central nervous system.

This book has taught me a great deal and this man is extreamly intelligent when it has anything to do with a computer system.

"Upgrading & Repairing PC's"
By: Scott Mueller-

Other than what I've typed you the only other thing I can think of is to ask a Computer Tech.  I was able to get help from one at Best Buy last week.

And, you can research RAM on Google 
[http://www.howstuffworks.com/ram.htm](http://www.howstuffworks.com/ram.htm)
[http://searchmobilecomputing.techtarget.com/definition/RAM](http://searchmobilecomputing.techtarget.com/definition/RAM)



If your using an older computer it could be that the power supply can not handle the amount of new RAM-  But I'm not writing this in stone.

BIO s ride on a chip and the chip has instructions that provides an interface between video/graphic and software running.

---

### Post by Zander21510 on 2012-07-24
So I've done a lot of testing and tried hard to get something to install...i just can't get anything to work.

Turns out having just 2 ram sticks in (enabling dual channel) seems to make it act better, it can actually get to X most of the time...but I keep getting

failed to set mode on [crtc:6]

at various times, sometimes before the boot CD/USB can even boot, sometimes I'll get as far as the installation starts copying files and it will crash to that error.

also sometimes it won't boot, the kernel will panic before it loads up X.

I've tried 32 bit, 64 bit, xubuntu, even Fedora. All failed in similar ways.

And almost like it's making fun of me, Windows 7 sits behaving perfectly. Boots fine, even reinstalled with zero errors.

So what can I do??

---

### Post by hells sponge on 2012-07-25
I am currently having the same problem with my ubuntu install. Since i last ran linux successfully, i have upgraded my graphics card and completely replaced my RAM.

I was able to get wubi installed by using some weird option in the advanced options... i think it was like acpi mode or something. hope this gets figured out before i use my new windows installation enough to get attached to it
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Zander21510 on 2012-07-27
So an update: I eventually was able to, with the "nomodeset" switch, get the thing to boot and stay going long enough to complete a full install of Ubuntu 12.04 x64. As soon as it booted up, I was able to get the newest nvidia drivers installed from the x-updates ppa and once that was done I was able to do a full update. One package broke during install and I had to deal with that but once it was dealt with it seemed to act OK. Still a little finiky and only able to work with 2 ram sticks in. I tried putting the third in and booting but no dice, random errors and crashes.

So then Windows decided to blow up and got some BSODs during windows update and it broke...

After lots of reading and because most issues seemed to appear related to the graphics...I broke down and just bought a standalone graphics card.

Got a really good deal on a GT-240 on ebay...only 20 bucks...hopefully it works out OK.

So I guess moral of the story is DO NOT use PC3200 with the 6150LE integrated graphics...

---

### Post by efflandt on 2012-07-27
Not sure if some of the AMD cpu's are particular about RAM.  Back in 2004 with an early Athlon64 3200+ (2 GHz) I got (2) 512 MB PC3200 sticks on sale at Frys and had problems.  memtest86+ showed errors.  OCZ sent me different PC3200 replacement RAM that they guaranteed would work, and it did.

Years later when I upgraded it with (2) 1 GB PNY PC3200 sticks, that worked without a hitch.  It still has 64-bit 10.04, but 64-bit 12.04 live/install iso on USB boots on it fine with legacy ATI X1300 video.

---

