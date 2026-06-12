---
title: "Ubuntu on one hhd Win 7 on another"
date: 2015-06-10
forum: Installation &amp; Upgrades
---

### Post by ray9 on 2015-06-10
I have Ubuntu 14.04 on a 500 g hhd and Win 7 on an 80 g hhd for my security system.  My question is how can I get the windows drive to keep accurate time?  I've read that I need to go into the bios and change the time on the windows hhd.  I am dual booting with grub.  When I select windows at boot windows starts up w/o an opportunity to get into the bios.  How can I get into the bios or how can I set the time in Win 7 so it is synced with Ubuntu?

Thanks in advance.

---

### Post by oldfred on 2015-06-10
You go into BIOS before grub or Windows starts. If a BIOS system, you should see the BIOS screen for a few seconds. It may even say what key to use, often del or f2 to get into BIOS. 

New UEFI systems have a fast boot setting that gives no time to get into UEFI/CSM unless you change that setting.

 [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)
time, UEFI, windows 8  - several posts by sudodus  
[http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648](http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648)

---

### Post by ray9 on 2015-06-12
I didn't work.  Works for Ubuntu but not Windoze.

---

### Post by oldfred on 2015-06-12
Did you read link on UTC vs. local time and how to change it in each system?

---

### Post by efflandt on 2015-06-12
Both Windows and Linux read the CMOS (hardware) clock/calendar when they boot. It is just that Windows assumes that CMOS is localtime and by default Unix systems would consider it to be UTC. When you install Linux and set it for the proper timezone it usually automatically figures out if the hardware clock is UTC or localtime. If for some reason it does not, see **man hwclock**. Assuming that you system time is correct in Linux, I think all you need to do is:```
sudo hwclock -w --localtime
```Then Windows should boot with the same time. After that time servers (ntp) can help you keep the time in sync in either system.

---

### Post by ray9 on 2015-06-24
I ran the command in terminal and nothing happened.  So I rebooted into win7 and the time was still wrong.  Ubuntu and all other Linux distros I've used have always kept the correct time.

---

### Post by ray9 on 2015-06-26
Resolved.  I went back again and changed the time in the BIOS and it finally took this time.  Thanks for the replies.

---

### Post by ray9 on 2015-06-26
Nut's.  Rebooted and it's 5 hours off again.  This after resetting the BIOS.

---

### Post by oldfred on 2015-06-26
Is system old enough that the little coin battery on motherboard has failed? Usually good for over 5 years, but no determined life.
Main reason to know it is not working is when BIOS does not hold settings & power cycle resets all BIOS settings back to defaults.

---

### Post by ray9 on 2015-07-04
You may be right on the battery.  The BIOS doesn't keep time.  So the battery looks like a watch battery?  I suppose there's no two in the same place.  I have an EMachines ET1161-07.

---

### Post by ray9 on 2015-07-04
I'll bet you're right on the battery  Looked in there and found it.  Will replace and advise.  Thanks.

---

### Post by ray9 on 2015-07-04
Replaced the battery and that fixed it!  Thanks again!

---

### Post by oldfred on 2015-07-04
Glad that worked. :)

You can change to Solved.

---

### Post by ray9 on 2015-07-06
I rebooted a couple of times and the time was correct so I figured it was fixed.  Nope.  Not holding time again.  I have no idea where to look.

---

### Post by oldfred on 2015-07-06
Since BIOS reset with battery change, you may have to redo the suggestions in Post #2?

---

