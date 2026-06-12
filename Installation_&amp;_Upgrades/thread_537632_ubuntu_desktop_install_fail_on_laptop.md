---
title: "ubuntu desktop install fail on laptop"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by ctsiow on 2007-08-29
Hi
Trying to get a windows laptop to dual boot to ubuntu desktop but I now have now working os on the system. The install seemed to have stopped with no error and system was sitting on the live cd desktop, with install icon etc and on a reboot get the message operating system not found. I have a ubuntu server running with no probs but this was built from ground up as a Linux box, not dual boot. Best way out of this please? I need to get windows back up and running then I can work out what happened to ubuntu.
Thanks
Mark

---

### Post by wjp.reg on 2007-08-29
You should be able to use the **recovery console** from the winCD and then run ```
fixmbr
``` to repair the master boot record and be able to boot windows again.

---

### Post by ctsiow on 2007-08-29
Hi
I will give that a go. I have tried again to install, this time it stopped with 'executing grub install /dev/grub failed' 'this is a fatal error'.
I will get xp back running then start again. thanks for the reply

---

### Post by ctsiow on 2007-08-29
No, fixmbr not worked. logged on to the recovery console ok and ran fixmbr and got the warning about not doing this unless you are really in trouble. did but no good. Luckily I took a full backup of the c drive last night using xp backup and this is stored on my other desktop so I do have a system backup to go back to. However I need to get windows on to get the files back on. Oh well, no-one ever said computers was easy.

---

### Post by ctsiow on 2007-08-29
I have now tried a repair install but this fails to boot windows too. I am interested as to what sort of damage installing ubuntu can have done to the drive, not hardware damage, just software. system is a amilo pro v8010, 512 ram, 80 gb sata hd parted 60 / 10 / 10 centrino 2GHz cpu. Could it be the sata drive?

---

### Post by Pumalite on 2007-08-29
Try: Recovery>FIXMBR>FIXBOOT

---

### Post by ctsiow on 2007-08-29
Right I have xp back working again so the question is what is likely to have happened? It appears that the part that I was loading ubuntu onto, one i set up using acronis, (ext3), was empty and was active so when the system went to boot there was nothing to boot from. I was using a desktop cd d/l yesterday and booted the system from that. I went to guided partitioning to start with, that one seemed to fail with out any errors. Then tried again with manual set-up with a /boot of 256mb, swap of 1G and 8G for /. I wasn't going to set-up separate home and everything else as I have done on the server. Shall I try again? Prob not even though I am now back working ok. Will try on a new h/d after a new install of windows just to find out what went wrong but not today!
Thanks for the suggestions, this has not put me off Ubuntu in the slightest, I still think it is a great system, just perhaps the Fujitsu Seimens laptop is not the best one to put it on.
Mark

---

