---
title: "X crashed after upgrade"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by thirdmusketeer on 2006-05-18
Hi Guys 

I did an upgrade and after reboot my X never starts up. I have no idea how to tackle this problem, I have come across solutions where Keyboard needed to be changed to kbd but mine is already kbd in xorg.conf. The following links are my two files.

[http://vlsi.colorado.edu/~sohail/Xorg.0.txt](http://vlsi.colorado.edu/~sohail/Xorg.0.txt)
[http://vlsi.colorado.edu/~sohail/xorg.conf](http://vlsi.colorado.edu/~sohail/xorg.conf)

Any insightful remark would be very helpful.

Thanks

---

### Post by NoUse on 2006-05-18
I assume you did the upgrade via synaptic or apt-get?

I would try making sure all of X is installed:
sudo apt-get install xserver-xorg

---

