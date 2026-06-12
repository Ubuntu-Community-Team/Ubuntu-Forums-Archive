---
title: "Failed boots thanks to Ubuntu, SATA, Linux, SCSI confusion"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by pofadda on 2007-05-20
I d'loaded both 7.04 Ubuntu and Xubuntu as possible working replacements for my Zenwalk installation.  They turned out to be as flaky as most other Linuxes when used with SATA (and, worse, Intel P965/jMicron motherboards).  Put simply, they don't install properly.  This is well documented in many forums including this one.  

Users fretting about non-installation post in the forums largely getting more disheartened, it seems, by poor responses, badly expressed, from untrained others who probably haven't actually read the plea fully before leaping to the writer's 'rescue'.

It is dismaying that as prestigious and otherwise well thought out distro as this can let this business slide on, blandly passing the buck for their users' distress on 'the community' instead of tackling the problem and actually documenting the  solution (or temporary workaround if that's all they can do) in the Documentation.  Ubuntu Community Documentation:  search: 'sata' result: 'German-language content has been moved to GermanSATAHowto....'  This for an issue that has been around for around a year!

Zenwalk - a piddling distro by Ubuntu standards - just installs and runs.  Suse 10.2 installs but only if the DVD is dumped onto the primary HDD and a curses-based 'manual install' is done.  Others just get worse.

Ubuntu - scarily - can behave differently for each attempted install.  On a default boot-up, the thermometer-bar can freeze after a millimeter, after a centimeter or may boot to a LiveCD screen.  About 5 attempt are needed for each such 'success'.  When trying the 'recovery' boot, the booting dies - usually after about 207 seconds has been shown on the screen.

I even got it to install but whether it would re-boot was still a gamble.  I can attach screen shots of stopped points but won't - for b'width reasons - unless asked.

I even edited the GRUB launch script ( hd(0,3) or /dev/sda4 i.s.o. UUID etc because during one failed boot the message was 'dev/disk/by-UUID/432194858757etc does not exist'! It does.

More than one person has said 'I haven't got time in my life for Linux'.  This sort of thing does not dispel that perception.

What's needed at a distro level to sort out this SATA/Linux/SCSI mess and when will Ubuntu offer an easy install, free of kludges and work-arounds for newbies with new kit?

Rant ends.

---

