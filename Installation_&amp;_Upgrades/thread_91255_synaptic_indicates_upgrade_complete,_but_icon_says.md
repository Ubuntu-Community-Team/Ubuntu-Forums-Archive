---
title: "synaptic indicates upgrade complete, but icon says 500+ pkgs to install"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by kline on 2005-11-16
I used the synaptic Edit -> fix to get rid of the packages that needed to be deleted;
after several mnutes of getting the dependencies correct (&c), synaptic was happy.
Everythng was clean; no errors, nothing to be installed or removed.  

Then, a minute later the red circle icon in the upper-right menu bar was displayed and a mouse-over read that there were around 568  packages to be dealt with:
some deleted, others installed.   I have already downloaded this bunch before, so my best guess is that something in my database doesn't understand that my new installation/upgrade is at 5.10.  Does anybody on-forum know what magic commands I need to issue next?

---

### Post by earobinson on 2005-11-16
why not just install them?

---

### Post by kline on 2005-11-16
[QUOTE=earobinson]why not just install them?[/QUOTE]

Because it looks like exactly what I did to upgrade from 5.04 to 5.10.  Unless I'm
missing something, these files are already installed.

---

### Post by earobinson on 2005-11-17
by guess is that you are, synaptic is quite a stable program, it may be that the pkgs need updateing, try it and see if the msg goes away.

I dont see how this could hurt. + if the pks are all ready there it wont take up any extra disk space

---

### Post by kline on 2005-11-18
[QUOTE=earobinson]by guess is that you are, synaptic is quite a stable program, it may be that the pkgs need updateing, try it and see if the msg goes away.

I dont see how this could hurt. + if the pks are all ready there it wont take up any extra disk space[/QUOTE]

Well, by hook and by crook: slowly!  I've used apt-get to -f fix and install missing 
packages.  Right now I'm fetching the latest gnome.  200+ pkgs to grab and install,
so I should know more in a few hours.   X-|

---

### Post by earobinson on 2005-11-19
kk, sometimes thses things just get broken, but you always lean lots while fixing.

(your just clicking repair till it works?)

---

