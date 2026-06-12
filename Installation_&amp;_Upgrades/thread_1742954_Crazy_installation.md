---
title: "Crazy installation"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by mazzy2u on 2011-04-29
OK, I just downloaded 11.04 and started to install it, selected install along side Windows 7 and instead of asking me where to install it, it just picked the hd next to the Windows drive and proceeded to format it. Which had all my backup stuff on. Great. Thanks. Er, even Windows asks where it should be installed. I have 3 hd's on this and there is a blank 500gig h/d all ready for it. I am new to this Linux stuff, and I have installed v10 before (and that curled its toes up when it automatically installed the ATI drivers). Its a bit of a bad start when it decided where to install, instead of asking me. So now I have to spend the next few hours/days trying to get back all my deleted stuff from the hd (if I can). :mad:

So to save myself any future headaches, let me know what I am supposed to select instead of it trashing a random hd in my comp.

---

### Post by dino99 on 2011-04-29
here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

but first recover your data:
[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by kansasnoob on 2011-04-29
> **mazzy2u said:**
> OK, I just downloaded 11.04 and started to install it, selected install along side Windows 7 and instead of asking me where to install it, it just picked the hd next to the Windows drive and proceeded to format it. Which had all my backup stuff on. Great. Thanks. Er, even Windows asks where it should be installed. I have 3 hd's on this and there is a blank 500gig h/d all ready for it. I am new to this Linux stuff, and I have installed v10 before (and that curled its toes up when it automatically installed the ATI drivers). Its a bit of a bad start when it decided where to install, instead of asking me. So now I have to spend the next few hours/days trying to get back all my deleted stuff from the hd (if I can). :mad:

So to save myself any future headaches, let me know what I am supposed to select instead of it trashing a random hd in my comp.

After selecting Install alongside Windows and clicking on Forward did another screen appear similar to this:

[ATTACH]190366[/ATTACH]

---

### Post by mazzy2u on 2011-04-29
It shows 3 things on the selection screen, one says install alongside windows 7, one says install over windows 7 and the last one says do something else. I have managed to get 99% of my stuff back (thankfully) and I will try again to install it on the right hard drive. So next time I will choose something else and see what happens.

---

### Post by kansasnoob on 2011-04-29
Thanks for NOT answering my question :(

---

### Post by kansasnoob on 2011-04-29
Sorry if I seem a little abrupt but I've done a lot of testing regarding the live installer (aka: ubiquity). I fought tooth and nail to get this bug fixed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

And this one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

And since I didn't find the "fix" for the latter sufficient I filed this one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

But after literally hundreds of tests I've found nothing in the Natty live-installer that should cause data loss w/o operator error.

**But I could be wrong!** It's impossible to recreate every potential installation scenario :)

Anyway, the safest way to install is absolutely using manual partitioning which is now called "Something else", and the procedure is very much the same as I showed here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

or here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

