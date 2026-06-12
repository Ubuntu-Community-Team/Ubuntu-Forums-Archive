---
title: "Ubuntu in Embedded PC, No Shutdown Steps"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by firasmail2000@yahoo.com on 2007-10-14
Hi Friends,

I'm new to Ubuntu forum. I was looking for procedure to customize Ubuntu OS to run it in an embedded  PC system. This PC is used usually as a control system and thus can be turned off in any time. This switch off may damage Ubuntu because no shut down steps will be done. 
My question is, what is Ubuntu components to be removed from it which needs shutdown ?
Any help will be highly appreciated.

Firas

---

### Post by tgalati4 on 2007-10-14
I used Damn Small Linux in an embedded application because it runs completely in RAM and boots off a read-only partition of a solid-state disk drive.  Rapid shutdowns do cause marking the file system unclean, but since it's read-only, I don't worry about it.

I did my coding and development work in Ubuntu and ported the binary to DSL.  After stress testing, this became a workable solution.

---

### Post by firasmail2000@yahoo.com on 2007-10-16
Hi, Friends,

I have received the following replay from one of my friends regarding my problem. Is their any comments ?


>>>>>
The problem you mention, making Linux suitable for embedded systems is not related to hardware , drivers, or anything like that. It depends on how to files system is mounted at boot ( ram,  Squashfs, cramfs, jffs2,etc. ) and how you implement the scripts spawned from init (the first user space process that the kernel executes). Currently there are many different ways to to this, depending on your application field. Also much simpler way to deal with this could be to just mount your compact flash card with the "noatime" option on ext3 , and mostly, unexpected power failures will not affect the integrity of your files system. <<<<<

regards,

Firas

---

