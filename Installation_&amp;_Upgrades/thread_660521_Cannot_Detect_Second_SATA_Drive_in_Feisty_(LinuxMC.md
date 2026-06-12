---
title: "Cannot Detect Second SATA Drive in Feisty (LinuxMCE)"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by haputanlas on 2008-01-06
Hello Everyone,

I have a second internal SATA hard drive that I have installed on my currently running system. I cannot see this hard drive at all with my current instance of Ubuntu. If I use a LiveCD I can see it as /dev/sdb, however LinuxMCE/Ubuntu does not see /dev/sdb at all. It's very weird that nothing I do can see it at all.

In addition, dmesg doesn't show the device either. I figure that it may be a configuration issue since other OSs can see it. 

Other things to note:
- The first hard drive is also SATA
- This new drive is already partitioned as EXT2 (Through a LiveCD). 
- Using KDE
- 750 GB Hard Drive - Seagate

Any ideas?


Justin

---

### Post by Emerzen on 2008-01-06
Go to System-->Preferences-->Hardware Information.  Is it listed there?

What have you done, other than dmesg, to detect it?

In my experience of adding harddrives, it's detected but not mounted.  To check if this is the case, try

```
sudo mount /dev/sdb /mnt
```

It should appear on your desktop.  If not, browse to the /mnt and see if it's that folder suddenly has 750Gb of space.

---

