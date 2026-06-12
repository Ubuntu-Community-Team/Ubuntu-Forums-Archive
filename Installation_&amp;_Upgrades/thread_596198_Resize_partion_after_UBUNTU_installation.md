---
title: "Resize partion after UBUNTU installation"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by susantha on 2007-10-29
[SIZE="3"][SIZE="6"][SIZE="4"]I've install UBUNTU 7.10 in my DELL Inspiron 6000 laptop. When partioning the hard drive I've assigned 6GB for the / and rest of the 30GB for the /usr. Now I found it's not the /user I need to assign more space but for the /home folder. When I tried to copy several ISO files machine keeps on saying not enough space. I tried to move those files to the /usr section but it does not allow me to do anything in that space. Is their a way to get that space from that place and give more space to /home? I really don't want to format the machine because I've done so much customization for it now. Any help would be greatly appreciated.[/SIZE][/SIZE][/SIZE]

---

### Post by logos34 on 2007-10-29
run these commands in a terminal and post them:
[B]
sudo fdisk -l

df -h[/B]

You could shrink /usr, [create a separate ext3 /home partitio]("http://www.psychocats.net/ubuntu/separatehome")n out of the freed up space and copy your home folder files (which includes your settings & configuration files) to that partition, then reinstall gutsy without the separate /usr.  (make sure during reinstallation not to format /home).

---

### Post by susantha on 2007-10-29
Hi Logos34,

Thanks for the reply buddy. I'll post the result one I reach home today. BTW I don't have enough free space in my hdd to create another /home because all the free space has been given to the /usr. 

Will come back soon with the result you're requested.

---

