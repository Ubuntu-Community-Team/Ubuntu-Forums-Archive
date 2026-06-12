---
title: "Cant run live CD for Ubuntu 6.10"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by krumble on 2007-07-23
Hi, I'm kind of new at linux and I can't seem to get to the installer to work.  When I get to the menu, I have the options of (Start or install Ubuntu) (Start Ubuntu in safe graphics mode) (Check CD for defects) (Memory test) (Boot from first hard disk).  I tried to start it and when it got to the loading screen, the kernal loaded fine but when I get to the ubuntu loading screen with the bar it freezes.  I left it alone for about 20 minutes and it was at the same place. I also tried it in safe graphics mode but the same thing happened.  I checked the CD for defects but there was nothing wrong with it.  I got the CD from the "Ubuntu Linux Bible".  

My computer:
HP Pavillion a1100y with an Intel Celeron CPU 2.8Ghz and 512mb of RAM
The only upgrades I have done to the computer is I changed is the NIC. I put in a Linksys wireless network card.
I also put in an ATI Radeon X1300 video card.  I also have a wireless mouse but I don't think that would be a problem.

Any help is greatly appreciated.

Thanks, Jon

---

### Post by PryGuy on 2007-07-23
Very strange, your config seems to be okay, appears to be a hardware problem... Have you ever had good luck booting Ubuntu b4?

---

### Post by krumble on 2007-07-23
No, this is my first time booting it on my computer.  I managed to get it working on my dad's laptop yesterday, but I tried it on my computer again today and it still freezes at the loading bar.

EDIT: I also tried to run freespire's live CD on my computer but I had the exact same problem. I just stopped on the loading bar.

---

### Post by PryGuy on 2007-07-23
So it froze on two PCs? Looks like the .iso file is broken or you've recorded the CD with errors. Have you tried the original CDs Ubuntu ships?

---

### Post by krumble on 2007-07-23
Oh no, it worked fine on my dad's laptop. Its only my computer that its not working on.

---

### Post by PryGuy on 2007-07-23
Ah, I see it then... Try hitting F6 on the CD boot menu and remove the 'quiet splash' options. Then tell us where the system freeses exactly.

---

### Post by krumble on 2007-07-23
umm well it was loading and last I remember it was checking my usb drives and detected my mouse then it went through a lot of numbers and stopped at this.

[17179658.468000] EIP: [<c0114cdf7>]  smp_apic_timer_interrupt+0x1f/0x60 SS: ESP 0068:d85e7dc0

[17179658.468000]

---

### Post by PryGuy on 2007-07-23
Yep, hardware error, as I expected. Can you remove all your USB devices and all you can and try booting the Live CD again?

---

### Post by krumble on 2007-07-23
Ok well now it says something different.

[17179628.464000] Recursive die() failure, output supressed
[17179628.464000] <0>Kernel panic - not syncing: Fatal exception in interrupt
[17179628.464000] double fault, gdt at c13fe000 [255 bytes]


Thats with all USB devices removed. Do you think it is either my video card or NIC?

---

### Post by PryGuy on 2007-07-23
No, it doesn't look like this... Gurus, what do you think?

---

### Post by PryGuy on 2007-07-23
Do you have alt CD/DVD install image? You may try installing Ubuntu from there... LiveCD screws up for some serious reason, but that doesn't mean that the installed Ubuntu will...

---

### Post by krumble on 2007-07-23
Umm well I can probably DL the latest one and burn the ISO of it, but I just wanted to see if my computer will support Ubuntu, because I'm planning on getting a new hard drive and using that as the main OS. But if I can't even get it to work, I'll just have to stick with windows.

---

### Post by krumble on 2007-07-27
Can anyone else help me?

---

### Post by PryGuy on 2007-07-28
So download it! Go ahead, be brave! ;) Seriously, I think there's not enough information from you that could help us diagnose your problem. There could be millions of resons there. And, by the way I had this problem the other day. I tried to boot my server with the Ubuntu DVD my friend downloaded for me. But it couldn't even load kernel! I made a copy of this disc, just to backup the DVD because I was sure it was a hardware not disk problem with my server. Imagine my amazement when I saw the disk booted perfectly! The drive that recorded itb used a mode that was incompatible with the drive that is on my server. So it can easily be your drive incompatibility problem for instance.

Again, Don't be afraid to experiment. The whole Linux thing is like a game, the only difference is that you do not waste your time but get knowledge solving your problems, and it can help you rise more money in the future. :) I'm sure you'll find answer. There can be a hardware incompatibility in your case that you can solve replacing it, but I doubt that's the case.

Good luck!

---

### Post by PryGuy on 2007-07-28
I've googled a bit for you and found one link:
[http://ubuntuforums.org/showthread.php?t=153669]("http://ubuntuforums.org/showthread.php?t=153669")

Have you tried disabling sound card in your BIOS?

---

### Post by PryGuy on 2007-07-28
I found [one of my topics]("http://ubuntuforums.org/showthread.php?t=125468") also. Intel HDA is a tricky stuff! :). What motherboard do you have?

---

### Post by krumble on 2007-07-28
Ok Thanks, I'm going to try to disable the graphics card and see if thats the problem since I saw a thread about the ATI X... graphics card series.  If not, then I'll go ahead and DL the newest release of Ubuntu and try that. Thanks for the help

---

### Post by PryGuy on 2007-07-28
Not the graphics card, but SOUND card!
You'll tell us about the progress, okay?

---

### Post by krumble on 2007-07-29
Found the problem. It wasn't my sound card. It was my graphics card. ATI X1300 is my graphics card. When i turned it off, ubuntu started with no problems at all.  I have 1 more question, where would I go to find out how to connect to my router?

---

### Post by phenest on 2007-07-29
You already know the answer.

You said you have recently added an NIC card. Remove it. I expect the wired network driver is crashing. This is common.

EDIT:

Your graphics card? If you turn it off, how do you know what the LiveCD is doing? Have you got 2 graphics cards?

---

### Post by PryGuy on 2007-07-29
> **krumble said:**
> Found the problem. It wasn't my sound card. It was my graphics card. ATI X1300 is my graphics card. When i turned it off, ubuntu started with no problems at all.  I have 1 more question, where would I go to find out how to connect to my router?I'm very glad to hear you solved your problem!  And welcome to Ubuntu as they say. ;)

---

### Post by krumble on 2007-07-29
> **phenest said:**
> You already know the answer.

You said you have recently added an NIC card. Remove it. I expect the wired network driver is crashing. This is common.

EDIT:

Your graphics card? If you turn it off, how do you know what the LiveCD is doing? Have you got 2 graphics cards?

I did turn it off in the BIOS and tried to run ubuntu and it ran with no problems at all.  I'm going to get a new HD next week and install it on there.

---

### Post by krumble on 2007-07-29
> **phenest said:**
> You already know the answer.

You said you have recently added an NIC card. Remove it. I expect the wired network driver is crashing. This is common.

EDIT:

Your graphics card? If you turn it off, how do you know what the LiveCD is doing? Have you got 2 graphics cards?

I did turn it off in the BIOS and tried to run ubuntu and it ran with no problems at all.  I'm going to get a new HD next week and install it on there.  I thought it would be the graphics card because I saw a post a while ago about ATI X**** series and how ubuntu might not support it.

---

