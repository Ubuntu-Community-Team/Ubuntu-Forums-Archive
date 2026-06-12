---
title: "startup problems in 10.04"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by foontas on 2010-05-13
Hi, this is my first time installing ubuntu on any PC.

I decided to install ubuntu on an old computer to give it a new lease on life.
The installation went fine, other than when the computer was booted with the liveCD in the tray all that i got was a blank screen, upon pressing the reset button, the installation went without a hitch.

but once i had it up and running, when shutting the PC down, it wouldn't boot up properly and gave me an "Out of Disk" error.

So i did a bit of looking around and came across a thread that recommended this: 
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

I performed the installation as per the link and now when i shut down and reboot (not restart), I get a new error.
"Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/230d2*****whole string of numbers here**** does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu :1.13.3-1ubunutu11) built-in shell (ash)
Enter 'help for a list of built-in commands/

(initramfs)"

from there, if I press the reset button, ubuntu starts as normal!

Computer stats are:
1 Gb ram
3.1 GHz Processor 
60 Gb HDD


what i want to know is can this be fixed or is there no point?
and if so, what version of ubuntu would be best for me?

---

### Post by darkod on 2010-05-13
Once you are in ubuntu, in terminal execute:

sudo update-grub

See if that helped.

If not, try the fix in this link starting from Step 4:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

