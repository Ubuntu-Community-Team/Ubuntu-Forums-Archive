---
title: "Can't complete installation of lubuntu"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by skorupion on 2020-04-25
So I am trying to install lubuntu 19.10 amd64, but before it I had lubuntu 16.4 i386 and it shows me an option of replacing a partition, but I can't go to the next step (the next button is Grey) what should I do?
[https://zapodaj.net/fefc1726a220c.jpg.html](https://zapodaj.net/fefc1726a220c.jpg.html) picture of my screen

---

### Post by CelticWarrior on 2020-04-25
Assuming you already have backups like you should, please select "erase disk" instead.

---

### Post by skorupion on 2020-04-25
Ain't working [https://zapodaj.net/ec0ec84dd3583.jpg.html](https://zapodaj.net/ec0ec84dd3583.jpg.html)

---

### Post by CelticWarrior on 2020-04-25
First of all, any special reason for you to post upside down pictures?

Now, regarding the issue itself, the drive is probably failing.
In the live session you can open Disks and check the drive's health.

---

### Post by skorupion on 2020-04-25
Sorry for posting it upside down second, I was able to install the old lubuntu and it was working, plus I am unable to find the section of where I can see the drive health, but it should be fine.

---

### Post by Impavidus on 2020-04-26
Instead of replacing a partition, have you tried manual partitioning? It should allow you to do the same thing, without the computer guessing what you want.

Is there any special reason why you install 19.10? It only has 3 months of support left. 20.04 has 3 years of support. Lubuntu 16.04 reached end of life a year ago.

---

### Post by guiverc on 2020-04-26
The error reminds me of [https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1864787](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1864787) which is mentioned in the Lubuntu 20.04 release notes (refer [https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/)) in the *Known Bugs* section. 

I'd suggest the work-around that is described there "*Replace Partition on Certain Partition Schemes With Calamares Fails***" **(or from the aforementioned bug report, though it'll be easier to understand the release notes I bet).

There are a couple of issues with the `calamares` installer that certain hardware & partitioning can 'trigger', I'm hoping that *workaround* will resolve it for you.  FYI: The text mentions ext4 & btrfs being tested, other file-systems were tested too (eg. xfs, reiserfs..) so use whichever you prefer.

PS: I know you're asking about 19.10, I recall issues occurring there too, but it was awhile ago so the *focal* [20.04] issues are more prominent in memory than *eoan* [19.10] ones (about four *bugs* exist, all are similar)

---

### Post by CelticWarrior on 2020-04-26
And 19.10 has only a few months of support left so there's really no point in installing it now.

---

