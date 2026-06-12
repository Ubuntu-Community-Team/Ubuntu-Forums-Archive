---
title: "Stuck after install.."
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by drewfus on 2005-08-25
I am having trouble running(installing?) 64bit of ubuntu.. install works fine or at less no errors. it also seems to start up alright, but at the last moment the sceen goes blank all accept for a "_" in the top right corner. Soon after the sceen goes blank I hear a little tune (sound a bit like drums..) then nothing except after every second press of the enter key it plays the tune again..

my specs r..
Athlon 64 fx-55
1 Gb Ram
nividia geforce 6600gt x2 (SLI)

it currently install on an old 4 Gb harddrive

I can go Ctrl + Alt + F1  and get a prompt.. but being a newbie I am not sure what to do?? 

I have try install drivers for my graphic card but have no idear of the root's password as i have just installed ubuntu

---

### Post by adwait on 2005-08-25
Apparently X cannot start on your machine, so there must be a problem wit hthe graphic card drivers. The root password is same as your normal password in ubuntu...you use sudo.

---

### Post by kamstrup on 2005-08-25
In Ubuntu you have no root user. Everything you will have to do as root you do like```
sudo my_root_command
``` and use you normal user password when it asks you.

Almost 100% sure it's the graphics driver that is givin you trouble... Your ctrl-alt-f1 prompt will save you :-)

In the thread below I explain how to change your driver to "vesa" - that almost always works. You are probably using the "nv" driver now (if you are using something else then try setting it to "nv") which strangely doesn't seem to work on your system.

[http://www.ubuntuforums.org/showpost.php?p=238105&postcount=20](http://www.ubuntuforums.org/showpost.php?p=238105&postcount=20)

IMPORTANT: In the thread I refer to /etc/X11/XF86Config. Since you are using Hoary you should replace this by /etc/X11/xorg.conf everywhere...

Be sure to post back if you solve the problem. Good luck!

---

### Post by drewfus on 2005-08-27
I muxt have terrible luck.. vesa or nv configuration inproved nothing and the i download drivers from nvidia which complained about no gcc install.. currently trying to install gcc but am have little luck, because it also is looking for a cc or gcc installed ???

---

### Post by kamstrup on 2005-08-27
If you are building your own nvidia drivers you'll need gcc and the linux kernel sources...

```
sudo apt-get install build-essential linux-headers-`uname -r`
``` should do the trick here. Then try compiling again...

Good luck

---

