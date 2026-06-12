---
title: "Moving hard drive with ubuntu, need to re-install??"
date: 2006-05-27
forum: Installation &amp; Upgrades
---

### Post by strebor71 on 2006-05-27
Hi folks, i currently have one computer with ubuntu installed on it, and a new one with windows. i would like to take the hard drive out of the machine with ubuntu and put it in the machine with windows and dual boot. i am thinking that what i will need to do is after installing the ubuntu drive, run the ubuntu install disk to install grub boot loader to be able to pick which OS to start.  a few questions:

1. is this thinking correct?

2.  what will happen when ubuntu starts and realizes that it is on a new machine? will it just reconfigure itself to the new machine components?

3. should i just wipe the ubuntu drive and do a fresh install, and set it up dual boot as if it were never installed before?

i would rather not wipe if i could help it, i have downloaded and installed lots of apps. and stuff. thanks in advance -mike

---

### Post by simonn on 2006-05-27
[QUOTE=strebor71]
1. is this thinking correct?
[/quote]

Maybe. You might (probably will) have to make changes to /etc/fstab and /boot/menu.lst. 

> 
2.  what will happen when ubuntu starts and realizes that it is on a new machine? will it just reconfigure itself to the new machine components?


Probably. If you have some unsupported hardware then you may have some problems.

> 
3. should i just wipe the ubuntu drive and do a fresh install, and set it up dual boot as if it were never installed before?
 

No! The only reason you had to do this  with windows is because of the registry and drive labelling (i.e. C:, D: etc)

---

