---
title: "Trying to install Ubuntu 10.10 - No option to install alongside current os"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by the_hawk22 on 2010-12-25
1. Downloaded Ubuntu iso and put it on a usb stick

2. Booted from USB and on the Install - Allocate drive space window, I don't see an "Install alongside other operating systems" option

I current have Vista on a Dell Inspiron 1525 and ~45 GB free space.

What should I check/do? I'd be happy to go with the 'Specify partitions manually' option, but am not clear on how to use it. 

I read something about using GParted to setup a partition, but GParted shows that I only have one partition that's 230 GB in size (which is my entire hard drive) which just doesn't seem right... (screen shot attached)

Thanks for your help

---

### Post by AbeJarano on 2010-12-25
That gparted disk information has to be wrong so I wouldn't trust the image on that stick.  If the image on there checks with no errors then I wouldn't trust using the stick itself with that image.  Can you try mounting the iso file in Windows and installing from the virtual DVD/CD??

---

### Post by the_hawk22 on 2010-12-25
Ended up getting it to work --

1. Installed Partition Wizard Home on Vista

[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

2. Right-clicked Unallocated Space -> Create -> Primary Partition

3. Restarted and booted usb stick with Ubuntu iso on it and "Install alongside current operating system" option was available this time

---

### Post by Quackers on 2010-12-25
What machine are you using and how many partitions were already on the disc?

---

### Post by the_hawk22 on 2010-12-26
It's a Dell Inspiron 1525 that came with Vista. There were 4 partitions originally, but deleting one wasn't enough I guess. 

I was left with the original primary partition (with Vista on it), two sets of unallocated space and one smaller partition. The "install alongside current operating system" option only showed up after I set one of the unallocated space partitions as a primary partition.

---

