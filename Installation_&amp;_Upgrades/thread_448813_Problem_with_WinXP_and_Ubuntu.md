---
title: "Problem with WinXP and Ubuntu"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by tb87670 on 2007-05-19
I am having serious problems with me trying to get WinXP to install after I put Ubuntu on my computer. I have 2 hard drives, a 120gig for my Ubuntu and Xubuntu, and a slaved 200gig for WinXP, both are completely clean and formatted with KillDisk and hooked up on IDE cables.

I read somewhere that I should install WinXP first and then Ubuntu, so I formatted the Ubuntu drive and now I am attempting to install WinXP. Problem is, after the greeting screen, it tells me that it can't detect my hard drive(s) and tells me to reboot (something Ubuntu never tells me). I honestly don't know what is happening, and any and all help will be needed. I am currently running on Ubuntu Live (another thing XP can't do) and will be watching for answers. If anyone wants to know, the only reason I'm needing WinXP is the compatibility with Windows-only games, thats the only thing WinXP has over Ubuntu, and sadly its enough to justify this reinstall :( Thanks in advance for helping.

---

### Post by Beuntje on 2007-05-19
Maybe your Bios is the limit ....
some biosses have problems reading large Harddisks... eg. 200gb....

---

### Post by tb87670 on 2007-05-19
Thanks for 5 minute response! My motherboard is a Soyo Dragon V2 2.0 for reference, but if this is the problem how do I fix this?

---

### Post by Ub1476 on 2007-05-19
If it were XP that said it could not detect your hard drive, you need to download the SATA drivers for your system and put them on a floppy/usb/cd. Check your computer's manufacturer website and look for drivers there. If Ubuntu could not detect your hard drive, I really don't have any clue..:-k

---

### Post by tb87670 on 2007-05-19
Ubuntu detects both of my hard drives just fine, but I am waiting to install Ubuntu after WinXp so I can choose which I want to boot at startup. I will give the sata drivers a try, thanks for the heads up on those Ub1476.

---

### Post by rillip on 2007-05-19
Remember during Windows installation that there's a step you need to take to load third party sata drivers (which is to say, any).  You have to hit F2 or F8 or something like that at one point near the very begining.

---

### Post by Ub1476 on 2007-05-19
You have to hit F6:) If the drivers you find are in a .exe file you need to extract it, then extract the .exe file inside there again, and finally open the temp.ima with MagicISO, or a a related program. Now you should see six files or something, containing txtsetup.oem. Just add this to your USB and you'll do fine:)

---

### Post by tb87670 on 2007-05-19
Well I put the SATA drivers on a cd, but WinXp Setup wouldn't recognize them (I am about to shoot the WinXP disc with my .45 pistol :mad: ) so I will give the USB drive a go. I will report back what happens, but be mindful that I'm running Ubuntu-Live so it will take time.

---

### Post by Ub1476 on 2007-05-19
Can you tell me what files you burned to the cd?

They should look like this:

iastor.cat
iastor.inf
iastor.sys
iaachi.cat
iaachi.inf
license.txt
readme.txt
txtsetup.oem

Not exactly like that of course. As you see I used ACHI, it might be you are using RAID, but anyways, it should contain all those cat, inf, sys, txt and oem files:)

---

### Post by tb87670 on 2007-05-19
I put the drivers on a usb and cd, it detected neither and asked for a floppy(I don't have a working floppy drive), so I am going to leave WinXp alone..... sorry for putting you all through this hassle, I'm just going to make due without Windows based games. This is the reason I bought an Ubuntu disc, it works better and the community is great. Thanks for the help.

---

### Post by Ub1476 on 2007-05-19
I don't have a working floppy drive either:) 

Here's what I did to get it working: 

Downloaded the Intel 82801GMU SATA AHCI Controller  (Intel Matrix Storage Manager) from fujitsu-siemens.com.

Extracted the .exe file to desktop. Extracted the next .exe file to desktop. Opened the temp.ima with MagicISO. It showed me those files:

iastor.cat
iastor.inf
iastor.sys
iaachi.cat
iaachi.inf
license.txt 
readme.txt
txtsetup.oem

I extracted them and copied them to my USB. I inserted the USB in my notebook and started the computer, booted from cd etc. NOTE: If your comp has more than one USB drive, you might have to try all of them before finding out which one is the one which is working.

---

