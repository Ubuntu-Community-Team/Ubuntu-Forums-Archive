---
title: "What can I do??? Installation questions"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by gigaferz on 2006-07-21
Ok..I was reading alot..and found about sometimes the livecd partitioner  freezes, so I used the partiotioner in Ubuntu and made a 40gb partition,then I made it as an ext3. So I now have a windos dev/hda1 and  an empty dev/hda2.
Now when I tried the installer  and select the 3rd option manually edit partitions..the new empty partition does not appear..How do I install ubuntu in that partition..Do I need to mount the partition before installing ubuntu???   Im trying to install ubuntu drake..Right now..on another space the installer is not responding.. how do i Stop a process like that..(in windows I bring up the task manager select the program and click end process..)

---

### Post by nalmeth on 2006-07-21
You don't really want to jump to kill an app, but you can do it in a similar way if you'd like.

Go to System -> Administration -> System Monitor.

Regarding the install..

You shouldn't need to create an EXT3 partition, I would delete it, and leave it as open space, then tell the installer to install to the largest continuous space.

If you're worried about the liveCD installer, and you have the bandwidth, I would go with the alternate installCD. Not as pretty, but much more dependable.

---

### Post by gigaferz on 2006-07-21
Thank you so much for your help..I restarted the lve cd version..then I found that the installer recognized the new partition..but...when I was going trhough  the process I realized I needed the root (3gb) and the swap (2gb)..making 3 linux partitions..after i edited my  main linux partitions in 3..i restarted again..and  everything else was a piece of cake...Thank you so much  again..The system monitor  looks real familiar...I tried before sudo kill al..but it didnt work...

---

