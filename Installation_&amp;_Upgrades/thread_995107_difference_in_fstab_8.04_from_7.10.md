---
title: "difference in fstab 8.04 from 7.10"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by jocatoth on 2008-11-27
i just upgraded ubuntu 7.10 to ubuntu 8.04. i have noticed that a network drive appears twice on my desktop, once in a folder which was created to mount a network drive into and once in a drive icon. both work fine to access the network drive. the duplication is unnecessary. i would like to clear up my misunderstanding of the fstab way of mounting a network shared drive.

the relavant entry in the fstab appears in the following format:

//Whitebox/Black	/home/john/Desktop/White_Black	cifs  exec,uid=john,gid=users,ip=192.168.1.125    0    0

it would seem that network drives are handled differently in 8.04. so i am not sure how to mount and use network drives properly. perhaps someone could point me in the right direction. thanks:confused:

---

### Post by jocatoth on 2008-12-24
i had some help but the problem outlined above was a gnome nautilis display issue rather than something to do with fastab

look at this thread

[http://ubuntuforums.org/showthread.php?t=1011543&referrerid=148779](http://ubuntuforums.org/showthread.php?t=1011543&referrerid=148779)

---

