---
title: "Installation hangs"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by pjaj on 2008-09-03
Fresh burn of ISO image of 8.04.1
CD checks OK
Ubuntu boots and runs from CD
Installation runs as far as partition stage, scans disks and then just sits there with "rotating" cursor.

---

### Post by Pumalite on 2008-09-03
Post your specs. (Memory, Graphics)

---

### Post by stoope on 2008-09-04
Hello,
I had the same issue. The problem ended up being an old hard drive that I was trying to install to. It had an old NTFS partition that was signaling "last shutdown unsafe", this prevented ubuntu from mounting it normally unless you use the --force option (at least when running from the live cd) Also the SMART status for that drive was bad. Since I am new to linux, I can't say for certain which of these was the exact problem, but I would suspect the former is not an expected issue during install and causes it to hang, I just ended using a new drive to install to. Hope this helps

---

### Post by Crafty Kisses on 2008-09-05
Could be a hardware issue like RAM and what not, try the alternate CD installer see if you get better luck.

---

### Post by junglist313 on 2008-09-06
Having the same problem here. Brand new Gateway with a 300gb drive, pentium dual core, 2gb ram. Trying to set up a Dual boot with Vista. Live CD boots normally, cannot get installer past the partition stage, hangs at 0%. Tried to run gparted, and gparted hangs at inital scanning stage. The wierd part is during the isntall it correctly identifies the drive, allowing me to move the slider to resize the partitions.
 So after this I tried the Wubi installer. Install went normally until I was instructed to remove the cd and reboot. Vista hung during logout, (uh-oh) And after a hard reboot I was greeted by the boot menu. I chose the Ubuntu option and was greeted by a prompt reading:

init/fram)>

Or something like that. I typed help and was given a list of commands, ran the usual ls and such and it appears a normal file system is there but I am unfamiliar with this type of install. 

I am trying to do this install on a friends computer so I don't currently have the machine in front of me, so any ideas on what to check the next time I go over there would be appreciated. Thanks!

---

### Post by Pumalite on 2008-09-06
If you can boot a Live CD; post:
sudo lshw

---

