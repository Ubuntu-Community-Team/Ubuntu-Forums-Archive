---
title: "installer hangs on partitioner"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by themoebius on 2006-11-17
I'm trying to install on a Dell Inspiron 8200 with a 30GB hard drive that currently has only an NTFS partition. When the installer gets to the step 5 it says launching partitioner which goes away then it has basically a blank screen and it just sits there reading the hard dist for about 15 minutes with the spinny mouse cursor. After about 15 minutes the partitioning screen is finally displayed and I can change the options but I can't move forward because it still isn't done reading the hard disk. It takes another 20 minutes for that to complete and now I'm still waiting after I clicked forward after selecting my options.

A bug?

---

### Post by themoebius on 2006-11-17
It stopped loading the hard drive but now its still sitting hung when i click forward after selecting partition options. The other strange thing is that the CPU is being used at 100% according to top. 51.3%us, 47.4%sy but the processes in the list don't add up. They total maybe 15% at most.

here's the paste [http://paste.ubuntu-nl.org/32287/](http://paste.ubuntu-nl.org/32287/). firefox and xorg spiked for some reason when i copied the output of the c console but normally it idles as described above.

I also rebooted and started the process over, this time monitoring CPU usage throughout. Currently its in the first loading partitioner stage where the hard drive read light is on but top reports CPU usage at 97%wa. The highest usage for a single process is around 0.3-4%. 

I swear there is some kind of phantom process taking up all my CPU!

---

