---
title: "No wireless network Lucid Linux"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by anlouis on 2010-04-12
I just upgarded from 9.10 to 10.4 I previously had my wireless network working with my Linksys wusb11 ver 2.6 adapter. After the upgrade I have no wireless. In the network manager no wireless network is present, but when I run lsusb it shows my wusb11 v2.6

---

### Post by AlanR8 on 2010-04-12
Just to ask an obvious question, but you have right clicked the network icon and enabled wireless haven't you?

Sorry if this is very basic!

---

### Post by anlouis on 2010-04-12
yes networking is enabled but only the wired network shos when right clicked

---

### Post by AlanR8 on 2010-04-12
Again, another obvious question.....lets get them out the way first, have you clicked System/Administration/Hardware Drivers to see what comes up? Is the driver loaded for the wireless adapter?

---

### Post by anlouis on 2010-04-13
> **AlanR8 said:**
> Again, another obvious question.....lets get them out the way first, have you clicked System/Administration/Hardware Drivers to see what comes up? Is the driver loaded for the wireless adapter?
It shows no proprietary drivers are used on this system.
I believe the same resulted in 9.10 which worked.
 
OK I have instaled windows drivers via NDISWrapper and I can now see my wireless connection but it will not connect

---

### Post by anlouis on 2010-04-13
I have also tried installing at76c503a-cvsroot.tar but nothing shows in iwconfig

---

### Post by pdc on 2010-04-14
anlouis:

you have installed a not-released; development-in-progress; likely-to-have-problems; best-just-for-experts; will-likely-change-quite-a-bit-yet; system;

there is a development forum where the bleeding-edge folks hang out

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

why don't you post there if you want to investigate a not-released; development; work-in-progress system ...........

---

