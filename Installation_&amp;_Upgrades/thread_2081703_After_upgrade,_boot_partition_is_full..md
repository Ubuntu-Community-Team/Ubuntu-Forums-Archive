---
title: "After upgrade, boot partition is full."
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by Go7enKs on 2012-11-07
Hello guys,

I just fresh installed Ubuntu 12.10 on my laptop which has a dual boot with Windows 7. Now, for some reason, my /boot partition is almost full (only 10mb left!) and I think this is messing up my updates. 

I had allocated around 250mb to the boot partition, following some instructions online. 

How do I solve this problem? 

Thanks guys!

---

### Post by jerome1232 on 2012-11-07
Reasons to not have a boot partition...

How many kernels do you have installed? Check with this command, if you have a lot, remove the older ones, keep at least 2.

```
dpkg --get-selections | grep linux-image
```

---

### Post by Go7enKs on 2012-11-07
This is what I get when I use that command:

```
linux-image-3.5.0-17-generic		install
linux-image-3.5.0-18-generic			install
linux-image-extra-3.5.0-17-generic		install
linux-image-extra-3.5.0-18-generic		install
linux-image-generic				install
```

Looks like I only have two...

---

### Post by snowpine on 2012-11-07
Boot with Live CD and use GParted to make your /boot bigger.

Separate /boot partition in Ubuntu is completely optional (unless you are doing something like LVM and/or encryption). Kernels are bigger than they used to be, so some old/outdated documentation on the web may recommend a /boot size smaller than what you actually need these days.

---

### Post by Go7enKs on 2012-11-07
I'll try that. Any suggested size to be safe and not run into this issue anymore?

Thanks!

---

### Post by snowpine on 2012-11-07
Strangely, Ubuntu's guide to Partitioning Schemes recommends 100mb:

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by oldfred on 2012-11-07
I have not booted into Quantal for several days and only have -17. My /boot says:

252 items, totalling 28.9 MB

So unless -18 is huge, you should not have that much space used??

---

### Post by snowpine on 2012-11-07
For what it's worth, my Debian /boot (created automatically by the installer) is 228M and is only 9% full (but I only have 1 kernel).

---

### Post by jerome1232 on 2012-11-07
On my 3 installs I have one using 118 MB, one using 185 MB one using 120 MB.

The one with 185 MB has like 8 kernels though, the one using 118 has 5.

I don't think you should be going over 250 with just 4 kernels installed. Are those linux-image-extra kernels really big???


I think 500 MB's ought to be safe, although I would've said 250 ought to be safe as well.

---

