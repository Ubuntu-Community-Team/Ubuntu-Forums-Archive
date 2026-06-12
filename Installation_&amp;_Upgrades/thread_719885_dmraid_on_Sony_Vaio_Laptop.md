---
title: "dmraid on Sony Vaio Laptop"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by rianlu on 2008-03-09
I am trying to get gutsy installed on my vaio and its giving me no end of headaches all stemming from my sataraid setup.  dmraid lets me view the partinions using fdisk and the gnome partition manager but they all show as having the same name in /dev/mapper.  I just want to format the partitions and then follow the rest of the instructions on the fakeraid howto but i cant format the partions because i dont know what to call them and I'm trying not to erase any of the data from windows.

if it helps this is the output from several of the commands given in the how to:

sudo dmraid -r
/dev/sda: isw, "isw_bdabebgcgc", GROUP, ok, 234441646 sectors, data@ 0
/dev/sdb: isw, "isw_bdabebgcgc", GROUP, ok, 234441646 sectors, data@ 0

ls /dev/mapper
control      isw_bdabebgcgc_Volume 0

anything help is appreciated greatly

---

### Post by Pumalite on 2008-03-09
If you are involved in this, backup your Windows anyway.

---

### Post by rianlu on 2008-03-09
I already have my core windows files and user files backed up, and i now have the partions formated I just cant figure out how to mount them.  If I could figure out how to access the partions in the terminal and not just the entire raid volume i would be set.

---

