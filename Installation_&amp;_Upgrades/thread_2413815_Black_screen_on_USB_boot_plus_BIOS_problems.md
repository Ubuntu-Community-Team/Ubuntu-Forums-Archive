---
title: "Black screen on USB boot plus BIOS problems"
date: 2019-03-02
forum: Installation &amp; Upgrades
---

### Post by unclecomrade on 2019-03-02
Hello there!

I have an Acer laptop from 2012-2013 era (Aspire V5-571G). It has been confirmed to run Linux, until...

Well, I ran into a problem booting off of a USB flash drive. The problem is that trying to boot ANY distro ends up with a black screen. No output, no blinking cursors, only a black screen.

After goofing around a lot with different flash drives and software I found out that my BIOS reads as UEFI by Windows 10 (OS that is currently installed). But the problem is... it's NOT a UEFI BIOS!

I have no idea how that happend, but, at some point, Windows did something with my BIOS rendering it incapable of booting any live-cd except Windows ones.

And more of a problem - I am not able to change any BIOS settings as they doesn't show up at all. And by settings I mean selection of BIOS mode (Legacy or UEFI). Yeah, pretty darn... unpleasant, to speak mildly.

Please, help me. I have no idea what to do now. I've tried everything other than updating BIOS. And the only reason I didn't try it is an unholy mess that Acer BIOS choice on their website is. The options they offer are completely meaningless as the version labels are all messed up and I can't understand what I am supposed to choose and I don't want to turn my laptop into a brick.

**EDIT: **Oh, and, by the way, everything boots on another PC, so it's not me who's doing flash drives wrong, I guess.

---

### Post by kc1di on 2019-03-02
Hello unclecomrade  and Welcome to Ubuntu Forums,

Often times it's actually the graphic card that turns out to be the problem Do you know what graphics card is being used in that machine? 
You may have to append the boot line with nomodeset.  A couple other things that could be causing problems.  Make sure secure boot is turned off and that fast boot is also off.  
This[ Ask Ubuntu]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu") thread should help with the nomodeset.
Just looked it up and at least some model of that era had Nvidia Graphic chip set and would deffinately need the nomodeset in order to boot to a desktop and after install will need the proper Nvidia driver installed from the driver manager.

---

### Post by unclecomrade on 2019-03-02
> **kc1di said:**
> Hello unclecomrade  and Welcome to Ubuntu Forums,

Often times it's actually the graphic card that turns out to be the problem Do you know what graphics card is being used in that machine? 
You may have to append the boot line with nomodeset.  A couple other things that could be causing problems.  Make sure secure boot is turned off and that fast boot is also off.  
This[ Ask Ubuntu]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu") thread should help with the nomodeset.
Just looked it up and at least some model of that era had Nvidia Graphic chip set and would deffinately need the nomodeset in order to boot to a desktop and after install will need the proper Nvidia driver installed from the driver manager.

Hello! Thanks for a suggestion. Fortunately, videocard is not an issue because, as I stated before, Linux is capable of working on this laptop. I successfully booted Ubuntu and Kubuntu off of a USB flash drive before the issue appeared.
The machine has two videoadapters in it: integrated *Intel HD Graphics 3000* and discrete [I]NVIDIA GeForce GT 620M.


[/I]**EDIT:** There are no such options in my BIOS as fast boot or secure boot. I think they are hidden, because Windows 10 seem to support them on the laptop. And I have no idea how to reveal the options...

---

### Post by yancek on 2019-03-02
Newer Acer laptops with windows 10 generally require 'trust' be set in the BIOS with a Supervisor password required.  Your computer is probably old enough that this will not apply.  Have you tested the usb(s) you are using on another computer to see if they boot to rule that out as a possible problem.  Did you install windows 10 or was it pre-installed by Acer?  Is your drive a GPT or MBR drive?  Are you able to access your BIOS and do you have a Boot Options key?

---

### Post by unclecomrade on 2019-03-02
> **yancek said:**
> Newer Acer laptops with windows 10 generally require 'trust' be set in the BIOS with a Supervisor password required.  Your computer is probably old enough that this will not apply.  Have you tested the usb(s) you are using on another computer to see if they boot to rule that out as a possible problem.  Did you install windows 10 or was it pre-installed by Acer?  Is your drive a GPT or MBR drive?  Are you able to access your BIOS and do you have a Boot Options key?

1. The flash drive is booting successfully on an another PC.
2. It's a 2012-2013 laptop without any preinstalled OS, so I installed Win10 myself after using 7 and 8.1 for a while.
3. Windows reports the drive is GPT.
4. I am able to access the BIOS and I do have a Boot Options key. The BIOS won't let me change the mode to Legacy or UEFI - there is no option to do that nor there is an option to enable/disable secure/fast boot.

---

### Post by unclecomrade on 2019-03-06
Well, apparently, I'm a bit of an idiot.
All I had to do is to try different USB ports.
It worked on USB 3.0 one.

---

### Post by cariocavip on 2019-06-03
Man, I feel you. I've been around the internet looking for an answer for the same problem. I'm amazed by other dude that posted his question listing EVERYTHING he had already tried and probably would have been the first sugestions of others conrades and also gave the forum an idea about his expertise - just saying to encourage more of this format.

Anyway, here's my two cents for the internet: that black screen going nowhere seens to be related to the fact you are probably experiencing a disk failure. Don't ask me why, since the bootable DVD/pen drive should have opened the toubleshooting screen anyway IMO, but It seens they check your drive before that and if your drive is unreadable, the process freezes. 

I have a HDD external case ($10) that let me use my HD on another computer like if It was a pen drive (you probably already knew that). Then I check It with GetDataBack Simple (to more complete exam and file recover) and/or with windows' Disk Management default app. It says my disk has a lot of bad sectors. So I dismounted my old windows partition and created a new 128GB partition to make a clean install. I'm not sure how will It be able to avoid those bad sectors again on this new partition. I hope choosing "slow format" will do the trick, but in last case, let's just get a new HD.

---

