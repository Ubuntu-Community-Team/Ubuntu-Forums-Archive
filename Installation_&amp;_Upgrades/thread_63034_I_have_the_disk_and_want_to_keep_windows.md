---
title: "I have the disk and want to keep windows"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by signman on 2005-09-06
I cant find any description of what happens when I put the disk in and the ubuntu 5.04 install screen comes up. I am running win2000 on this machine and every other version on others. I want windows to still boot (dual). Initially I only want to try ubuntu. from what I can see you need considerable experience to go past the install screen.
hope someone can point me in the right direction. ](*,)

---

### Post by GreyFox503 on 2005-09-06
I just did a quick google search and this page has some screenshots of the installer:

[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

Most of the installation is really easy, the only tricky part is the part about partitioning.  If you have free space on your drive (I mean unpartitioned space), then the installer can automatically create partitions for you.

If your computer is like most people's, then your windows partition will cover the entire drive.  If this is the case, then you should probably defragment windows thoroughly, then instruct the installer to shrink your Windows partition by a little.

Ubuntu doesn't need too much space.  If you gave it just 10GB that would be plenty for the base system and the swap space, though if you want to install a lot of applications, you might need more.

If you're just trying it out, then I think the base install uses around 3-4GB (probably  a liberal estimate), and there is a swap partition which is usually 1-1.5x the amount of RAM you have.

Hopefully that is enough to get you started.  If at all possible back up your important data in Windows before you begin, but in my experience the installer does a pretty good job with partitioning.

---

