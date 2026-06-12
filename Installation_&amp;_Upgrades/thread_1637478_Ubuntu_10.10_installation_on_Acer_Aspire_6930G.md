---
title: "Ubuntu 10.10 installation on Acer Aspire 6930G"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by Mortesins93 on 2010-12-04
Hello,
I wanted to install Ubuntu 10.10 for a friend of mine but I need some information. First of all, I used the liveCD (32 bit version), got all the hardware info and I found out that it has a 64 bit processor, so do I have to install the 64bit version? I installed a 32 bit version on another 64 bit computer and it works fine, why? Is it normal for this to happen? If so, what are the advantages of installing the 64 bit version?
Second, I would like to keep Windows too, but I could not figure out what the current partitions were:
/dev/sdb1 NTFS 10GB (vista loader)
/dev/sdb2 NTFS 227GB (Windows recovery environment)
/dev/sdb3 NTFS 224GB
/dev/sdb4 NTFS 4GB (Windows XP Embedded)
Does anybody know what this means? What partitions can I delete or shrink to install Ubuntu?
Thank you in advance

---

### Post by sikander3786 on 2010-12-04
Hi.

You can install a 32-bit OS to a 64-bit machine but not vice versa.

The advantages of 64-bit over 32-bit is a long debate. As 32-bit now even supports RAM > 3 GB by using the PAE-Kernel, 64-bit is not an absolute necessity therefore.

If you tested all the hardware and it works well with 64-bit then I would recommend that. Why? Because it would perform a bit faster than 32-bit. You might not even feel the difference unless you are doing some data compression or video encoding etc.

And flash is no longer a problem for 64-bit.

Regarding you partition setup, it seems a bit problematic as the output you posted tells us that there are already 4 primary partitions on the drive and therefore you can't create another one unless you delete one of them. I am not sure if the sda1, sda2, sda3 and sda4 were the original results or it was just a blind guess by you.

Anyway, I would recommend to boot a Live CD and run bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would exactly tell us everything about your setup and therefore we would be able to advise more efficiently.

Results.txt will be generated on your desktop once you run that script. Copy all text from that straight into your post and wrap it with proper code tags # from the post menu. [/code] at the end and [code] at the beginning.

---

### Post by Mortesins93 on 2010-12-04
Thanks a lot, the problem is that the computer is not mine and I don't know when I could get the info you asked me for. Would the "sudo lshw" output be of any help because I have that if you need?

---

### Post by sikander3786 on 2010-12-04
> **Mortesins93 said:**
> Thanks a lot, the problem is that the computer is not mine and I don't know when I could get the info you asked me for. Would the "sudo lshw" output be of any help because I have that if you need?
Nope. That wouldn't tell us about the partitions.

If you can't run the bootinfoscript, we at least need this one.

```
sudo fdisk -lu
```

---

### Post by questioned on 2010-12-04
I have an acer aspire one with linux on it (as well as windows7). It works pretty well for both OS. As long as you have the 32-bit, it would run well as mine does. The only issue with mine, is that there is a wireless kernel problem when I boot linux. It said something with "linux wireless kernel error". Idk why it doesn't work. I hope it doesn't give you the same problem... I'm not sure how to fix mine to be honest... :?

---

### Post by Mortesins93 on 2010-12-04
Well, right now I don't have the computer here because its a friend of mine's, when I'll have a chance I will let you know how the partitions are.
Thank you very much anyways

---

### Post by sikander3786 on 2010-12-04
> **Mortesins93 said:**
> Well, right now I don't have the computer here because its a friend of mine's, when I'll have a chance I will let you know how the partitions are.
Thank you very much anyways
You are Welcome :-)

Keep us posted ;-)

---

