---
title: "Install Raid"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by janhein on 2012-11-19
Hello,
 
I have an ubuntu server 12.04 running.
It has one 500gb harddrive.
I want to add an second 500gb harddrive to create an raid 1 configuration.
Is it possible to create an raid 1 configuration on an existing server?
If yes, is there somewhere an manual with an step by step tutorial?
 
Thanks
Jan Hein

---

### Post by BertN45 on 2012-11-19
See the next recipe [http://ascend4.org/Installing_Raid_1_on_Existing_Ubuntu_Server](http://ascend4.org/Installing_Raid_1_on_Existing_Ubuntu_Server)

---

### Post by darkod on 2012-11-19
The link in the previous post seems to be how to install software raid1 when you are starting from scratch. That wouldn't keep your data.

If what you want is to keep all the data you currently have, you need something like this:
[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)

---

