---
title: "Partitions not displayed when trying to install ubuntu.Help"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by MadridBill on 2013-04-12
Hi guys. 

ok. 

I installed ubuntu 12.04 on a 24gb partition on my HDD.
It wouldn't boot though, kept getting a grub error.

So I created a new partition from free space and installed again.
It worked so I spent the rest of the day on other tasks.
I deleted and formatted the 24 gb partition and saved photos and other personal files to it.
I updated and done a restart.

It restarted fine but didn't show the 24 gb partition in home folders, I ran testdisk to see what was going on. 
It showed 2 24gb partitions.
After it had completed its checks it told me the New folder with all my files was fine.
The other couldn't be recovered, which was fine. I didn't think I needed it.

The I tried to restart the computer again.
Back to the grub error and ubuntu won't start.

I thought about instaling again over the top of the installation I have but here is the problem.

When I am in ubuntu loaded from my USB stick the home folder shows the "3 devices" which are all partitions of the HDD.
System volume - Media - New Folder

Although when I try to install ubuntu, from boot or from desktop it only shows the 250gb HDD without any partitions.

I don't want to lose my data.
I don't really want wasted space with multiple installations of any OS, never mind 2 instalations of ubuntu.

System volume has the ubuntu files on it. The other 2 contain only documents, music, video and photos.

Any advice on what I do from here?

---

### Post by darkod on 2013-04-12
Partitions do not show in Filesystem (or Home) unless specifically told to. You have to configure that. Otherwise how would ubuntu know how you want to use your partitions?

I got confused with all that explanation and mentioning of grub errors. Forget at the moment whether you can see the 24GB partitions or not. Does ubuntu boot or not?

If it does, boot it, open terminal and post the output of:
```
df -h
sudo parted -l (small L)
```

If it doesn't boot, it means you need to fix the boot process first, and only after that look at mounting partitions.

---

