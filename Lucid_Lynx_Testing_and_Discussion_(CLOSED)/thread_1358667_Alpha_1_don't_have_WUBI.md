---
title: "Alpha 1 don't have WUBI"
date: 2009-12-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-12-18
Karmic WUBI was flaky, was wanting to test Lucid's WUBI. To my surprize there is none. Does anyone know if (1) If it's gonna come out in Alpha2?, (2) I have to wait awhile?, (3) WUBI is gone for good?

---

### Post by plun on 2009-12-18
Well, that's maybe a problem....

File a bug  !

[https://bugs.launchpad.net/wubi](https://bugs.launchpad.net/wubi)


--

---

### Post by meborc on 2009-12-19
> **theozzlives said:**
> Karmic WUBI was flaky, was wanting to test Lucid's WUBI. To my surprize there is none. Does anyone know if (1) If it's gonna come out in Alpha2?, (2) I have to wait awhile?, (3) WUBI is gone for good?

wubi is not gone... probably they will wait until beta before adding wubi support, it is not exactly a developers tool... 

i installed wubi (karmic) on my work machine, because i was not allowed to mess with partitions (they obviously had heard about my special ability of killing data off disks:)). it installed 64 bit ubuntu, and it works GREAT

i have had absolutely NO problems with that install, one of the best i have seen yet!

---

### Post by garvinrick4 on 2009-12-21
Use Karmic and at Terminal:

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade


That should bring you up to date.

---

### Post by theozzlives on 2009-12-21
> **garvinrick4 said:**
> Use Karmic and at Terminal:

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade


That should bring you up to date.

I don't want to upgrade Karmic WUBI. I want to test Lucid's WUBI, it should be a part of Alpha. All testers are not developers. Anyhow, I filed a bug just incase.

---

### Post by garvinrick4 on 2009-12-21
It attaches itself to Windows dos4grub and boots into the Linux kernel and plants itself in a folder in the C: drive of Windows.
I guess it should be in the LIVE CD it was in  Karmics because I have 1 install on a Vista machine of 9.10 and used it as a bug tester for Karmic. Seems as though it would be there doesn't it.
Karmic version had fits with reboot and shutdown bugs wonder if it
is the same. Was a nice way to learn Linux, could just uninstall when I screwed it up and reinstall clean in 15 minutes or so. 
Anyway anyone want to upgrade from Karmic to Lucid there is the code 
in previous post, misunderstood the thread and was repremanded by the starter.

---

