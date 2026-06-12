---
title: "Installation Issues"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by ArcheryMonkey75 on 2008-01-24
I have been trying to install Ubuntu 7.10 on a blank hard drive for some time now and I finally got it installed.  I had the hard drive hooked up to my Windows computer because that was the only computer that would boot from the disk.  I took the hard drive out and put it in another computer...the monitor said there was a frequency issue with the video signal (even though i had used this computer before with other hard drives).  Then I tried it in a second computer and it began to boot from the hard drive but it stops on the screen where it says "OK" several times down the right hand side.  Is this becaue I transferred the hard drive from the computer it was installed on?  I made sure that when I installed it there were no other hard drives attached to make sure the boot file went on the correct drive, which was my problem a few weeks ago.  Could it be that the computers I am trying to run it on are too old (because they wont boot from any CD that I try)?

Please help me get Ubuntu running!

Thank you!

---

### Post by mssever on 2008-01-24
It's quite likely that your Ubuntu install doesn't like being suddenly transported to completely different hardware. If you boot into recovery mode, you might be able to reconfigure a bunch of stuff. Otherwise, I don't know if there's a whole lot you can do.

---

### Post by ArcheryMonkey75 on 2008-01-25
At the moment, when it boots, the last line that shows up is "Running local boot scripts (/etc/rc.local)  [OK]"  What would come after that?...or is there something wrong with the hardware configuration?

When I go into recovery mode it says "root@Ubuntu:~#" and prompts for something...What should I type in?

---

### Post by mssever on 2008-01-25
> **ArcheryMonkey75 said:**
> At the moment, when it boots, the last line that shows up is "Running local boot scripts (/etc/rc.local)  [OK]"  What would come after that?...or is there something wrong with the hardware configuration?

When I go into recovery mode it says "root@Ubuntu:~#" and prompts for something...What should I type in?

The prompt means that recovery mode came up OK. Try running ```
/etc/init.d/gdm start
``` That command is supposed to bring up your graphical interface. I'm guessing that that will fail. If so, typing this might fix your problem: ```
dpkg-reconfigure xserver-xorg
```

To shutdown, type ```
reboot
``` or ```
poweroff
``` depending on what you want to do.

---

