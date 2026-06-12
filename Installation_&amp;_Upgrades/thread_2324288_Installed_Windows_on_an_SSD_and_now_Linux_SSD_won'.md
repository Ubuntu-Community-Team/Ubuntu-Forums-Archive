---
title: "Installed Windows on an SSD and now Linux SSD won't boot."
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by jgvidals on 2016-05-12
I always used my Linux OS until I wanted a few more gaming options. So I installed Windows on a separate hard drive. Now I can't boot into the Linux drive again (It flashes with a cursor). I tried the boot-repair tool and it didn't appear to do anything. I tried reinstalling the OS to the Linux drive and nothing. Can anybody see what the problem is from the boot-repair dump? I'd appreciate any help. 

paste2.org/t3enCFfm

EDIT:
I tried the boot-repair tool after I reinstalled the OS and it didn't work. Here's the output: paste2.org/bZKJ7gkE

---

### Post by oldfred on 2016-05-12
Is this yours?
[http://paste2.org/t3enCFfm](http://paste2.org/t3enCFfm)

I do not know encryption nor ZFS configuration.

But script shows Windows issues and that most often with any Windows 8 or later is really the fast startup or always on hibernation.

Use BIOS to choose to directly boot sdd and turn off fast startup.
The boot into Ubuntu and run 
sudo update-grub

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

