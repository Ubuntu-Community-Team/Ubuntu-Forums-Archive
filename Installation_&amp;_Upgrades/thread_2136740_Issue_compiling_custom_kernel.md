---
title: "Issue compiling custom kernel"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by cchamberlain on 2013-04-18
Hello,

I recently screwed up my FreeBSD server by deleting the /etc/defaults/ directory and now I am trying to recompile my Ubuntu kernel (on my laptop) with UFS write support so that I can retransfer the /etc/defaults/ directory files back onto my FreeBSD box via a USB flash drive.  To recompile my kernel with this support turned on I've been following [http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/](http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/) but have run into an issue.

After I tell it to compile with make-kpkg it rolls along for a while until it hits the following error - 
> 
make[3]: *** No rule to make target `firmware/bnx2x/bnx2x-e1-7.8.2.0.fw', needed by `__fw_modbuild'.  Stop.


I found one thread documenting this issue at [http://ubuntuforums.org/showthread.php?t=2115317&page=2](http://ubuntuforums.org/showthread.php?t=2115317&page=2) but since I didn't pull the source from git, I can't simply do the git update that they suggest.

Definitely would appreciate anyone who could point me in the right direction on this as right now my home file/media server is completely out of commission.

Thanks in advance!

---

### Post by matt_symes on 2013-04-18
Hi

Where did you get the source from ?

I would just

```
sudo apt-get source ......
```

Then configure and compile from there.

That's what i am currently doing.

Kind regards

---

### Post by midnightramen on 2013-04-18
just to piggyback on this thread, i usually follow the instructions here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I usually have to recompile once in a while to support a specific sound card.

---

### Post by cchamberlain on 2013-04-19
Thanks guys, I'll give those suggestions a shot and see if I can get it working.

---

