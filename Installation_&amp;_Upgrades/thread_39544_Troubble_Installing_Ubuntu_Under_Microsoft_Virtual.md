---
title: "Troubble Installing Ubuntu Under Microsoft Virtual PC"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by koorb on 2005-06-05
I have tried a few versions of Linux, but never got on with them and then yesterday somebody recommended Ubuntu, so I am giving it a go. After the standard install I get a long black screen because the colour depth is set too high for the VPC.

Some people have [Found](http://vpc.visualwin.com/Notes/Ubuntu.4.10.html) a fix by typing in "sudo dpkg-reconfigure xserver-xfree86", but nothing happens for me.

The best I could do was login on the command line interface, type that in and then it tell me that xserver-xfree86 is not installed.  ](*,) 

So where am I supposed to type in "sudo dpkg-reconfigure xserver-xfree86"?

---

### Post by tread on 2005-06-05
Try
sudo dpkg-reconfigure xserver-xorg

Ubuntu Hoary uses xorg, not xfree86.

---

### Post by koorb on 2005-06-05
:grin: 
Thanks, works great now. And I actually think I am going to like using Ubuntu.

---

