---
title: "partition table gone"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by InfosecDM on 2010-02-23
I have searched and didnt find a situation like mine so i thought id ask.  i have a dual boot setup on my hp pavillion    windows vista /dev/sda1 and backtrack linux 3,while trying to install backtrack 4 (which is ubuntu based) i deleted the former partitons for bt3.  im not quite sure what i clicked but using the ubiquity installer it deleted my partition table so now my entire drive is listed as unallocated space.  i have some very important files on my windows partition other wise i would just format and start over. how can i restore the partition table and boot to windows to atleast grab the important stuff. the drive hasnt been formatted so the info is still there i just cant get to it anyone have any ideas?

---

### Post by darkod on 2010-02-23
TestDisk can do this but I haven't used it and can't give you more precise instructions. They have documentation on the website and also google might help find instructions.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by InfosecDM on 2010-02-23
the only problem with that is there isnt a bootable partition on the drive and i dont see a testdisc live cd any other ideas

---

### Post by elmosim2 on 2010-02-23
There are utilities that are meant for grabbing deleted files.  I think if you used one of these you could find what you need.

From this article 
[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)
He seems to have recovered his files using 
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Good luck!

---

### Post by darkod on 2010-02-23
> **InfosecDM said:**
> the only problem with that is there isnt a bootable partition on the drive and i dont see a testdisc live cd any other ideas

As far as I know it's in the repositories for ubuntu. Boot with the ubuntu cd into the live desktop and you can install it with:

sudo apt-get install testdisk

Of course, it will be there only until reboot. It's lost on reboot. But that's enough to finish the job.

---

### Post by oldfred on 2010-02-23
I fortunately have not needed testdisk. More info on it. It is on most recovery type CDs.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

