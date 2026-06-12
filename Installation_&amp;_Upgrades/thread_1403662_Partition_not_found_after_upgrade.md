---
title: "Partition not found after upgrade"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by luvburrell on 2010-02-10
I installed 9.04 then tried to upgrade to 9.10 and it froze so I had to reboot. Since then I have not been able to re-install 9.04 or see my partition.  Everytime I try to reinstall it says and shows that it can't find the partition like there isn't a hard drive installed.  HELP!!!

---

### Post by darkod on 2010-02-10
Boot into the live desktop and try running fsck for the root partition, for example:

sudo fsck /dev/sda1

or

sudo fsck /dev/sda5

what ever your root partition is.

---

### Post by luvburrell on 2010-02-10
Thanks but that did not work. I tshows that I have a live session user but there is no hard drive showing just the cd rom. I guess I will have to get some help in cleaning up this drive and starting fresh

---

### Post by darkod on 2010-02-10
There is software for checking partitions and drives, TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can also install it in live desktop I think, with:
sudo apt-get install testdisk

But I haven't used it so far (luckily, never needed it), and can't offer much assistance how to use it.

---

