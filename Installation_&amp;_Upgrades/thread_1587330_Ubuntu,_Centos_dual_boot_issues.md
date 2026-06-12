---
title: "Ubuntu, Centos dual boot issues"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by lxlv01 on 2010-10-03
hello, lately, wanted to see the red hat side of things and do some virtualization with CentOS, so i am trying to dual boot ubuntu 10.04 LTS and CentOS 5.5 . the machine is a laptop, toshiba A100 series.

what I did was to create the following partitioning scheme via Ubuntu LiveCd

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288290+   5  Extended
/dev/sda5               1        2103    16892284+  83  Linux
/dev/sda6            2104        9988    63336231   83  Linux
/dev/sda7            9995       12623    21117411   83  Linux
/dev/sda8           12624       18800    49616721   83  Linux
/dev/sda9           18801       19457     5277321   82  Linux swap / Solaris
```created an extended partition and in there have made sda5 and sda6 as / and home for ubuntu and sda7 and sda8 as / and home for CentOS. and sda9 as swap.

I installed ubuntu first and then installed CentOS with no bootloader. Run sudo update-grub through ubuntu and now i have both Ubuntu and CentOS available. But when i select CentOS, i have an error which reads "invalid magic number".

I have grub2 installed, haven't downgraded or done anything to it and the ubuntu install is fresh, one week since i updated to 10.04 from scratch.

I have found much contradictory stuff on google, but not something that provides a definite solution and also [this post]("http://ubuntuforums.org/showthread.php?t=1305252") but the second command provided in the solution is one i cannot understand very well and it doesn't seem to work. 

Can someone tell me what I am doing wrong here and how to make this work. I would prefer to do things via Ubuntu since debian stuff is what i am comfortable with and i am installing CentOS to learn not to do work on it.

---

### Post by oldfred on 2010-10-03
There was a similiar thread.

Multiboot Ubuntu 10.04, CentOS 5.5
[http://ubuntuforums.org/showthread.php?t=1545969](http://ubuntuforums.org/showthread.php?t=1545969)


Post this to see your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

