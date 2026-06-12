---
title: "trying to go from 10.04 to 12.04 and receiving a PAE message"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by mike_lee on 2014-03-17
In trying to upgrade from 10.04 to 12.04 to install specific application software, my old toshibas are throwing out a non-pae message.  I can see from some threads that this might be fixed in the 14.04 release.  I am looking at just running the straight Ubuntu, unless there is another distro that you would recommend.

Thanks

---

### Post by mörgæs on 2014-03-17
I suggest that you skip 12.04 and go straight to 14.04, as the installation proces is easier. More here: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) 

If you have a PAE problem then your hardware is around 10 years old and not strong enough for Ubuntu. Lubuntu is a better choice.

---

### Post by TheFu on 2014-03-17
You need a non-PAE kernel. Ubuntu used to distribute a release ISO like that ...  Don't think you can upgrade directly - it will be a reinstall.
[http://releases.ubuntu.com/12.04/ubuntu-12.04.4-alternate-i386.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.4-alternate-i386.iso) is it.

To help with the migration of your programs, settings and data ... get some ideas from here:
[http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines](http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines)  Notice the sorts of things backed up.

Your solution WILL BE DIFFERENT. That link is just for ideas. YOU will need to know where things are on YOUR system and back those up.

---

