---
title: "Help! Partitions and other problems"
date: 2017-02-19
forum: Installation &amp; Upgrades
---

### Post by epicdragon44 on 2017-02-19
Hello everyone! I'm in a bit of a fix and I'd like some help ASAP.

I've been playing around with Linux for about a year, and I know most of its ups and downs. Recently, I started using GParted to edit my partitions, and no problem so far.

About five weeks ago, I installed Fedora and wiped the hard disk clean for a fresh install. It was a great experience and is a great distro. However, this morning, after reading some reviews I took a fancy to Xubuntu. Prior to this, I'd only tried a few other distros (in total that is Fedora, Ubuntu MATE, Linux Mint MATE, Slax, Lubuntu, Debian, and MX Linux, which, by the way is a really great distro too) and I've never experienced any problems before. I've also done a clean install of Linux Mint MATE on a friend's Toshiba laptop before by wiping the hard disk, and then re-installing Windows 7 and dual booting it by setting up some partitioning first. However, this morning, when I tried to install Xubuntu, it didn't even recognize that Fedora was even there, and so I couldn't just select the option that says "Run side-by-side" or something like that.

Strange.

I used Live GParted to try and edit my Fedora partition, but then I found I couldn't shrink it and make free space for my new partition, because *all my space in the partition was used. *That's right. [I]My entire hard disk was somehow being used by Fedora, and I couldn't shrink it!
[/I]So now I'm wondering; is it a glitch? Has anyone seen this before, where my whole hard disk is used and I can't shrink the partition? If so, can you help? It's an old HP G62 by the way.

Thanks!

---

### Post by oldfred on 2017-02-19
Fedora, I believe uses the LVM partitioning.
That is Logical Volume management. Or you have a physical partition or two /boot  & LVM if with Ubuntu. And then you create logical volumes inside the LVM physical partition.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

LVM has some advantages if used for entire drive, I have never used it so do not know details. Those that want to multiple boot often choose to install Fedora in a physical partition like the default Ubuntu install.

---

### Post by RobGoss on 2017-02-20
I'm a bit confused about your post, you stated your whole hard drive was using your space, if Fedora is the only distribution on this machine why wouldn't it use the entire disk space

It might be better to just create a unallocated partition and try installing Xubuntu on it that way

When your run the live installer do you get the option to choose something else?

---

### Post by epicdragon44 on 2017-02-20
Yes, I do get the option to choose something else.

Sorry for the confusion; it says that out of the partition that Fedora owns, it has used all of the available space, but I know for a fact it didn't. It also doesn't recognize any operating system already on the laptop during installation

---

### Post by oldfred on 2017-02-20
That is how LVM works, it uses all the physical partition and the logical partitions are all inside it.

You probably can also install Ubuntu inside the LVM to another /mapper/... LVM volume.

Either fully use LVM or erase the LVM and use only standard partitions.

---

### Post by epicdragon44 on 2017-02-27
Oh! I see. Thank you!

---

