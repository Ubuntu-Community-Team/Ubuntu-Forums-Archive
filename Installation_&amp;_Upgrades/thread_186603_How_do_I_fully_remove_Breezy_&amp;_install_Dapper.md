---
title: "How do I fully remove Breezy &amp; install Dapper?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by linuxa on 2006-06-02
Hi there

Having had some bad experience upgrading from Hoary to Breezy, I'm determined to do a full clean install for Dapper Drake this time round.

I currently have Kubuntu on a Dual boot with WinXP, and have every intention not to mess up my Winxp partition. 

Would someone be so kind as to tell me how I could do a **clean** removal of Breezy Badger (this might be a more generic question targeted at all Linux Distributions).

Thanks in advance
Linuxa

p.s. Kudos to everyone involved in the Ubuntu project. For having the tenacity to bring out periodic releases with increasingly better stability and support. Great work guys! :D

---

### Post by SqRt7744 on 2006-06-02
[QUOTE=linuxa]
Would someone be so kind as to tell me how I could do a **clean** removal of Breezy Badger (this might be a more generic question targeted at all Linux Distributions).
[/QUOTE]

well, the install CD should gives you the option to "manually edit the partition table" (not as bad as it sounds).  You then choose to reformat the ext3 partition.  I've done this a number of times without damaging a preexising XP install.  I don't know about the graphical installer though, I haven't tried it yet.

---

### Post by linuxa on 2006-06-02
Thanks for the reply **SqRt7744**, I totally forgot that the repartitioning tool is available within the installer (I did have to use it to get this Dual-Boot up and running). 

I'm having a very <duh> moment right now :P

I think my intention was to find out how to remove a Linux Distribution. I'll start a new thread in the future.

Cheers.

---

### Post by aysiu on 2006-06-02
Create a separate /home partition--which will make future clean reinstalls easier:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by linuxa on 2006-06-03
[QUOTE=aysiu]Create a separate /home partition--which will make future clean reinstalls easier:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)[/QUOTE]

Thanks for the link, quite useful. Taking queue from it, what I might do instead (to avoid downloading & Booting the LiveCD), is to back up my /home to removable media (e.g. usb or CD/DVD). And repartition my harddrive so that /home retains it's own partition when I install Dapper. This way future upgrades will not take out my own settings.

Cheers

Edit: I was surprised/happy to find that as of Kubuntu 6.06. The install CD doubles as a LIVE CD, so to install to Harddrive, all one has to do is boot up the LIVE CD, and click the INSTALL icon the desktop (ala Mephis). So there's no more excuse not to back up my /home directory once the LIVE/INSTALL CD loads :D

---

