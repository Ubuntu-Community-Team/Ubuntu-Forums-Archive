---
title: "Clean install of 12.04 beta 2 hangs"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by graabein on 2012-04-14
Hi, I had Ubuntu 10.10 and tried upgrading to 11.04, but it resulted in a unusable system. It just stopped booting on **Checking battery state** (and I have a desktop computer, mind you). 

So yesterday I decided to wipe it clean while keeping my /home and the Windows 7 partitions intact. I put Ubuntu 12.04 beta 2 on a stick and chose other options from the install menu. 

From there I selected the old ext4 partition for / and checked the format box. I also selected swap area and /home, but did not tick format for those. Then I started the install process... but it just said **Removing conflicting operation system files...** for more than an hour so I rebooted and tried again.

This time I formatted the old / using gparted before I repeated the steps, selecting it as ext4 / and used swap area and /home (no format again). Same thing is happening now. It just hangs on **Removing conflicting operation system files...**

So I wonder if anyone has any suggestions?

---

### Post by dino99 on 2012-04-14
wonder if your pc's hdd have some hidden partitions like HP & Dell and some others are used to, or is there some raid or crypted partitions. Never seen this error before, maybe some googling can help.

note: its a known issue  [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/946663](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/946663)

[http://www.google.fr/#hl=fr&sugexp=frgbld&gs_nf=1&cp=46&gs_id=5&xhr=t&q=Removing+conflicting+operation+system+files...&pf=p&output=search&sclient=psy-ab&oq=Removing+conflicting+operation+system+files...&aq=f&aqi=&aql=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=dda3ba5ee4953ba5&biw=1387&bih=886](http://www.google.fr/#hl=fr&sugexp=frgbld&gs_nf=1&cp=46&gs_id=5&xhr=t&q=Removing+conflicting+operation+system+files...&pf=p&output=search&sclient=psy-ab&oq=Removing+conflicting+operation+system+files...&aq=f&aqi=&aql=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=dda3ba5ee4953ba5&biw=1387&bih=886)

---

### Post by graabein on 2012-04-15
Thanks dino. I do not have any encryption going on, but I think it is a HP computer with a single original hdd. 

The partitions are as follows:

[LIST]
[*]/dev/sda1 ntfs (Windows 7)
[*]/dev/sda3 extended
[*]/dev/sda5 ext4 /
[*]/dev/sda6 linux-swap
[*]/dev/sda7 ext4 /home
[*]/dev/sda8 ext4 /media/data
[*]/dev/sda9 ext4 /media/extra
[/LIST]

I'll read more on the links you posted. Thanks again!

---

