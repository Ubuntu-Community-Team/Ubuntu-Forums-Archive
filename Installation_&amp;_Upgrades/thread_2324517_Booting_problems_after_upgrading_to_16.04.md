---
title: "Booting problems after upgrading to 16.04"
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by dannyboyinpy on 2016-05-13
This seems similar to my problem, but I tried the nomodeset tweak and it didn't seem to work. You can see the details of my situation on my askUbuntu post (no answers) here [http://askubuntu.com/questions/771514/cant-start-up-after-updating-to-16-04](http://askubuntu.com/questions/771514/cant-start-up-after-updating-to-16-04) . With nomodeset the output at the alt-f7 screen reads 

fsck from util-linux 2.26.2
/dev/sda1: recovering journal
/dev/sda1: clearing orphaned inode 524295 (uuid=122, gid=131, mode=0100600, size =0)
/dev/sda1: clearing orphaned inode 524293 (uuid=122, gid=131, mode=0100600, size =0)
/dev/sda1: clearing orphaned inode 524291 (uuid=122, gid=131, mode=0100600, size =0)
/dev/sda1: clearing orphaned inode 524290 (uuid=122, gid=131, mode=0100600, size =0
/dev/sda1: clean, 569967/9519104 files, 10823249/38047232 blocks

I really don't know if this output is important or useful, but thought it couldn't hurt to give all the information I can. I really appreciate any help I can get as I need this computer for a school project due soon.

---

### Post by dannyboyinpy on 2016-05-15
It turns out that the update had failed, but I was able to fix it simply by running

sudo apt-get -f update

This fixed the broken packages. Once this was fixed I was stuck in a login loop but that was easily fixed by changing the owner of .Xauthority

---

### Post by seanbw2 on 2016-06-16
> **dannyboyinpy said:**
> It turns out that the update had failed, but I was able to fix it simply by running

sudo apt-get -f update

This fixed the broken packages. Once this was fixed I was stuck in a login loop but that was easily fixed by changing the owner of .Xauthority

When you said you were stuck in a login loop, did you mean a username/password loop or a maintenance /control D loop.
If it is a control-D loop, how did you get out of it? Please!
thanks for your time.

sean :-k

---

### Post by RobGoss on 2016-06-17
If you have corrected your issue would you mind marking this thread as solved

---

