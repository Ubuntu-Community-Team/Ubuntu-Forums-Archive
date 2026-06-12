---
title: "Xubuntu on Thinkpad I-Series 1300"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by everythingsused on 2006-12-23
I just acquired an old thinkpad I Series with 186 mb of ram. I tried to install Ubuntu from the live CD since I already had it lying around and not surprisingly it froze, so I'm attempting to install xubuntu 6.10 from the alternate CD instead. But it's freezing too, very early on in the install. I already checked the md5sum and it came out okay, but I downloaded and burned a new copy anyway just to be sure and I get the same results. I can get Windows XP to install and it works fine (although slooooooowly) so I'm pretty sure there's nothing wrong with the computer itself. 

Has anybody had any luck installing on this or a similar system? Or does anybody have any other suggestions. It seems that with 186 whole mb I should be fine, but would it maybe be better to try DSL or something else smaller? 

Thanks for your help!

---

### Post by everythingsused on 2006-12-27
Okay... no responses... that's okay. 

I'm still trying to convince xubuntu to install on this system mainly because I'm out of CD-Rs at the moment, I'm stubborn and I cannot think of any good reasons why it won't work. 

Maybe this might help - the installation always freezes at the same point no matter what command line options I use or which mode I install in. The last three lines are:

ohci_hcd 0000:00:14.0: OHCI Host Controller
ohci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:14.0: irq 10, io mem 0x81c00000

Then it stops. I even tried running over night and it wouldn't budge from that spot. If there's something funky going on with the USB bus is there any command line option to make it ignore the USB during install? Ideas anybody?

---

### Post by K.Mandla on 2006-12-28
You might check the USB options when the CD boots up. There are some F-key options for command-line switches, and USB detection might be skippable (is that a word?).

You might also try a server installation, and add on to it. However, if you're having gut-level hardware detection errors at this point, you'll probably see them again, no matter what GUI you add on.

Check your BIOS too; I know some older motherboards used a funky legacy USB system that causes conflicts sometimes. See if there's an option to disable USB or to disable any USB detection. It's going to depend on the machine and the motherboard, so I can't offer much more advice than that. :|

---

### Post by goodwill on 2007-01-16
Just want to tell you that here is another innocent i Series (I believe its 1300, SKU 2666-HH1) hit the same issue too. I do manage to boot into 6.06 LTS in GUI installer (although its slow to a level it would never complete, thats why I start another nightmare by downloading 6.10, yuck) So maybe I would test it on 6.06LTS alternate and see how it goes.
I tried the following boot parameters and it DOESNT solve the problem:
debian-installer/probe/usb=false
irqpoll (this is the one I need to put in for 6.06LTS)
noapic, nolapic
So, hope someone could solve the problem with these hints.

---

### Post by everythingsused on 2007-02-01
It's true. I tried several different boot options to get around the USB and none of them worked. I finally solved the problem by installing Debian instead. The install went very smoothly. The USB still doesn't work at all, but it's better than nothing.

---

### Post by AgenT on 2007-02-01
Debian is a very good choice for this project (or for almost any project).

For USB support, try loading the OHCI module (#modprobe ohci_hcd). The OHCI module is confirmed to work on a Thinkpad i1300. If that fails, try doing lspci and lshw to find out what specific USB controller is being used and search for it on the Internet. Good luck.

.

---

### Post by rikai on 2007-02-10
After some quick googling, i found the answer.
For future reference for anyone, passing the following parameter lets you continue the install: 
pci=off

---

