---
title: "grub rescue"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by simikennady on 2011-02-02
:mad:i have installed ubuntu using WUBI, and it was working for the last 4 months. today i was trying to install lineno.sty file for latex files; using synaptic. while installing it some error message related to grub came and after the downloading was finish the system asked for rebooting. when i reboot the system it has gone to grub rescue mode. i have so many files saved in the ubuntu partition, i don't want to loose it, please help.
[IMG]http://static.linuxquestions.org/questions/images/statusicon/../icons/useragent/icon_windows_xp_2003.gif[/IMG] [IMG]http://static.linuxquestions.org/questions/images/statusicon/forum_new.gif[/IMG] [[IMG]http://static.linuxquestions.org/questions/images/buttons/reputation.gif[/IMG]]("http://ubuntuforums.org/questions/reputation.php?p=4245550")   i have installed ubuntu using WUBI, and it was working for the last 4 months. today i was trying to install lineno.sty file for latex files; using synaptic. while installing it some error message related to grub came and after the downloading was finish the system asked for rebooting. when i reboot the system it has gone to grub rescue mode. i have so many files saved in the ubuntu partition, i don't want to loose it, please help.
[IMG]http://static.linuxquestions.org/questions/images/statusicon/../icons/useragent/icon_windows_xp_2003.gif[/IMG] [IMG]http://static.linuxquestions.org/questions/images/statusicon/forum_new.gif[/IMG] [[IMG]http://static.linuxquestions.org/questions/images/buttons/reputation.gif[/IMG]]("http://ubuntuforums.org/questions/reputation.php?p=4245550")   i have installed ubuntu using WUBI, and it was working for the last 4 months. today i was trying to install lineno.sty file for latex files; using synaptic. while installing it some error message related to grub came and after the downloading was finish the system asked for rebooting. when i reboot the system it has gone to grub rescue mode. i have so many files saved in the ubuntu partition, i don't want to loose it, please help.

---

### Post by Rubi1200 on 2011-02-02
Hi and welcome to the forums :-)

Is Windows still booting normally?

See here for Wubi issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

problem #2, solution #1 should work.

Don't forget to apply the Permanent Fix back in Ubuntu.

---

### Post by simikennady on 2011-02-02
before doing all that can i take back up of all that in the different partition from a remote system.

---

### Post by Rubi1200 on 2011-02-02
You can recover your data from the Wubi install from _within_ Windows. In this case, you can use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk.

---

### Post by simikennady on 2011-02-03
when live CD was used only sudo fdisk -l was working, sudo grub command is not working

---

### Post by simikennady on 2011-02-03
i have asked for an external help to recover my ubuntu partition and he used windows recovery tool. Now the system has come to the orginal form(when it was bought new) with C and D partition. now is there any chances for me to recover things.

---

### Post by bcbc on 2011-02-03
> **simikennady said:**
> i have asked for an external help to recover my ubuntu partition and he used windows recovery tool. Now the system has come to the orginal form(when it was bought new) with C and D partition. now is there any chances for me to recover things.

Is there a d:\ubuntu directory? (it sounds like you installed on D: ). If not, check c:\ubuntu.

If you find it, then is there a file d:\ubuntu\disks\root.disk? If so then you should be able to recover your data.

Download the program from here [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) and point it at the root.disk file.

---

### Post by simikennady on 2011-02-03
nothing is there in both c and d drive. i think i have to reinstall everything. this is happening for the second time with me.  Is it advicable to continue having dual partition. I used some synaptic package to upgrade some new style files and now this has happened. what is the necessary precaution i should take so that similar things won't happen again.

---

### Post by bcbc on 2011-02-03
> **simikennady said:**
> nothing is there in both c and d drive. i think i have to reinstall everything. this is happening for the second time with me.  Is it advicable to continue having dual partition. I used some synaptic package to upgrade some new style files and now this has happened. what is the necessary precaution i should take so that similar things won't happen again.
Well, if the people you took the computer to really did a factory restore, then your data is gone. A windows "system restore" is something different and shouldn't affect your data. 

If you reinstall then there a number of things you can do. One buy an external hard drive and keep regular backups of your data or synch them in the Cloud (Ubuntu one).

Two, if you use Wubi read the Wubi megathread - it list all the issues and how to prevent them. Plus back up the root.disk.

If you can partition and do a regular Ubuntu install this is probably best.

And finally, change your tech support.

---

### Post by simikennady on 2011-02-03
yah right now I am trying to install windows and ubuntu in two partitions, so that this problem won't arise. yah the tech support here has just spoiled the whole thing. I am not a software person though i could find out the right way how to get it corrected using this forum but i was not fast enough to get a grip of things. before they easily done the formatting of the whole thing.

---

