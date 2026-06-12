---
title: "[SOLVED] Getting rid of previous installations"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by 1205919 on 2007-09-21
Hi Im fairly new to Ubuntu

When I first installed ubuntu (6...?) I didnt really know what I was doing (not that I know now LOL):confused:

To get to the point, I installed Ubuntu a couple of times, mainly because I somehow locked myself out and was afraid to loose my existing data, so I did a new install each time.

I suspect that the old installations are using up a lot of space and would like to know how I can establish how many different installations co-exist on my machine and how to get rid of all the previous ones and keep just the latest Ubuntu 7.0.4

When I boot my machine I see a list of different (I Think ) installs and I always boot to the first one , where im able to see all my stuff...

Please help

Regards
Paul

---

### Post by takeawaydave on 2007-09-21
It sounds like you may have multiple redundant entries in your grub.conf so your given multiple options to select on startup.
You may on the otherhand have old installations on various partitions of your harddisk. Really depends on what you did. 
A quick fix would be to backup any data you want to keep, boot using a live disc (ubuntu install disc should do or knoppix) and then reformat the disk (use gparted/parted/fdisk) and then get a nice new fresh install done.

---

### Post by 1205919 on 2007-09-21
Thx for that
Which tool would you suggest for making backups

---

### Post by takeawaydave on 2007-09-21
Personally I'd just use a cd/dvd or usb hd. Have you got any of these?

---

### Post by 1205919 on 2007-09-21
yip
got an ext usb hdd
thx
i think ill do fresh install
have  a nice day

Paul:)

---

### Post by 1205919 on 2007-09-21
sorry one last question
how do i backup my mail from thunderbird 2?
if i can just copy the folder  containing the mail, where is it

Thx

Paul

---

### Post by takeawaydave on 2007-09-21
It should be under ~/.thunderbird (~ si your home directory). 

open up a terminal and type:

ls -la

you should see this directoy ( . means it is hidden the ls -la shows the hidden directories as a list) 

Just be safe and backup your home directory.

---

### Post by 1205919 on 2007-09-21
thx
your help is much appreciated

---

