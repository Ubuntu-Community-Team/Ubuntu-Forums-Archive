---
title: "Tutorial: dual boot an installed xp and ubuntu on the IP35 mainboard"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by ldfj3jf on 2008-09-20
It took me all day! imagine the conundrum: I know nothing about linux, and ubuntu, the 'easiest' distro, won't even install. :popcorn:

Symptoms: live CD, live USB - either fail with a prompt or take forever before not finding your hard drive. It also displays 'ata 5.00: revalidation failed' over and over again while in text mode. 

Not being disrespectful, but in the forums all I could find was 'linux-centrix' advice - FYI "set all_generic_ide floppy=off irqpoll in GRUB" means nothing to a newbie. 

Check your mainboard model: if it's an ABIT IP35 the bad news is that the SATA controller is set by default to IDE, and that ubuntu won't work with that. The few fix offered in this forum DO NOT WORK - they are workarounds that eventually fails later down the road (random crap on startup, etc - there's even a related bug still open on the tracker for ubuntu). Not the best experience for a newbie.

The only 'right' solution is to set your Sata controller to 'ahci' in the bios, but of course this will prevent you from running windows XP, which doesn't support Ahci out of the box. In order to do this you need to reinstall windows with a slipstreamed ahci driver (not really fun) OR use the following EASY trick to install ahci on an already installed xp: 

[http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)

Follow the advice, and now you have a sata controllet set to ahci that will install Ubuntu in the most elegant way possible (ie, no need to mess with any config files).

JOY!!!! :guitar: I hope this saves someone a couple of hours :)

---

