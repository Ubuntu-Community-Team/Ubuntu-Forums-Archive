---
title: "Install Ubuntu on 2 SATA2 harddisks with RAID 0"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by kanduvisla on 2007-02-28
Hello,

I'm very new to the whole Ubuntu and Linux thing, but I gave it a try on my laptop. It works very nice and I'm very impressed by it. So impressed that I want to install it on my desktop PC.

But there something goes wrong. I've got 2 SATA2 harddisks (149 gb) configured as RAID0 (striping). I've got 4 partitions: Windows, Mr. Data, Documents and Vista. I want to delete the contents of my 'Vista'-partition and install Ubuntu over it (yeah! :))

But the installer sees my harddisks as 2 harddisks with each 149 gig unallocated space. Does anyone know what the problem is? Or how I can make it so that I can install Ubuntu on this partition?

---

### Post by Corvo78 on 2007-02-28
I think that this means that you have an onboard RAID which is not entirely hardware based.

So, your onboard RAID is a mix of hardware and software.
You probably needed to load a corresponding driver to be able to installl Windows onto this Raid array.
Since it is not entirely hardware based (and thus not transparant as 1 drive to the OS), people also call it **"FakeRaid"**.

See this help entry for more info: _[help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)_


Beware though, I've tried installing onto a FakeRaid - and gave up!!
[i](I wasn't going to spend more then 8 hours (re)trying installing Edgy.
So, I ended up buying an extra hardware RAID controller, from 3ware, and finally had a silky smooth install.)[/i]

---

