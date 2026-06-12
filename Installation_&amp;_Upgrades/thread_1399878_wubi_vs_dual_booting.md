---
title: "wubi vs dual booting"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by UncleMonty on 2010-02-06
What are the pros and cons of using wubi instead of dual booting?

---

### Post by llawwehttam on 2010-02-06
WUBI is installed inside windows and therefore depends on windows. I would dual boot every time.
If you get a kernel update in wubi it can kill both systems and it is quite unstable.

You could always use virtualbox as a third option.

---

### Post by MelDJ on 2010-02-06
think of wubi as installing ubuntu as an application in windows.
if windows crashes, it too is gone.
and it doesn't get its own filesystem. so you don't get the benefits of ext

---

### Post by OrangeCrate on 2010-02-06
Agreeing with the previous posts, I think Wubi is generally used just to check out a distro, rather than being considered as a long-term install option.

IMO, dual booting is always the best option. See here for some guidance, if your interested in trying it:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by lidex on 2010-02-06
> **OrangeCrate said:**
> Agreeing with the previous posts, I think Wubi is generally used just to check out a distro, rather than being considered as a long-term install option.

IMO, dual booting is always the best option. See here for some guidance, if your interested in trying it:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

Absolutely. Call it a preview ;)

---

### Post by 2hot6ft2 on 2010-02-06
I've never even tried a wubi install. I just can't see installing Ubuntu inside Windows and having Windows crash taking Ubuntu with it. Dual booting is the way to go. I dual and triple boot my machines if they even have Windows at all.

---

### Post by minws on 2010-02-06
Hi,

Wubi is unstable, don't think about upgrading the kernel and you will not be able to boot to ubuntu. I don't agree though that is for testing, for testing is the live cd, installation inside virtualbox or a live usb stick. I personally use wubi because I like to keep my windows system as it is,as ubuntu are unstable sometimes, meaning that is not 100% that your system is going to be the same after upgrade. So I'm using the great tools from the linux community and a 99% great os and if the system crashes I'm reinstaling from inside windows.

---

### Post by Mark Phelps on 2010-02-08
While I personally advocate NOT using Wubi (for all the reasons already cited), you should be aware that one of the Advantages of using Wubi is that you don't have to mess around with partitioning -- and running the risk of corrupting Vista (or Win7) and rendering them unbootable.

If you do decide to dual-boot, search the forums for threads on this first and be sure to use the Vista (or Win7) builtin Disk Management utility to shrink the OS partition.  Don't fall for the temptation of using the Ubuntu installer to do a side-by-side installation that involves resizing your MS Windows OS partition.

However, that said, if you're using Windows XP, you should be OK with letting the Ubuntu installer resize your OS partition.

---

### Post by Alex Libman on 2010-02-08
I disagree with the terminology used on this thread.  [Wubi]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29") is a way to install Linux for [multi-booting]("http://en.wikipedia.org/wiki/Multi_boot") with Windows (dual, triple, or otherwise).  The alternative to multi-booting is installing only one host OS, and running any other OS'es through an [emulator]("http://en.wikipedia.org/wiki/Emulator") instead, which is not how Wubi works.  What I think this thread compares is using dedicated [partitioning]("http://en.wikipedia.org/wiki/Disk_partitioning") vs the [loopmounted device]("http://en.wikipedia.org/wiki/Loop_device") method that Wubi allows.

The loopmount method is easier for new users to set up, because it doesn't resize or create any physical partitions, but it has some minor stability and speed disadvantages, and hibernation is not supported.  It also creates complications in cases of fragmentation, or if you ever decide to resize or uninstall your Windows partition.  Having OS'es on different partitions is also great for [ghosting]("http://en.wikipedia.org/wiki/Disk_cloning") and [virtualization]("http://en.wikipedia.org/wiki/Full_virtualization") purposes as well.

So I think that intermediate-level users should try something like [Parted Magic]("http://partedmagic.com/") (FOSS) or the [EaseUs Partition Manager]("http://www.partition-tool.com/personal.htm") (proprietary FreeWare) to shrink their Windows partition instead.

---

