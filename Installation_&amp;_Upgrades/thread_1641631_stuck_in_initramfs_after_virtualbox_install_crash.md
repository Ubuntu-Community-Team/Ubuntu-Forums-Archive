---
title: "stuck in initramfs after virtualbox install crash"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by homemrobo on 2010-12-09
Hi there, let's see if anyone can help me.

I used to have my ubuntu 10.04 running with a virtualbox for a windows xp. 

I remove that virtualbox and create another one, bigger, with 10gb. On the process, my computer freezes..  now I'm stuck on that initramfs screen.

I really need to recover my linux (I have apache, mysql, samba, all up and running).

I can reach "grub" booting with right shift pressed, but I really don't know where I have to begin.. 

Some light will be great.

[]'s

Homem Robo

---

### Post by dino99 on 2010-12-09
you might need to take control with "chroot" after booting on a livecd

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

here is an example you can follow:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

then you can do what you want/need: update/upgrade ....

the virtualbox issue can be due to oversized video ram allowed. ( no max than 50 % of real ram)

---

### Post by homemrobo on 2010-12-09
Hi Dino, so, I have to start from a live cd.. but then, what can I do? I just need to fix that initramfs screen...

I try to boot with livecd, I get ubuntu running.. but I cant find any file/folder of my previous ubuntu.. How can I check where are my files/folder from livecd?

how can I restore ubuntu without losing my stuff?

[]'s

Homem Robo

---

### Post by homemrobo on 2010-12-09
Hi there, following these steps:

[http://ubuntuforums.org/archive/index.php/t-1244466.html](http://ubuntuforums.org/archive/index.php/t-1244466.html)

I found that my /dev/sda was missing. I turn off the machine, reconnect all cables and now it's back. 

After that, initramfs is gone and all my samba/web/mysql stuff is ok.

Thanks!

Ubuntu is like a wild horse!

---

