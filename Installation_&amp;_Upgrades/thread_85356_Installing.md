---
title: "Installing"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by LeXiee on 2005-11-02
My boyfriend installed Ubuntu 5.04 last night and when he rebooted after the installation was completed and he got the following error about GRUB!  It was Error 18.

I would like to fix the problem for him...

Could someone help me out?

I really appreciate it :p

---

### Post by paddyg on 2005-11-02
please just take a look here:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=2284](https://bugzilla.ubuntu.com/show_bug.cgi?id=2284)

[http://www.ubuntuforums.org/showthread.php?t=6448](http://www.ubuntuforums.org/showthread.php?t=6448)

hope it may help

---

### Post by LeXiee on 2005-11-02
Ok thanks!  I'll try and make sense out of it...

I have never even formatted a PC before hehe  should be interesting :)

---

### Post by paddyg on 2005-11-02
[QUOTE=LeXiee]Ok thanks!  I'll try and make sense out of it...

I have never even formatted a PC before hehe  should be interesting :)[/QUOTE]

Well, then
please let me tell you this:

either 
make 2 partitions: one / (root) and another swap (about 2 times your ram, but usually not above 2 GB)
or
make (according to the links i gave you) 1 /boot partition (a small one), 1 /  (root), 1 swap.

Format your linux partitions (/ and /boot) as ext3 or reiserfs, NOT ext2.

You aren't going to dualboot, are you?

---

### Post by LeXiee on 2005-11-02
Nope not dualboot

---

### Post by LeXiee on 2005-11-02
I just wanted to say thanks!  I got it installed!

Now I have to figure out how to get it to detect my mouse... to do this I'm going to have to find out basic keyboard shortcuts! hehe  I've never used Ubuntu before..  should be interesting :)

---

