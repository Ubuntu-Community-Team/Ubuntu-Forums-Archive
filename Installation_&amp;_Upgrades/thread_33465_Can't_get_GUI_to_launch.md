---
title: "Can't get GUI to launch"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by NineNine on 2005-05-11
I just installed.  The GUI doesn't work.  I get some error message about the X Server not able to start.  It asks me to read a log, which I do (with PICO I remembered from college), and it's very long, with errors about video cards and memory.  This is a generic, vanilla PC, about 5 years old (Dell PRecision Workstation 610MT).  The machine works flawlessly with W2K Pro.

What do I do?  Am I just stuck re-installing W2K?


Also, while I was sitting here typing this post, the hard drive was spinning like crazy, even though the only thing on the screen is "ubuntu login:" on a black and white screen.  What was it doing?


More info:
CIRRUS(0): No valid MMIO address in PCI config space
CIRRUS(0)I2C initialization failed
CIRRUS(0): No valid modes found
Screen(s) found, but none have a usable configuraion.

Another edit: I found this link: [http://lists.debian.org/debian-user/2000/11/msg01753.html](http://lists.debian.org/debian-user/2000/11/msg01753.html)
 
I'd like to try that one suggestion, but I can't exit the xorg.conf file with pico.  I get permission denied.  Why can't I edit my own configuration files?  Also, if I have to be logged in as adminsitrator, what's my password?  Setup didn't even tell me what my admin password is!!

Is it this difficult for *everybody* to install this thing?

---

### Post by rjstevens3 on 2005-05-11
a couple things:
1. you have to be root to make changes to xorg.conf, so in ubuntu use the sudo command.
    $sudo pico xorg.conf 
then it will ask you for your pasword. btw i use vim, so i can't help you with pico

2. there could be lots of problems with your xorg.conf. a possible problem is that your monitor doesn't return the correct values to the video card, so your modes are not found. try putting:

Option      "IgnoreEDID"  "true" #in the device section

what do you have as the BusID? if its your agp slot then it should be "PCI:1:0:0"

post your xorg.conf and maybe i can help more.

RJ

---

### Post by NineNine on 2005-05-11
[QUOTE=rjstevens3]a couple things:
1. you have to be root to make changes to xorg.conf, so in ubuntu use the sudo command.
    $sudo pico xorg.conf 
then it will ask you for your pasword. btw i use vim, so i can't help you with pico

2. there could be lots of problems with your xorg.conf. a possible problem is that your monitor doesn't return the correct values to the video card, so your modes are not found. try putting:

Option      "IgnoreEDID"  "true" #in the device section

what do you have as the BusID? if its your agp slot then it should be "PCI:1:0:0"

post your xorg.conf and maybe i can help more.

RJ[/QUOTE]

Thanks for your help.  I have no way of posting the config file, since the machine isn't working (I'd have no idea how to move that file to another computer in my network, or post it online without a GUI).  Honestly, the few hours I've spent on this is already waaay too much effort just to get a basic, working operating system.  So, thanks for your help, but I'll just re-install W2K and try Linux again in a few years when maybe it'll be working properly (of course, I've been saying this about every year for the past 10, and I still don't see any progress).  [shrug]

---

