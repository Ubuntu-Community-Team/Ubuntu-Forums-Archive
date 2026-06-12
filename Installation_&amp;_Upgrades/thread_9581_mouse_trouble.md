---
title: "mouse trouble"
date: 2004-12-29
forum: Installation &amp; Upgrades
---

### Post by garriguer on 2004-12-29
Hi, I installed ubuntu, and everything went smooth, except for mouse, which behaves in an extrange way: seems to work properly, only the buttons dont work.

If I go to system configuration I don’t find any means to uninstall or re-install the mouse, or change the mouse type, which may be the trouble. I am windows user, as you can see I’m not familiar with linux functions.

Its an inalambric mouse (both keyboard and mouse are..) connected to usb port.

As I’m not able to find in ubuntu’s documentation solution to my problem, I decided to call you for help.

 Thank you.

---

### Post by garriguer on 2004-12-30
I'd like to explain something that happens on boot; I get the following:

MOD PROBE; FATAL; Error inserting HW_RANDOM:lib/module/2.6.8.1-3-386/kernel/drivers/HW_RANDOM.KO:No such device

May this be part of the problem?

How can I go around that?

Thanks again :oops: n

---

### Post by strawberry on 2004-12-30
You can try the' dpkg-reconfigure xserver-xfree86' to reconfigure your mouse-settings. I met a topic about it, pls. search for details.

---

### Post by Rancoras on 2004-12-30
[QUOTE=garriguer]I'd like to explain something that happens on boot; I get the following:

MOD PROBE; FATAL; Error inserting HW_RANDOM:lib/module/2.6.8.1-3-386/kernel/drivers/HW_RANDOM.KO:No such device

May this be part of the problem?

How can I go around that?

Thanks again :oops: n[/QUOTE]

I'm not sure about the mouse, but here's the solution to the HW_RANDOM warning.

[http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

---

### Post by garriguer on 2004-12-30
:sad: I inserted the few lines you told me in /etc/hotplug/blacklist, and now I don't get the FATAL MOD PROBE, but mouse buttons still doesn't work

---

### Post by garriguer on 2004-12-30
](*,) Sorry, I couldn't find your topic, neither been able to start a program to reconfigure the mouse

Would you mind to be more explicit? Remember I'm very new at Linux (in fact "today new")

Thank you
xxxxxxxxxxxxxxxxx
Ten minutes later, more or less, I've been able to know (trough  terminal root) that xfree86-server is not installed on my system

I tried dpkg-reconfigure xfree86-server , and I've got this answer: xfree86 not installed :?:
xxxxxxxxxxxxxxxx
Now I made it OK  (dpkg-reconfigure server-xfree86) :evil: , but there is no way, mouse allways without buttons..

---

### Post by feneks on 2004-12-30
So you are a totaly newbe to Linux? -Welcome!

Hopefully you'll understand my mini-HOWTO  8-[ 

First you need a "shell". This is little program which has a DOS-like interface - but is much better! You can find it at the Applications-menu. There you'll find a menu called "Systemtools" or so (mine is in german). There you'll get the Programm. It could be called terminal too. Start it.

Oh, you haven't any mouse working, isn't it?
If "yes" do following instead.
Press [Crtl]+[Alt]+[F1] at the same time together. Now you are in a non-graphical interface- Don't panic. Type your username. Then type your password. Then proceed with the next paragraph.

type in:
*sudo dpkg-reconfigure xserver-xfree86*

You will see the configuration interface of debconf. It will ask you several questions. Most of them haven't to do anything with mice. Just press [ENTER] then.
But one question is for mice. There you'll have to choose /dev/input/mice
Next you'll be asked for the protocol your mouse understands. IMPS could work - if not you'll have to try again -with another protocol of course. The Microsoft-protocol is another good guess.
For the following questions just press [ENTER] again. After this configuration you'll have to restart the graphical interface:

*sudo /etc/init.d/gdm restart*

Afterwards mouse should be running.
If it doesn't missing kernel-modules could be the answer.
You can look at the already running modules with

*sudo lsmod | less*
[SIZE=1] "| less" prints content at your monitor till it reaches the last line. [Curser down] and [cursor up] allows to scroll.  [q] quits less. [/SIZE]

Let us know what lsmod tells you. Only the modul names are interessting

Oh, to get back to graphic interface you normaly use [Ctrl]+[Alt]+[F7]

Anything I wrote dubious? Tell us.

---

