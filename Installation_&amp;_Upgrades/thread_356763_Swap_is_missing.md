---
title: "Swap is missing"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by eppoh on 2007-02-08
This PC has Xp/ PClinuxOS and Kubuntu, in  multi boot array. The Kubuntu seems to be a bit slow, for having 512mb memory on the board.

The memory monitor show the swap as "unavailable" and when I check the partitions it shows it but does not show the mount point. It actually says "none" under mount point.

 I know the swap partion exists. I created one when I installed the Os and PCLinuxOS uses it. So how can I get kubuntu to use it?

---

### Post by Stemp on 2007-02-08
> It actually says "none" under mount point.

There is no mount point for the swap partitions.

> So how can I get kubuntu to use it?

Are you sure your kubuntu is not using the swap ? 
Try this command : **free** to look at you swap usage.
eg : Swap:       522104      17724     504380

---

### Post by eppoh on 2007-02-08
What command is that? I get nothing in a shell when I issue : free

---

### Post by taurus on 2007-02-08
You mean there is no output at all when you type this command from a terminal (after hitting the Return)?

```
free
```

---

### Post by eppoh on 2007-02-09
I get command not found.

---

### Post by taurus on 2007-02-09
How about this command from a terminal?

```
sudo fdisk -l
```

---

### Post by eppoh on 2007-02-09
As you can see. Kubuntu sees the partition, but I still think it is not using it. 
Also, the Kinfo Memory page on my Mepis machine shows the memory scale as green- like the other memory scales -unlike the "grey" one on this Kubuntu install

---

### Post by taurus on 2007-02-09
What does your /etc/fstab look like then?

```
cat /etc/fstab
```

---

### Post by eppoh on 2007-02-09
problem was in the fstab file. Changed it to recognize the partition as /dev/hda2 instead of using UUI. Now it works. Thanks

---

