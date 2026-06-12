---
title: "can't repair jfs filesystem"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by b9anders on 2010-04-15
I run ubuntu on ext3 but I have some other partitions formatted with jfs.

After a system crash I am having trouble mounting it. However, when I run fsck on it (which I expect would fix it), I get:

```
fsck from util-linux-ng 2.17.2
fsck: fsck.jfs: not found
fsck: Error 2 while executing fsck.jfs for /dev/sda6
```

I searched the repos for the needed utils, found it and ran:

sudo aptitude install jfsutils

However, aptitude wants to remove 
linux-headers-2.6.32-19{u} 
linux-headers-2.6.32-19-generic{u}

Which I am pretty sure is a bad idea. I don't really understand why linux-headers would conflict with jfsutils when it doesn't have them included.

Any suggestions on what to do to get fsck.jfs working?

---

### Post by psyke83 on 2010-04-15
> **b9anders said:**
> I run ubuntu on ext3 but I have some other partitions formatted with jfs.

After a system crash I am having trouble mounting it. However, when I run fsck on it (which I expect would fix it), I get:

```
fsck from util-linux-ng 2.17.2
fsck: fsck.jfs: not found
fsck: Error 2 while executing fsck.jfs for /dev/sda6
```I searched the repos for the needed utils, found it and ran:

sudo aptitude install jfsutils

However, aptitude wants to remove 
linux-headers-2.6.32-19{u} 
linux-headers-2.6.32-19-generic{u}

Which I am pretty sure is a bad idea. I don't really understand why linux-headers would conflict with jfsutils when it doesn't have them included.

Any suggestions on what to do to get fsck.jfs working?

As long as kernel 2.6.32-21 in installed and works correctly on your system, you can safely allow the operation.

---

### Post by xebian on 2010-04-15
> **b9anders said:**
> I run ubuntu on ext3 but I have some other partitions formatted with jfs.

After a system crash I am having trouble mounting it. However, when I run fsck on it (which I expect would fix it), I get:

```
fsck from util-linux-ng 2.17.2
fsck: fsck.jfs: not found
fsck: Error 2 while executing fsck.jfs for /dev/sda6
```

I searched the repos for the needed utils, found it and ran:

sudo aptitude install jfsutils

However, aptitude wants to remove 
linux-headers-2.6.32-19{u} 
linux-headers-2.6.32-19-generic{u}

Which I am pretty sure is a bad idea. I don't really understand why linux-headers would conflict with jfsutils when it doesn't have them included.

Any suggestions on what to do to get fsck.jfs working?

If you don't have a need for the headers why not?  You need them only when you compile modules.

Or you can use apt-get to install which will only suggest you to run apt-get autoremove.

Or just download the jfs*.deb and then do dpkg -i jfs*.deb

---

### Post by b9anders on 2010-04-15
cheers. thought the headers were important.

---

### Post by psyke83 on 2010-04-15
> **b9anders said:**
> cheers. thought the headers were important.

The headers are important for compiling kernel modules - so if you use the restricted fglrx or nvidia drivers, for example, you should always have the headers installed.

However, version 2.6.32-19 is an outdated kernel, so it's no big deal to remove these packages - as long as you have updated your system with the newer kernel (and its headers).

---

