---
title: "Problem getting 10.04 LTS kernel source"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by bingasedu on 2012-03-16
I'm running 10.04 LTS, and I need to rebuild my kernel with a modified config file. I'm trying to following the procedure spelled out at [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile), but I'm running into a problem when I try to download the source. Here's the command and the output.
```

$ sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux-source-2.6.34.1' as source package instead of 'linux-image-2.6.34.1'
E: Unable to find a source package for linux-source-2.6.34.1
$

```
I'd be grateful for any help with this. Thanks.

---

### Post by Bucky Ball on 2012-03-16
> For those of you who want or need to rebuild the kernel, you can  download the source code with the config file from the links above, as I  wrote before there wont be anymore included kernel source archive, but  you will have a package called  linux-source-2.6.34.1-blackjack_2.6.34.1-1_i386.deb which contains the  kernel source code with the patches.... from [HERE]("http://blog.robertalks.com/index.php/2010/07/09/kernel-2-6-34-1-blackjack-released-for-debianubuntu-blackjack/HERE"). Just wondering if that kernel is still about. I am using 2.6.38-** on my 10.04 boxes (not on one now so can't be specific, sorry).

One thing you should always do before compiling a kernel is update. I would upgrade, too (this will not upgrade to a newer release, just apps and packages). One after the other in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```BTW, do you have gcc installed???

```
sudo apt-get install gcc
```You won't get far without it, but doubt that's the issue. ;)

---

### Post by bingasedu on 2012-03-16
Thanks very much for the response.
> **Bucky Ball said:**
> ... from [HERE]("http://blog.robertalks.com/index.php/2010/07/09/kernel-2-6-34-1-blackjack-released-for-debianubuntu-blackjack/HERE"). Just wondering if that kernel is still about.
That link appears to be dead.  :(

> **Bucky Ball said:**
> One thing you should always do before compiling a kernel is update. I would upgrade, too (this will not upgrade to a newer release, just apps and packages). One after the other in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```
I'm just wondering if/how this is different from running the Update Manager. Also, I do have gcc installed.

Can you tell me why the following doesn't put any source code in /usr/src - isn't that what it's supposed to do? Especially when it reports that linux-source up to date? Or is it putting the source somewhere less obvious, perhaps?
```

$ sudo apt-get install linux-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$

```

---

