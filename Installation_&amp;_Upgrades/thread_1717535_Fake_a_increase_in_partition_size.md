---
title: "Fake a increase in partition size"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by gabefair on 2011-03-30
When I installed Ubuntu 10.10 onto my external laptop hard drive I selcted a 5gig install for no reason. :?
 
 So I tried to use GParted and tried remastersys to increase the size.
 
 I boot from and external hard-drive (host) into ubuntu when I start my computer.
 And as you can see I have plenty of space left on it. But ubuntu thinks I  don't have any space left because its mounted "disk" is only 5gigs  large.
 
 Running GParted from a live-cd doesn't work 
 b/c it can not find the /sda partition which is ubuntu. (loop 0 on host)

   [IMAGE HERE]("http://gfair.tumblr.com/photo/1280/4202823620/1/tumblr_liuu153F9e1qzw3ci")
 
Explaining the photograph below:
 111g --sda2 & sd5 is my internal HD in my Labtop
 465g -- sdb1(host) is my external HD wich contains the ubuntu os that I boot from.
 
 [I]How can  I  (the hard way) expand the size of my /dev/loop0 **without using GParted**?
 Can I **fake the partition expansion** by changing value of some variable somewhere in ubuntu?[/I]
[IMG]http://s3.amazonaws.com/data.tumblr.com/tumblr_liuu153F9e1qzw3cio1_1280.png?AWSAccessKeyId=AKIAJ6IHWSU3BX3X7X3Q&Expires=1301547790&Signature=f0TZFhCDVir2wQI7s8E8LnY%2Bj%2B8%3D[/IMG]

Thanks forum for your help
-Gabe

---

