---
title: "dual boot grub stopped working after win xp upgrade"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by Tim P on 2007-02-26
I am using unbuntu and attempting to switch everything over from my previous windows system.  I had windows 2000pro and it got messed up by a virus of sometype so I installed xp pro over the existing installation.  The unbuntu is on a seperate hdd from the windows instalation but after windows xp pro installed the grup file no longer comes up, so I cannot choose to get to my unbuntu install.  I'm fairly new to unbuntu and linux but have over 25 years of hell with microsoft so I am definitely willing to learn, but need a little help here and it needs to be explained in beginners terms.  I've got dain bramage from being with microsoft for so long.   That may be a new class action suit???

Thanks in advance, 

Tim

---

### Post by loswr86 on 2007-02-26
I'm also a linux/ubuntu newb, but I read (via my scouring the net for a solution to my grub prob) that you must install windows first when setting up dual boot. Apparently windows has a file that after installed overrules grub and prevents it from running. Sorry I couldn't give a more detailed answer, but I hope its a start.

---

### Post by mikewhatever on 2007-02-26
Probably, GRUB wrote itself to the MBR of the first HDD during Ubuntu installation, so that when you reinstalled Windows, that MBR got overwritten again. Try reinstalling GRUB to the MBR of Ubuntu HDD and then switching the BIOS to boot from that one. Then, we can manually add an entry for Windows XP to grub menu.
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I don't know your level of Linux experience, but the link above might be a bit confusing, so to say :)
Here is how to reinstall GRUB using a live CD 
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

