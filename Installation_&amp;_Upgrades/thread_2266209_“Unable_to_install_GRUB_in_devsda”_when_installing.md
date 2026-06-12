---
title: "“Unable to install GRUB in /dev/sda” when installing ubuntu"
date: 2015-02-20
forum: Installation &amp; Upgrades
---

### Post by shannon3 on 2015-02-20
What does this mean and how do I fix it? I'm installing the latest version from a cd onto a newly built computer With an MSI A78M-E35 Micro ATX FM2+ Motherboard and AMD A8-6600K 3.9GHz Quad-Core Processor.

---

### Post by ubfan1 on 2015-02-20
Is this a UEFI machine?  Is your hard disk sda?  Sometimes sda is actually the install media.

---

### Post by kerry_s on 2015-02-20
the latest version ? 15, 14.10, 14.04.2, ...?

---

### Post by shannon3 on 2015-02-20
I think it's 14.04.1. I'm trying to put it on Samsung 120GB ssd. I don't know what uefi is.

---

### Post by shannon3 on 2015-02-20
It looks like I van try it out from the disk. Everything appears on the desktop but when I click install everything starts to install until the end when I get the error message.

---

### Post by shannon3 on 2015-02-20
I looked around the mb bios and it seems to be running legacy+uefi.  I can change that to uefi only...should I ?

---

### Post by tokyobadger on 2015-02-21
[could be worth reading these UEFI install tips](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by shannon3 on 2015-02-21
Just tried 14.04.2LTS. Same error message. I think I'm in way over my head here.

---

### Post by fantab on 2015-02-21
Boot from the Ubuntu DVD/USB and 'try ubuntu', install [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), run '**create bootinfo summary**' and _note down the url_ link to the bootinfo file and paste the url here.
Bootinfo will give a detailed look into your boot process, and we need to look at it.

---

### Post by shannon3 on 2015-02-21
Got it installed! I figured out what I was doing wrong running the boot repair tool. After typing that first command and pressing enter, I didn't hit enter again, I just typed in the next command. So of course it couldn't find the boot repair because it hadn't been downloaded yet. :(  chalk it up to being a newbie I guess. Thanks everyone for the help. I'm sure I'll be spending a lot of time on these forums figuring things out. Thanks again!

---

