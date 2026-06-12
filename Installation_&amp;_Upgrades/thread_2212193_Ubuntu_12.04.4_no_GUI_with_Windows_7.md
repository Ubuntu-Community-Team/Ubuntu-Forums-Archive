---
title: "Ubuntu 12.04.4 no GUI with Windows 7"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by acron2 on 2014-03-19
I just installed Ubuntu 12.04.4 on a seperate partition with Windows 7 as my Primary OS (installed first)
I let Ubuntu do the distribution of the partition under the "Install Side-by-side" option
When booting up, there is no prompt asking for ubuntu so I googled it and some forums said to install EasyBCD and add an entry

I did that and I got a new boot option, but when I boot into it I get a Grub4Dos command prompt asking for grub> commands

I tried the following:
startx - command not found
boot - error 8 kernel must be loaded before booting
sudo apt-get install... - sudo not found

I've been breaking my head over this for the past 4 hours, but I can't figure it out.
I've tried reinstalling 5 times, I've looked at all the possible forums I could think of and none of the solutions people had before helped.


Computer specs:
Inter i5-4670K CPU @ 3.40GHz
32GB RAM
Z87-G45 MSI MoBo
ASUS NVidia GeForce GTX770 

OSs installed
Primary: Windows 7 Professional
Secondary: Ubuntu 12.04.4

---

### Post by TheFu on 2014-03-20
Please run **boot-info** and post the link here. My signature has links.

---

