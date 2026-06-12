---
title: "URGENT :: I need some help before installing..."
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by Simscape on 2008-04-15
Alright, my computer is a eMachines W2646. I have upgraded it recently to these specifications...
[COLOR="DarkOrange"]REGULAR[/COLOR]
CPU:  	Intel® Celeron® 2.60GHz Processor
128KB L2 cache & 400MHz FSB
Operating System: 	Genuine Microsoft® Windows® XP Home
Chipset: 	Intel® 845GV chipset
Memory: 	256MB DDR (PC 2100)
Hard Drive: 	40GB HDD
Optical Drive: 	48x Max. CD-RW Drive; 3.5" 1.44MB FDD
Video: 	Intel® Extreme Graphics 3D
Sound: 	AC '97 Audio
Network: 	10/100Mbps built-in Ethernet
Modem: 	56K ITU v.92-ready Fax/Modem
[COLOR="DarkOrange"]NEW[/COLOR]
768MB of RAM
nVIDIA GeForce 6200
160GB SATA HDD
SATA HDD Controller
I know its not much, but it makes it go fast :KS
Now, with the 2 graphics cards, the old Intel 845G is intergraded, and in the install screen, I'm seeing waves on the screen, its hard to explain. I was wondering what if the two of them will cause a conflict in Ubuntu?
Also, I have 2 memory chips, I have exceeded my limit, my BIOS only supports 512, but I have 768.
I'm able to have Windows to work fine with that because I had a specialist take care of these things, I know quite a bit about computers, but not enough to fix that.
Any help? Will this cause Ubuntu to crash or mess up?

---

### Post by Simscape on 2008-04-15
Alright, its installed, and works, its 8.04, I still see those waves, but all is well, but I can't change desktops effects from none, do I need to download a driver for my nVIDIA card?
Do I need to download any other drivers for that fact?

---

### Post by PmDematagoda on 2008-04-15
Did you go to System>Administration>Hardware Drivers and enable the Nvidia driver?

---

### Post by confused57 on 2008-04-16
If you still see the "waves" after installing the Nvidia drivers, you might try disabling the onboard graphics in bios or blacklisting it in Ubuntu(if you can't disable in bios):
[http://ubuntuforums.org/showthread.php?p=4640049#post4640049](http://ubuntuforums.org/showthread.php?p=4640049#post4640049)

---

### Post by Simscape on 2008-04-16
> **PmDematagoda said:**
> Did you go to System>Administration>Hardware Drivers and enable the Nvidia driver?
Yes, I did actually, but it keped disabling its self... As in "Disabling" I mean every time I would exit out of the Window and go back it would be unchecked.
8.04 kept messing up on my computer, I have decided to go to 7.10 and upgrade to 8.04 once it has been released.
I'll install 7.10 and folo that tutorial confused57 gave me, thanks.

---

### Post by PmDematagoda on 2008-04-16
Your issue may be due to conflicting modules, if you still have Hardy and didn't change the driver then I can tell you a way to fix it.

---

### Post by Simscape on 2008-04-16
Nope, I don't sorry, but maybe you can help me with something on 7.10.
I have did what this tutorial has said: [Click]("http://ubuntuforums.org/showthread.php?p=4640049#post4640049")
And, I'm to the part where I need to install the driver, should I use the one in "System>Administration>Restricted Drivers Manager" or download it from nVIDIA.com?

---

### Post by PmDematagoda on 2008-04-16
Use the one in Drivers Manager(Now Restricted Drivers Manager).

I use the 6200 myself and it works a real treat, so there shouldn't be a problem installing the drivers that way.

---

### Post by Simscape on 2008-04-16
Well, I enabled the drivers, it said I needed to restart, so I did, and went into the BIOS and set the graphics to  PCI.
I started Ubuntu, the loading bar was small, but otherwise it was fine, then I saw some messages on the screen, and the last one said "Running local startup scripts..." I said alright, it does that in 8.04, and then the login screen comes up. I didn't get a login screen.
I restarted the computer enabled onboard graphics and started Ubuntu, it said its running in low graphics mode because it can't detect graphics cards correctly, I clicked continue, and it went to a black screen and nothing happened.
Well, what do I do now?

---

### Post by Simscape on 2008-04-16
Oi, why does Linux have to be so complicated....
Its my 2 graphics cards... They are causing a conflict between each other.
I blacklisted my old on (At least I think I did), it messed up Ubuntu even worse!
What do I do? I refuse to use the intergraded one, then I wont be able to use what I'm going through all this trouble for anyways...

---

### Post by Simscape on 2008-04-16
This whole problem has been miss diagnosed....
Turns out it was the hard drive causing the problem, weird, but true.
Wen I had my computer fixed, they said the hard drive was bad, but I had to test it my self, and it seemed to be working antel Ubuntu gave me an I/O ERROR on HD0, which I knew that was a drive error.
I replaced the drive, reinstalled, NOW IT FULLY WORKS WITH NO PROBLEMS!!!!!!!
YEAH! (lol, sorry)
Thank you for all your help.

---

