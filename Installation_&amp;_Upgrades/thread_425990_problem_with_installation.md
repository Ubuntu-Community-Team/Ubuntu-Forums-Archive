---
title: "problem with installation"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by harithski on 2007-04-28
I am trying to install kubuntu 6.10 on my Dell inspiron 6400 laptop.
I insert the cd and boot kubuntu. As every one knows, a wizard takes me through 6 steps in installing Kubuntu of which the 4th one is to partition the drives. I chose mannual partition because I need a dual boot with windows.
Now,  I clicked the 8GB unallocated space that I left for Kubuntu. But none of the options on the top ( create,delete etc ) are active. The only option that I have access to is the properties option. 

Why are the options not active ? I have 3 primary partitions already on my 60GB drive. How ever, I can have another one. Can't I ?

Some one please help me with this

---

### Post by bulldog on 2007-04-28
Download the Gparted live cd,it's about 50MB,burn it to a disk and boot from it.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Make the free space an extended partition and create two logical partitions in the extended partition.
One swap around  1GB and format it as swap and make the rest an ext3 partitions and format it as ext3.

Now install again and choose manual partition,mount the swap as swap and format it as swap,and the ext3 partitions has to be mounted as /  [root] and format it as ext3 again.
Set the bootflag option to yes and continue the install.


Good luck and welcome to ubuntu :)

---

