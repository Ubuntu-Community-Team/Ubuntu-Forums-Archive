---
title: "Installing Gutsy on Raid1"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by fuzzdk on 2008-01-25
Hello.

I have a "real software raid". That will say a software raid created with Gentoo. All partitions that are raided are of type "linux raid autodetect". I have the following mount points for raid devices (I have some more but that is not important):

swap
/

So I do not have anything that is not raided. Now I want to install Gutsy so the old / becomes /olddisk and that I get a new / that is also raid1 (no space problems for this)

What I do not like is that the liveCD doesn't recognize my existing raid1 devices. Will that say that Gutsy once it is installed will also not autodetect raid devices? And how do I get it installed on raid1 in a way so it will boot without problems?

---

### Post by Pumalite on 2008-01-25
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by fuzzdk on 2008-01-26
It is not a "fakeraid" - it is a linux software raid. Every disk is seen as /dev/sda, /dev/sdb.... and the raid devices is seen as (in Gentoo): /dev/md0, /dev/md1,...

I got really surprised that the livecd didn't detect those devices.

---

### Post by fuzzdk on 2008-02-02
I have now installed Ubuntu on my system. It was a little complicated:

1) I had to use the 'alternate desktop CD' since the LiveCD doesn't support linux software raid.
2) The installer skipped installation of a bootloader - so I had to but the 'alternate desktop CD' in rescue mode and install grub.

---

### Post by bonnin on 2008-02-07
I am having an issue when testing the raid1. I can boot of the first drive with out the second drive no problems. But when i try booting off t he second drive with no first drive it boots but gets stuck at the ubuntu screen and then after 5mins or so it loads busy box. Any ideas whats wrong?

---

### Post by fuzzdk on 2008-02-08
Just a guess: Have you installed grub on only the first disk, and have an old bootloader (e.g. grub from an earlier installation) in the boot sector of the second disk?

---

