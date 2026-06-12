---
title: "SetUp Linux on my USB HardDrive"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by derby007 on 2006-11-02
Can i set up another Linux operating system on my USB 2.0 250GB hard drive, or even on my main drive? ie. i have Ubuntu Dapper & Kubuntu, by just selecting which session/interface i want, but now i want to try another Linus OS, or another version of Ubuntu, etc. EG: do i need another swap partition?

---

### Post by kidders on 2006-11-02
Hi there,

You can install as many OSs as you like :-)

If you have more than one hard disk, you should probably be using multiple swap partitions already, but you don't really _*need*_ more for a second Linux install, since they can't both use it at the same time.

You won't be able to hibernate a PC that's sharing swap space with another OS however, for obvious reasons.

Any help?

---

### Post by derby007 on 2006-11-02
You can install as many OSs as you like :
do u mean Linux OS's ?

So, i can use the ONE Swap for a 2nd installation of another Linux OS....is this right?

Will my boot up give me the option of choosing which one, or does this depend on the OS i'm installing?

---

### Post by kidders on 2006-11-02
> **derby007 said:**
> You can install as many OSs as you like :
do u mean Linux OS's ?

Installing multiple Linuxes is easier than other Windowses or OSXes (are any of those even words!? :confused: ). So don't worry ... putting Ubuntu on with another flavour of Linux won't drive you crazy and make you cry ... it should just work :-)

> **derby007 said:**
> So, i can use the ONE Swap for a 2nd installation of another Linux OS....is this right?
You can, provided none of your Linuxes will need the swap when they're not actually running. Having said that, it is often simpler just to make more swap. After all, you won't need much of it.


> **derby007 said:**
> Will my boot up give me the option of choosing which one, or does this depend on the OS i'm installing?
You can configure your bootloader (I assume you have one already) to let you choose what you want to boot into.

---

