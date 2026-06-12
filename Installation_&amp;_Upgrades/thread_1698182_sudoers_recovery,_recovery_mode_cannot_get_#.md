---
title: "sudoers recovery, recovery mode cannot get #"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by lastguy on 2011-03-01
Ubuntu 8.04 I guess, I shall use visudo but I use gedit and made a syntax error. no other a/c, and I'm not sure whether root passwd. after that sudo su not work. use shift to get to recovery mode and drop to # prompt, yet it still ask me root passwd that may be never set or I forgot. anyway I can recover it? thanks
I know such is a old topic, sb said add single user mode, I tried to add "single" then ctrl-x yet it still asks for passwd.
{update}
I get it work, it seems ubuntu changed usage each version, so we do know developers are improving ubuntu:).

1. during boot (usually BIOS shows hot keys), hold down shift to pop up grub menu
2. move cursor to linux recovery boot, press 'e' to enter edit mode
3. the linux line already shows 'ro single', change it to 'rw single init=/bin/bash'
4, press ctrl-x to boot the system into '#'
5. cd /etc and you can modify say visudo, adduser, passwd,

what's my fault? I want to add "NOPASSWD:" in sudo line yet I added ":NOPASSWD" that blocks whole sudo. Linux is not smart, cannot remove wrong syntax auto.

---

### Post by tommcd on 2011-03-01
See this for fixing problems with sudo:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
If you have enabled the root acount, please be aware that enabling the root account is not recommended in Ubuntu.
I never bother with *sudo su*, or any of the other variations of that. I have always just use plain old *sudo* in Ubuntu and I have never had a problem with it in almost 6 years of using Ubuntu.

---

### Post by lastguy on 2011-03-07
thanks alot the link is much clear with GUI. 
yeah Ubuntu sudo works fine, previous is just my fault, I added ":NOPASSWD" but it shall be "NOPASSWD:".

---

