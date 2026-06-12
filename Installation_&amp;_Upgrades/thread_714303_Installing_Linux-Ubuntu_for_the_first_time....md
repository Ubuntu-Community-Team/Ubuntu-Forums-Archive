---
title: "Installing Linux-Ubuntu for the first time..."
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by levent20 on 2008-03-03
Halo,

Downloaded the live cd... i imagine the one that takes you through the ubuntu desktop and you can try things out before actually installing it... 
Checking the iso image was ok!
did a manual partition in my external drive (100GB). one 40 gb ext3 and one 20 gb swap. then i went and started installing and the computer is stuck at 15% saying detecting file systems 1 and a half hours max so far.
What should i do?
I want to try ubuntu first without touching my winxp system at the moment...
the manual partinioning was like this...

1. ext3 /    40GB
2. swap    20 GB
3.free space

Sorry new to linux, new to ubuntu, new to forums also.
Thanks,
Levent20

---

### Post by Pumalite on 2008-03-03
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
Burn a new CD. Do md5sum on the iso. Burn at 4x or less:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by mikewhatever on 2008-03-03
You'd better redo those partitions. 20 gb for swap is too much, you'll never need more then 1.5 gb.

---

### Post by drdrewdown on 2008-03-03
i thought everyone had 20gb of swap space ;p

---

### Post by Pumalite on 2008-03-03
1 GB is more than enough if you have 1 GB of RAM. In laptops /swap=RAM if you want hibernation.

---

### Post by mikewhatever on 2008-03-03
> **drdrewdown said:**
> i thought everyone had 20gb of swap space ;p

No. ): [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

