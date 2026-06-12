---
title: "How to upgrade to new version of ubuntu in dual boot"
date: 2020-09-04
forum: Installation &amp; Upgrades
---

### Post by ahti-sc on 2020-09-04
I have a dual boot system with Windows 10 & Ubuntu 18.04 LTS. When I first installed Ubuntu I gave it very low disk space (19, 15 and 25 gb for root, home and swap) but now since knowing how cool ubuntu is for developers I want to be part of linux community so I have decided to upgrade to newer version of Ubuntu (20.04.01 already downloaded).

First time when I dual boot my system by installing ubuntu I had accidentally corrected windows leading to lose of data I don't wanna repeat it again.

So how would I safely replace my old version ubuntu with newer one  ?

My current partitions: [https://ibb.co/5MBj5tQ](https://ibb.co/5MBj5tQ)

I wanna know from experts step by step guide.

---

### Post by dino99 on 2020-09-04
Note that recent ubuntu releases now use swapfile inside root instead the previous swap partition; so it can be used to widen the /home partition. By default a fresh ubuntu installation does not set a /home partition now.
If you prefer to continue using it , then update the /etc/fstab file uuid ( via 'sudo blkid' after having wiped the swap partition and extended the /home one).

 [https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

---

### Post by oldfred on 2020-09-04
Two issues.
One reinstall or upgrade.
Other resize partitions.

Do you have good backups? Of everything on entire drive? That is a requirement before any major system change.

How much free space do you have? If you want to see your NTFS partitions you have to mount them also. (And fast start up has to be off to mount them.)
df -h

I prefer new clean installs, many others have not had issues with upgrades. But you need to have system fully updated and remove all ppa and proprietary drivers. Reinstall those after upgrade.

Advantage of new install is major houseclean. No left over kernels, log files and cruft. But you have to have good backup if you want to restore your data. And list of installed apps, if you installed a lot of apps to make it easy to reinstall them.

---

### Post by ahti-sc on 2020-09-04
I don't have any data on ubuntu so I can completely remove old version of ubuntu and install a newer one. But at the same time I don't want my windows to be affected because on windows I have lot of important data.

---

### Post by Impavidus on 2020-09-04
The partition sizes in your screenshot are slightly different from those in your post, but that doesn't really matter. 19GB for a root partition (with separate /home) is a bit small, but not ridiculously so. A 15GB /home partition is small, but we don't know your needs. 25GB for swap (your screenshot shows 15GB for swap, maybe you swapped some partition sizes in your post?) is extremely large. We usually recommend 4GB.

The Ubuntu installer nowadays defaults to a swap file instead of a swap partition, but Ubuntu will work fine with either (or even with none, but then your programs will crash instead of slow down when you run out of memory). If you use a swap file, the root partition must be slightly larger (obviously).

If you want to give more space to Ubuntu, first use Windows to shrink the Windows partitions to free some space up. Make sure this space is adjacent to the Ubuntu partitions. Reboot Windows a few times to let it run all filesystem checks it wants to run. Then boot a live disk and open gparted. Delete the Ubuntu partitions present now, create new partitions with the layout and sizes you prefer. Then start the installer, select "something else" for partitioning, select the partitions you created and set their use. Then install. Just don't touch the Windows partitions. I hope you've got backups of your important files anyway, right?

---

