---
title: "Why can't I install Ubuntu on my Desktop?"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by szymbar15 on 2013-01-10
So I have my desktop computer which I desire to change into Linux-Powered machine, but I can't seem to install Ubuntu. First I tried with two DVD discs, it resulted with "Medium" something error after a longer while when I pressed "Install Ubuntu". Now I tried with USB Key I made with "LiLi USB Creator". But after the screen displays icon in lower part of the screen, it turns black, displays some info that progresses too fast to read it, and it leaves me with this. Frozen.
[http://prntscr.com/oq1in](http://prntscr.com/oq1in)
Warning, picture is huge. Can you help me? ;)

---

### Post by lukeiamyourfather on 2013-01-10
What version are you trying to install?

---

### Post by szymbar15 on 2013-01-10
Would be 12.04 LTS Desktop AMD-64.
I hope it doesn't make any difference that I have Intel i5-2500.

---

### Post by dino99 on 2013-01-10
here is how to set the partitions:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode (named: install Something Else, in the installer).
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

then when installing  the  iso, choose the "Something Else" installation

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by szymbar15 on 2013-01-10
So I only need to make partitions? No magic? It will work straight after? O_o

---

### Post by BlinkinCat on 2013-01-10
Hi,

Did you check  the MD5SUMS and Hashes of your ISO ?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Good luck

---

### Post by szymbar15 on 2013-01-10
Wait, actually what do hashes (Downloaded from Ubuntu site, so they are probably all right) and partitions (I thought there was internal Ubuntu Partition Manager before install) have to the frozen install screen that doesn't change anytime? O_O

---

### Post by BlinkinCat on 2013-01-10
Hi,

How to do MD5SUM is located in the supplied link

You can very quickly check if ISO is in order by following those directions - :)

---

### Post by lukeiamyourfather on 2013-01-10
> **szymbar15 said:**
> Wait, actually what do hashes (Downloaded from Ubuntu site, so they are probably all right) and partitions (I thought there was internal Ubuntu Partition Manager before install) have to the frozen install screen that doesn't change anytime? O_O

I think the post about partitions was meant for another thread. It looked like it stopped on the graphics drivers based on your photo of the screen. You could try Ubuntu 12.10 and see if it works for you since it will have different graphics drivers. Also there's an alternate install disc which doesn't load a GUI during the install.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

See the "ubuntu-12.04.1-alternate-amd64.iso" and see that does the trick. The install process is mostly the same, you just have to use the keyboard instead of the mouse.

---

