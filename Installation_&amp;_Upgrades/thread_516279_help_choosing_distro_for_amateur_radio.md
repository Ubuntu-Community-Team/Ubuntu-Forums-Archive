---
title: "help choosing distro for amateur radio"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by displicente on 2007-08-03
I just installed ubuntu 7.04 for desktop. I installed using Synaptic package manager the amateur radio ax25 software. Now that I want to config the parameters I unsure how to procede. I open the file ax25d.conf and it read only. I tried  a chmod and it is not allowed. I tried su and I can not authenticate. I can not log in as root.
Should I have better switch to the server version?
There is any experienced user that can also tip me about if it is better to use ubuntu or Kubuntu?

What I want is to run a FBB station with a Igate. probably I will install a Dxcluster later. Any help would be appreciated.

thanks in advance

Neville A. Cross
YN1V
Managua, Nicaragua

---

### Post by w4ett on 2007-08-03
Ubuntu is as good a distro as any for the Radio Amateur...I use it myself in the shack.

[http://radio.linux.org.au/](http://radio.linux.org.au/)

Is a good site for additional ham software.....another good source for information on use of open source software for our hobby is the irc channel on freenode #hamradio....lots of ops there to ask questions of.

Free BSD had a large following too, but anything you can run on that O/S, you can run on Ubuntu.

For the AX.25 protocol, install all the entries in the Synaptic Package Manager...I believe they are interdependent.

73 de W4ETT

---

### Post by displicente on 2007-08-03
Getting to install ubuntu in a dual boot configuration (linux/XP) was not that dificult. Instalation process has been really improved. The Synaptic package manager it is really easy. My problems begins going further from that point.

I am not sure if it was a mistake to choose Ubunto desktop istead of server. The problem is that the config files are read-only. And I am not sure how to work around that if I am not a allowed to login as root or giving a "su".

So my questions is simple, should I drop this desktop distro of ubuntu to try the server version?
O there is a easy way to finishing the ax25 setup without to start all over again?

Neville A. Cross
YN1V
Managua, Nicaragua

---

### Post by w4ett on 2007-08-03
You might find the Ham Radio/FreeBSD Live CD more to your liking.....AX25 is already implemented on it, and the distro is Amateur Radio Specific.  You can also install from this CD, just like Ubuntu, or you could dual or triple boot your system with it.

[http://blogs.ittoolbox.com/unix/bsd/archives/ham-radio-on-freebsd-14564](http://blogs.ittoolbox.com/unix/bsd/archives/ham-radio-on-freebsd-14564)

73 de W4ETT

---

