---
title: "How to tell if I'm using Ubuntu through Wubi"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2012-08-30
I'm using Ubuntu 10.04 on two computers, my current one and my old one. I want to upgrade to 12.04. I thought I'd try to upgrade on my old computer first, just to familiarise myself with the process before attempting the upgrade on my current computer. However, the installer tells me I haven't enough space to do that on my old computer.

I remember running Ubuntu through Wubi on my old computer at one stage, but I also seem to remember switching to running Ubuntu directly because of some problem I had using Wubi. At the same time, I find that I still do have on the computer the file root.disk. If I could delete it, I'd have enough space for the upgrade.

How do I establish whether I'm still using Wubi?

---

### Post by coffeecat on 2012-08-30
The easiest way I know is to look at the output of the terminal command:

```
df -h
```

Obviously, run that command from within the Ubuntu system you want to examine.

For a conventional installation, the first line will be something like this:

```
/dev/sda6        50G  8.7G   39G  19% /
```

That tells you what is mounted as the root partition. For a wubi installation, depending on which version of Ubuntu you are running, the first line will be something like this (for older versions of Ubuntu):

```
/host/ubuntu/disks/root.disk      8.5G 8.0G 23M 100% /
```

Or for 12.04, something like this:

```
/dev/loop0       15G  6.0G  7.7G  44% /
```

Also, further down in the df -h output for wubi installs, you will see this:

```
/dev/sda2       90G   46G   45G  51% /host
```

The details will vary, but that line tells you which partition is your wubi host partition.

Post your df -h output if you need any help interpreting it.

---

### Post by lesliek on 2012-08-30
Thank you for replying so promptly.

When I look at the output of df -h, I see, among other things:

/dev/loop0             13G   12G  933M  93% /

and

/dev/sda2             108G   65G   43G  61% /host

so I'm definitely still using Wubi on this computer and must have migrated from Wubi to a regular installation on a netbook I have, rather than on this computer.

If I understand the output correctly, I'm using only 13G of a total of 108G to run Ubuntu on this computer.

Would you happen to know offhand whether there's a way that I can increase by a few Gs the amount of space Wubi devotes to Ubuntu, so that I can then do the upgrade?

Thanks again,

Leslie

Later: I'm confused (even more!).

I found a script to resize my Wubi install, but when I ran it, I got this message: ./wubi-resize_1.5b.sh: Unsupported - this is not a loopmounted install

I don't know what to do now.

---

### Post by coffeecat on 2012-08-30
> **lesliek said:**
> When I look at the output of df -h, I see, among other things:

/dev/loop0             13G   12G  933M  93% /

and

/dev/sda2             108G   65G   43G  61% /host

so I'm definitely still using Wubi on this computer and must have migrated from Wubi to a regular installation on a netbook I have, rather than on this computer.

If I understand the output correctly, I'm using only 13G of a total of 108G to run Ubuntu on this computer.


Almost. :) the 108GB is your host partition. The 108GB is the total size of the partition, not the free space. Don't forget that if that is your C: partition, the Windows installation will take up quite a bit of space. Your root.disk is 13GB and 92% full so it does need enlarging.

> **lesliek said:**
> 
I found a script to resize my Wubi install, but when I ran it, I got this message: ./wubi-resize_1.5b.sh: Unsupported - this is not a loopmounted install

Was that script from one of the links here:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

Or elsewhere? Tbh, I've never done a wubi resize myself, but I usually point people to that wiki link.

---

### Post by lesliek on 2012-08-30
The script I used was from the first link that you gave, It's the automated resize script.

I see that there's a thread dealing with the script, so I'll now post there.

Thanks very much again.

---

### Post by coffeecat on 2012-08-30
> **lesliek said:**
> I see that there's a thread dealing with the script, so I'll now post there.

The thread you've posted in is for discussion of the wiki, not for technical support. See the OP of that thread. I suggest you start a new thread in a support area of the forum with a new and descriptive title, after which I'll close this one for you. The title is important to attract the attention of people who have some experience of that script.

**EDIT**: new thread here:

[http://ubuntuforums.org/showthread.php?t=2050262](http://ubuntuforums.org/showthread.php?t=2050262)

---

