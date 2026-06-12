---
title: "Ubuntu 10.04 doesnt work after install"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by Mr.Z53 on 2010-12-05
Im totally new to Ubuntu and anything linux so bear with me, i dont know all of the tech terms or anything.
 
Anyways, i have an HP Compaq desktop that had Windows XP on it but it got so bogged down with downloads and installs that it barely worked anymore. I lost my system recovery cd and decided that i would just replace everything with Ubuntu. I burnt the Ubuntu 10.10 32bit live cd, and installed. afterwards, i was unable to boot anything at all. i read that some older computers had problems running 10.10 so i burnt and installed 10.04 LTS, upon rebooting after 10.04 install, a line of code flashed accross the top of the screen, the screen went lucid black and i heard a sound like african drums or somthing. nothing else happens! i need help, thanks.

---

### Post by Mr.Z53 on 2010-12-05
Im totally new to Ubuntu and anything linux so bear with me, i dont know all of the tech terms or anything.
 
Anyways, i have an HP Compaq desktop that had Windows XP on it but it got so bogged down with downloads and installs that it barely worked anymore. I lost my system recovery cd and decided that i would just replace everything with Ubuntu. I burnt the Ubuntu 10.10 32bit live cd, and installed. afterwards, i was unable to boot anything at all. i read that some older computers had problems running 10.10 so i burnt and installed 10.04 LTS, upon rebooting after 10.04 install, a line of code flashed accross the top of the screen, the screen went lucid black and i heard a sound like african drums or somthing. nothing else happens! i need help, thanks.

---

### Post by laidback on 2010-12-05
My first thought is to suggest that you try Ubuntu Live. I see you've downloaded the ISO and burnt it to a CD. When you boot from this you should be given the option to trial Ubuntu (i.e. Live ) which doesn't affect the hard disc at all. The idea here is to test your hardware etc and see how Ubuntu is on your system before you install it. You can then install from the Live version should you wish to. If the Live version doesn't work I doubt that an installed version will either.

I'm also thinking that you should check the md5sum of you ISO and compare it with the one on the web to make sure you didn't get any corruption via the download.

---

### Post by ronparent on 2010-12-05
Each new release of Ubuntu gets new feature built in needed to support new hardware. Unfortunately the older hardware would be left behind were it not for a selection of boot parameters that can be added to the menu boot line. Also unfortunate that someone totally new to Ubuntu would be at a loss on how to identify what parameters are needed to proceed with a normal boot.

First off I never proceed with an install until I have been able to root out the needed parameter and successfully booted to a live cd. This entails hitting F6 at the line to run Ubuntu without any modification to your system, etc. On XP vintage equipment I have found the 'noapic' and/or the 'nolapic' parameters sufficient to permit a boot. Other equipment may require more. Generally deleting 'quiet splash' from the boot line helps to identify the culprit - the point at which the boot process stops gives some clue to the problem. Also the loger the process continues before stopping helps - the later the troublesome item the lower in the list of parameters it probably is.

This is a tedious process and sometimes nothing on the list works. At least then you have a more specific question to present to the forum. Also video chip compatibility problems are sometimes especially difficult to track down. Someone on the forum with the same hardware can usually tell what worked in their own case. Unless your hardware is really old (ten years or more) there usually exists a solution. 

Do post if your problem continues and someone will help you sort it down. It would be helpful if you could post the spec.s on your hardware (processor, memory, seed, graphics card, etc). If your system is too inadequate to run Ubuntu someone will let you know and suggest a suitable alternative. Good luck.

---

### Post by howefield on 2010-12-05
Please do not post duplicates in various forums.

Threads merged.

---

