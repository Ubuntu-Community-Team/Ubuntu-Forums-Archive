---
title: "need help with ubuntu + light desktop"
date: 2006-04-21
forum: Installation &amp; Upgrades
---

### Post by sgoen1986 on 2006-04-21
Ok here's the problem..

Today some old P2(?) 450Mhz, with 64 mb ram and 6GB HD came in.

My plan generally is to perform an Ubuntu 5.10 server install and install a light desktop.
So i was aiming for XFCE, problem is I can't find a good guide to get this running.

Please help me out here, or point me in the right direction :)
Thanks!

---

### Post by johnny2211 on 2006-04-21
Here's a very short guide:cool: 

after the server install:

1. install x-window-system-core
2. install xfce4
3. install xfce4-terminal


After that just type: startx

install synaptic and the rest can be done in a graphical interface...

Have fun and good luck:-D

---

### Post by Jagot on 2006-04-21
Here's a slightly longer one for installing Xubuntu:

[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

---

### Post by sgoen1986 on 2006-04-22
ok thanks sol far!

I've installed the first part, but can't install xfce4, when hitting 'sudo apt-get install xfce4' I get the error message that it can't find the package..

So, how do I obtain it? :)

Thanks again!

---

### Post by aysiu on 2006-04-22
You probably skipped this step: > Uncomment the universe repository line (search for universe and uncomment that line by deleting the '#' character) (use 'x' to delete a character in vim) Please re-read the Wiki entry.

---

### Post by sgoen1986 on 2006-04-22
Ok, got it running, thanks to you all.

After it wasn't that hard, and I learned some more, again :D

Great thanks to all of you!!

(won't be the last time you will be hearing from me ;) )

---

