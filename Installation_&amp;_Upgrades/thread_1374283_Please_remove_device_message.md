---
title: "Please remove device message"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by blackroom on 2010-01-06
I have a netbook with Windows 7 and already have my HDD partitioned. I downloaded UNR 9.10 and saved it to a 1GB USB drive. I set my boot priority to have it boot off of USB prior to the HDD and I save/reboot. Upon boot up I get a message to remove devices and reboot. I tried several different BIOS configurations and cannot get it to recognize the boot file. Does anyone have any ideas on how I can get this corrected? I would like to have a linux dual boot system especially since I'm taking a linux admin course.

---

### Post by blackroom on 2010-01-06
I solved this problem. This was my mistake. Now I have the problem where it loads (I see the symbol) and then goes blank and remains blank. I will research this but if you have any suggestions feel free to help out. I will check back.

---

### Post by presence1960 on 2010-01-06
When you boot the ubuntu Live USB @ the menu hit F4 and choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions") for more info.

You may also want to try the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by blackroom on 2010-01-06
I tried F4 and that moved me to a blank black screen with a cursor but I could not figure out how to do anything. I will keep looking...I may have to do a test base install as opposed to a GUI.

---

### Post by blackroom on 2010-01-07
I think I found my problem...I was using UNBootin.exe, or something like that I'm not with my netbook right now, to create the boot drive. When I formatting the Flash drive and attempted to rewrite the data on it to program would just become "Not Responding" and not copy over the files. I will try download it again or maybe even a different program.

---

