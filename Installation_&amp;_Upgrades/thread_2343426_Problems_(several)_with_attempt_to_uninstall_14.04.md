---
title: "Problems (several) with attempt to uninstall 14.04 LTS and reinstall 16.04.1 LTS"
date: 2016-11-16
forum: Installation &amp; Upgrades
---

### Post by ReFranz on 2016-11-16
I have a 64 bit HP business desktop (2009), partitioned between Windows 7 HP Business and Ubuntu. When I upgraded from 12.04 to 14.04, there was some bleed-through to Windows, and the Windows clock has had problems with variable time-zones since. I attempted to upgrade from 14.04 to 16.04, but there was a problem early in the process and I aborted. 

I chose to attempt to uninstall 14.04 and install 16.04. (Yes I made complete backups, thanks be). I downloaded 16.04 and burned an ISO (something I've done several times before in differing contexts), and attempted to follow the directions from this link:  [http://askubuntu.com/questions/223301/how-to-completely-remove-and-reinstall-ubuntu](http://askubuntu.com/questions/223301/how-to-completely-remove-and-reinstall-ubuntu)  .  The results were a disaster. 

As the machine attempted to boot from the disc, a purple screen with 2 small icons at the bottom (a keyboard and a 'person') appears. An error message mentioning 'failed to read' follows and disappears quickly. Then the machine rapidly makes repeated attempts to read the disk ad infinitum until the disk is manually removed, while an Ubuntu opening screen with the red and white dots seems to try to open the OS--with no success. I burned another ISO disk using Windows: using it produced the exact same result.

Since the initial failure, it's been impossible to log in to Ubuntu--I always use a Guest Account. Using my usual keyboard and the screen keyboard produces no letters in the log in line, and clicking on the login line, changes the screen to the standard purple background with only the Ubuntu logo in the lower left and NO WAY TO ACCESS THE PROGRAM. Hitting random keys including Ctrl Alt T produces a guest session with no log in necessary, but with no bookmarks, or any of my installed programs.

My next planned action is to download and burn 14.04.5 LTS, uninstall the present version, an attempt to install from the disk--then make another attempt at 16.04. I'd appreciate any ideas on this. Why might my machine, which seems to work fairly well, and regularly boots up from 2 different Puppy-Linux disks, not read the Ubuntu disks?

---

### Post by Autodave on 2016-11-16
Your download could be corrupt: I would get a fresh one and try again.

I would try and go straight to 16.04: I have never had any luck upgrading from one version to the next. I have 13 machines: I tried all 13 when 16.04 was released. One worked w/o any problems, 2 worked with quite a few problems, the other 10 just crashed (more or less).

---

### Post by ReFranz on 2016-11-18
The solution to my problem, which Autodave's reply suggested and which took my subconscious mind a day to process, is that the machinery of my desktop is incompatible with 16.04 LTS. Another contributing factor was a conversation with a Windows tech in India a few months ago. He was a conscientious person, who went the extra distance to tell me that my computer was unsuitable for Windows 10. Big thanks to Autodave for his observations!

---

