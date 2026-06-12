---
title: "How do I find and install source?"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by theinvictus on 2005-08-08
I don't have internet in linux so apt-get is out of the question....I need the source so that I can use ndiswrapper to install my wireless card, so can anyone tell me where to find and how to install the source for my kernel? 2.6.10-5-i386

---

### Post by jkndrkn on 2005-08-08
Download source here:
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

Install using the directions here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Good luck!

---

### Post by theinvictus on 2005-08-08
I need the kernels source, I already have ndiswrapper

---

### Post by jkndrkn on 2005-08-08
It's available in synaptic.

---

### Post by az on 2005-08-08
To build a module, you only need the headers.  Install build-essential and linux-headers-2.6.10-5-386 (unless you have changed your kernel to 2.6.10-5-686, or k7...)

But you already have ndiswrapper installed.  You just need to install ndiswrapper-utils, which is also on your cd (along with the headers and build-essential)

---

### Post by theinvictus on 2005-08-08
If its on my cd, how do I use it? I typed  apt-get install kernel-headers-2.6.10-5-386 and it couldn't find them... maybe I just don't know how to get the off my cd...

EDIT: You were right, source was installed in synaptice, as were headers...however the header doesn't match the kernel number instead it is like 2..6.99......test something...

How do I install the proper headers?


also ndiswrapper-utils is already installed...

The whole reason this came up is because on a different forum I was getting help on installing my WUSB11 card and someone told me to use ndiswrapper , however whenever I get to modprobe ndiswrapper it freezes the system...the person on the other forum told me I need to have kernel sources installed (which it turns out, I already did...)


Any help would be appreciated....

---

### Post by theinvictus on 2005-08-08
[QUOTE=jkndrkn]It's available in synaptic.[/QUOTE]


It might be, but not in the repositories I have access too, remember I have no access to the internet in linux so my repositories that I have acess to are just the ones that came off the cd....

Do you have to mount the cd-drive before being able to apt-get from it?

---

### Post by theinvictus on 2005-08-09
thnx for the help...I was being a moron thinking they weren't installed....when I limited my repositories to just the cd in synaptic, and then searched I found that both the headers and the source were both installed already, as wel as ndiswrapper-utils (but no seperate entry for 'ndiswrapper', is it supposed to be that way?)

by build essential, do you mean the one entry by that name that comes up when u search for "build-essential" under the cd repository?

---

### Post by az on 2005-08-09
Yes, install the build-essential package.

You do not need the source.  You only need the headers.  You need the correct headers, the ones that match your kernel.  If you did not change the running kernel, you are running 2.6.10-5-386, and you should install those headers.  If you only ave the cd and cannot get on the net, those are the only headers available anyway.

The ndiswrapper module is already included in your kernel package.  The ndiswarpper-utils is the command line program.  If that is locking up your computer, did you install the correct .inf file?

Anyway, if you want to build the newest ndiswrapper from source, you are good to go with the linux-headers-2.6.10-5-386 and build-essential.

---

