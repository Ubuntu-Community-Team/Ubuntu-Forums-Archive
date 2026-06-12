---
title: "Live CD boots, but I get some weird console"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by psychiccyberfreak on 2006-12-26
**EDIT: moved topic to this thread:** [http://www.ubuntuforums.org/showthread.php?p=2060445](http://www.ubuntuforums.org/showthread.php?p=2060445)

I got my brand new computer yesterday with a nice core 2 duo processor, blah blah blah...

I installed windows (only for games) and then I moved on to kubuntu 6.10.

I turned it on, and the boot menu came up, I selected start or install, and it loads the kernel. I get to where KDE is supposed to come up, but instead I was confronted by the "debian built-in console (ash)"

the output says "failed to access ttk; job controll turned off". I type in startx to see if *mabie* it works, but it says "command not found". I pop in my regular ubuntu 6.10 CD and I get the same message, and I put in 6.06 and I get some other error message, but I'm not going to get into that.

so, what should I do?

---

### Post by tnseditor on 2006-12-26
I am also trying to install Kubuntu Edgy and it has the same error message.  I have also tried  Ubuntu Dapper 32 bit with the same error message and Dapper 64 bit that will just hang before loading anything.  If I find a way around this, I will let you know.  :-k

---

### Post by psychiccyberfreak on 2006-12-26
I probably wouldn't do 64 bit, it supports it but I've herd it's more efficient using 32 bit. I was thinking mabie there was a boot parameter disabling the pretty loading screen mabie it would fix it. Sady, I don't know what it is/could be/if it exists.

Oh and my setup is similar to yours; core 2 duo custom built 2 gigs of ram 160 gig hard drive, an intel DP965LT and a nvidia geforce 7 series graphics card :)

---

### Post by tnseditor on 2006-12-27
I read that you can get to the boot screen and press F6 and then enter noacpi.  I have tried it with Dapper 32 bit and Kubuntu Edgy 32 and neither will work. :(

---

### Post by psychiccyberfreak on 2006-12-27
Same here... :(

---

### Post by flsantos on 2006-12-27
Try new download, or new copy of ubuntu. It should do...

---

### Post by tnseditor on 2006-12-27
I am trying to download Feisty 64 bit now.  Do you suppose it will work?

---

### Post by flsantos on 2006-12-28
I believe you should try Edgy again. Feisty is a work in progress, or else try Dapper (its stable).

---

### Post by tnseditor on 2007-01-14
I installed Ubuntu Feisty (Herd 2) 32 bit without any problems :D!  I am very happy to have Ubuntu on my new computer!

---

### Post by psychiccyberfreak on 2007-01-23
that's great, I'll try that out later, but I think I might wait untill it is released and stable before I actually use it, if it works.

But my computer must hate linux because I just tried installing fedora and it seems it does not have drivers for my SATA controller. ](*,)


**EDIT:** Mabie if I try the alternate CDs it will work, I'll try that now

---

### Post by psychiccyberfreak on 2007-01-24
OK, I tried the alternitive disk, and it says that I don't have CD drivers for it.

I have a samsung drive with lightscribe and it's a DVD RAM drive. (Yes, it's a burner)

**EDIT:** device manager calls it "TSSTcorp CD/DVDW SH-S182M"

so, I think that's the problem with the regular disk too, but does Feisty have more CD drivers and that's why it works?

---

### Post by psychiccyberfreak on 2007-01-24
Ok mabie it's also my SATA controller, not just the CD drive. It's an intel ICH8 4 port SATA storage controller.

this is getting real frustrating I might just not put it on... but help me anyway

---

### Post by psychiccyberfreak on 2007-01-24
Ah found the problem myself:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502/comments/99](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502/comments/99)

> ICH8 SATA controller doesn't work. This is a known situation. This is
another bug and is totally unrelated to this bug.

Also found this:

> Q. Why Linux is not detecting or recognize my attached hard disk? How do I install Linux on SATA hard disks?

A. Go to your BIOS setup

Press F1/F2 or Del key to enter into BIOS setup

Now turn the ICH8 controller in AHCI mode

Save settings reboot system

Now Linux installer should see disk. Read this previous FAQ for more information. 

[http://www.cyberciti.biz/faq/linux-sata-controllers-not-recognize/](http://www.cyberciti.biz/faq/linux-sata-controllers-not-recognize/)

Should I do this? I am dual booting windows here, I don't want to screw that up either.

---

