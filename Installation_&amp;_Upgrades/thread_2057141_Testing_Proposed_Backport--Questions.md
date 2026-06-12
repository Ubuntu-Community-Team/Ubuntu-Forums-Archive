---
title: "Testing Proposed Backport--Questions"
date: 2012-09-13
forum: Installation &amp; Upgrades
---

### Post by Alcidious on 2012-09-13
Hi all,

So I've been subscribed to a thread related to a bug I reported about my Samsung laptop.  Im running Ubuntu 12.04 32-bit, and I don't know how to install the -proposed.  I tried to follow the instructions given at: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

I created the /etc/apt/preferences file, and filled it with the content. I then ran sudo apt-get install packagename/precise-proposed.  Here is the output:

alcidious42@IronMan:~$ sudo apt-get install 3.2.0-31.50/precise-proposed
[sudo] password for alcidious42: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.2.0-31.50
E: Couldn't find any package by regex '3.2.0-31.50'

I'm not sure exactly how to proceed.  I installed and tested a couple of other kernels, but it was simpler.  I downloaded the kernel image and headers, and I can easily select the kernels from grub.  However, at the address given, [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/installer-i386/](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/installer-i386/),

I'm not sure exactly which files, and in what folder (I assumed [http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/installer-i386/20101020ubuntu136.4/](http://archive.ubuntu.com/ubuntu/dists/precise-proposed/main/installer-i386/20101020ubuntu136.4/)) {the september one...}.  But there are more than just headers and such?

What do I need to do? Have I proceeded correctly? Any guidance is appreciated!

---

### Post by GeForce 9500GT on 2012-09-13
Did you [read this]("https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIInstallProposedUbuntuUpdates?highlight=%28proposed%29%7C%28repository%29")? It might help you a bit.

---

### Post by Alcidious on 2012-09-13
Yes, that link points to the same page I posted about.  As I said, I added the /etc/apt/sources.list and created the /etc/apt/preferences file.  But since I am just testing, and do not want to enable updates, I attempted to run

sudo apt-get install packagename/precise-proposed

From the output above, it did not work.  I suspect I either need to actually download the files given in the link sent to me, in which case Im not sure what to download, or I did something incorrectly or out of step, in which case i don't know how to figure that out.

---

### Post by Frogs Hair on 2012-09-13
I have used proposed updates since 10.04 and have always added the repository from update manager > settings > updates > proposed updates.

---

### Post by Alcidious on 2012-09-15
I added the repository by editing the /etc/apt/sources.list file... but maybe ill double check and try that way just to make sure.  

But after the repository, what am I supposed to do? When I've downloaded other kernels in the past, you just download the images-headers, etc. But in the link to the proposed kernels, there is a whole mess of files... Clues? Directions? Pointers?

---

