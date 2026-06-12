---
title: "How do I mount /def/ubuntu-vg/root?"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by Ranger48 on 2016-01-29
Hi, I have a big problem. I messed up my Ubuntu installation and now my laptop won't boot.

I did so many things, I'm not sure at which point things blew up. I started by trying to create a new partition on Ubuntu 14.04 for a dual boot, but then I saw that the partition was lv. Of course, wise guy didn't back up! So I spent a lot of time on the internet, trying this, trying that. I even booted up with a gparted live CD. But at some stage I must have done something stupid, because after that I couldn't boot, even with the gparted CD.

However, I can still boot with the Ubuntu live DVD, and with the file manager I can see the root partition which I tried to change. But it is not mounted, and I tried mounting it without success. If I could mount it I think I could recover my data. I don't mind having to re-install the OS again and losing my software.* But the data is important.

Could someone please advise me on how to mount the partition from the live DVD so that I can access the files. On my system the partition shows up as /dev/ubuntu-vg/root.

Thanks

---

### Post by ajgreeny on 2016-01-29
I have never used it but that naming convention means you installed using LVM partitions.

In order to mount and read them in a live OS I think you need to install the lvm2 package in the live system using software-centre or apt-get.

---

