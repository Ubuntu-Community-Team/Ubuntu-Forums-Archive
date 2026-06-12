---
title: "minimal install for just remote x via ssh"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by zero-9376 on 2007-03-14
Hi all, what i want to do is install a minimal system without local x and still be able to run x applications though ssh to a windows or linux machine via ssh, i tried with a console install from edgy alternate and then installed xterm but it wont let me open it on the remote machine.

help appreiciated.

---

### Post by cowmix on 2007-08-15
Bump. (Running Feisty server)

---

### Post by TravMan63 on 2007-08-15
Is this possible without Xserver running?  If so - I'd like to know how as well...

It is supposed to be possible to login from a display manager - if you can configure the 'magic cookie' properly... I have been unsuccessful with that.


I don't think this answers your question - but is how I do it...
Otherwise - I run x11vnc on host - and a user must be logged into x

then I can start x11vnc over ssh (as that user) - and run  vnc viewer 4 on XP to run X apps

a restriction seems to be (with ubuntu 7.04) - that with the 1st created user x11vnc will not work.  Works with other users created after 1st.

---

