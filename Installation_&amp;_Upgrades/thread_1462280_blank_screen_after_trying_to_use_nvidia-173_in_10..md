---
title: "blank screen after trying to use nvidia-173 in 10.04"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by hcaleman on 2010-04-25
I did a fresh install of 8.04 alternate disk with LVM then updraded to 10.04 (due to lack of any spare CDs around).

Everything was working fine but wanted to try to get the nvidia-173 drivers installed (I have an old FX5200).  Can't start into X now as my plasma says mode unsupported.  

At one point I managed to boot into recovery mode then root terminal and removed all nvidia packages and reinstalled nvidia-173 only and followed the instructions listed on the 10.04 release candidate page.  Still stuck with the unsupported modes error on my TV though.  I have a 720p plasma display (1366x768), I usually run 1280x768 without issues.  I'm guessing it is the refresh rate set in the new xorg.conf that is throwing me off, how to adjust this?  

An issue that's complicating things however is that when I try to boot into recovery mode I get an error stating 'pcspkr' driver already registered, aborting... then it hangs there until I ctrl-alt-delete and force a restart.  This is preventing me from getting to the point where I can select a a root terminal to try to fix my errors.  

Any advice is appreciated, I have used 8.04 exclusively for a few years and wanted to try something new (still not all that adept at linux setup).

EDIT: I managed to get to root again and just removed the xorg.conf file and that seems to work somewhat.  Except now I can't boot as I get a looping mountall: Plymouth command failed that hangs up the process.

---

### Post by davoudi on 2010-06-01
[http://ubuntuforums.org/showthread.php?t=1470822](http://ubuntuforums.org/showthread.php?t=1470822)

---

