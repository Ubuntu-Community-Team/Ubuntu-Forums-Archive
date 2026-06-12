---
title: "Same error during and after install (critical temperature)"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Mikebgr on 2010-04-30
Hello,

I got the same error while installing (even though install works fine!) during installation and after it. Its Critical temperature reached, 3564 C, shutting down. Celcium value is not made up, its actually among those lines (four-digit).

I had another problem with installation, but I managed to install using nomodeset setting. My pc is a rock laptop (which is actually supposed to work well with vista instead.. oh wel..).

Any suggestions? I have tried installing with acpi=off, but it doesnt make any difference during installation or after it..

Also another error I got during some of my tests was: "init: Failed to spawn rc-sysinit main proccess: unable to open console: input error

---

### Post by Mikebgr on 2010-04-30
any thoughts on this? I have also tried setting the bios to mark my disks as raid but to no avail...

---

### Post by doas777 on 2010-04-30
obiviously a sensor reading is messed up, since you would be dead if within 30 feet of a machine at that temperature. 700C will melt iron. 

what software is giving you this reading? lm-sensors/sensors-applet?

---

### Post by Mikebgr on 2010-04-30
Actually I'm not really aware if I'm dead or not but my ubuntu installation trully is! I dont quite follow you, since I dont know which sensor gives that reading. The crash happens on boot up and a kernel panic occurs (could not start inetd I think is an error that pops sometimes). Is there a way to shut that thing at bootup so I can get inside the actual OS and find proper drivers?

---

### Post by doas777 on 2010-04-30
wow, i had no idea that the kernel was every concerned directly with system temperature. something is seriously wrong there. sorry man, this sounds to be way outta my element. 

can you boot into recovery mode?

---

### Post by Mikebgr on 2010-04-30
I think the kernel is indirectly affected since inetd is stopped but kernel needs something from inetd. I'm not really familiar with whats happening during boot so I'm at a loss!

---

### Post by Mikebgr on 2010-05-01
Actually this is SOLVED!

I booted into recovery mode and installed nvidia's drivers through aptitude and voila, I'm posting from 10.04!

---

### Post by RavenDT on 2010-06-16
May be solved for you, but I have been having this same problem, except I don't even have Ubuntu installed on my computer. The installation won't even come up due to the fact that it says "Critical Temperature reached (3720 degrees C)". My laptop is about 6 months old, and Fedora 12 and Windows 7 work fine. I got rid of Fedora, expanded my Windows 7 partition, and installed a new hard drive. I was able to install Ubuntu 10.04 Server on my Tower PC, but I can't boot into any Ubuntu installation on my laptop. :(

---

