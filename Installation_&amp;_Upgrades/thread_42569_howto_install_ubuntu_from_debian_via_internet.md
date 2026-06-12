---
title: "howto install ubuntu from debian via internet"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by lynx7taupin on 2005-06-18
this is a dumb simple question but being a newbee I'm not quite sure how it goes

I want to install ubuntu directly from internet without burning any CD, predownloading the CD images on my hard drive on making boot diskettes 

I've searched the forum some but I've fund up until now is for when you have a windows installed and you want to add a ubuntu install

well I don't have windows on my machine (not the one where I want to install ubuntu) I have debian insted

I know there is a way to install any linux distribution by downloading a few short files and editing the lilo config while using debian, then reboot and have ubuntu to install autoticaly from the internet

I my case I'll whant to get rid of debian one ubuntu starts to install,

I know this is simple but I can't remember how exactly it work and can't find it; could anyone give me a link or some help ?

thanx,

lynx7taupin

---

### Post by netrattler on 2005-06-18
Here are some links to help you out.

[http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge](http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge)

[http://www.ubuntulinux.org/support/documentation/faq/upgrade-woody](http://www.ubuntulinux.org/support/documentation/faq/upgrade-woody)

Joe

---

### Post by lynx7taupin on 2005-06-18
well I tryed that but it didn't quite work and now I have a brken system

what I wanted to do is not upgrade install ubuntu and remouve debian

what I was looking for was more [http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html)

but I there is no unpartitionned space on my computer and I don't remember where I car repartion my disk,

so I guess I'll wait to recive the ubuntu CD

---

### Post by lynx7taupin on 2005-06-21
looks like I'm out of luck

I finally burned a CD but didn't know I would be useless

first I hadn't noticed that I had to have a least 64 MoRam so I had to add ram, and once installed it was dead slow

My biggest problem is that ubuntu is the FIRST lunux distribution I've seen that did NOT detect my 3com 509B isa cards, so with no network my ubuntu is clearly useless, in other words I guess I have to give up on ubuntu and wait until I get a newer computer someday

later,

---

### Post by netrattler on 2005-06-21
With an ISA card your probably going to have to configure that by hand to get it to work. what do you get when you run ifconfig eth0. If the module isn't loaded you can always add the module by hand, the module for it should be 3c509. So all you need to do is add it to your /etc/modules and edit the /etc/network/interfaces.

Joe

---

