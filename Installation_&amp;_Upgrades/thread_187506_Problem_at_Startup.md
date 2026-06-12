---
title: "Problem at Startup"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by foxx21 on 2006-06-03
I installed Ubuntu on an external hd. When my laptop boots up it takes me to grub, runs ubuntu, starts to load Ubuntu, then after it says loading module I get a black screen with 
--------------------------
Alert!
/dev/sda2 does not exist. Dropping to a shell!

Busybox v1.00-pre10 (debian20040623-1ubuntu22)
Built in SShell (ash)

/bin/sh: tty, job control off

---------------------------

I cannot get past this screen. When I use Live CD it works fine. Any help with this problem would be greatly appreciated. Thanks for your help.

---

### Post by pellgarlic on 2006-06-07
[edit: sorry, totally didn't read your post properly. ignore me :)]

---

### Post by pellgarlic on 2006-06-07
ok, i actually did find something:

[http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=16190&post_id=111367](http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=16190&post_id=111367)

it seems that some of the mepis folks having the same problem with an external usb drive found that adding a "rootdelay" gave the usb drive more time to initialize and become ready, thereby circumventing the problem. you could try this and see if it works for you. let us know if it does, as i'm planning on doing a usb drive install soon as well... :)

(quick reference:

in grub's menu.lst, append "rootdelay=10" to end of "kernel" line:

kernel /boot/vmlinuz-2.6................. rootdelay=10

)

---

