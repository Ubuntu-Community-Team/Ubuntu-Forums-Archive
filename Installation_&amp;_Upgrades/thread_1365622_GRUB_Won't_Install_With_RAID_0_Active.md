---
title: "GRUB Won't Install With RAID 0 Active"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by Keithodulaigh on 2009-12-27
Hi,

I installed Ubuntu 9.10 successfully on my custom system a few days ago. I then tried to reinstall today with RAID 0 active.

However it won't install - it says something about GRUB faling to install and wont't be able to boot etc.

I Googled the message and found different suggestions, none seem to work. I've tried:

1. Retry to install
2. Re-create my Raid 0 setup an retry
3. Running "grub" from a terminal in the LiveCD...says it can't find it...

Any suggestions?

Thanks,
Keith

My motherboard is a AMD powered Sapphire Pc-AM3-RS-790G

---

### Post by darkod on 2009-12-27
For motherboard bios raid, so called fakeraid, read here about adding grub2:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Skip the installation procedure and concentrate on installing grub2. Note there are options to do it with alternate install cd or standard desktop (live cd) version.
In general, you should use the alternate install cd for raid support. If you didn't, that's one of the reasons grub won't install (although it can happen with using the alternate cd too in some situations).

---

### Post by Keithodulaigh on 2009-12-28
Thanks for the reply darkod.

What part of that link though is specific to grub2?

I can see options for various versions of Ubuntu but nothing relating to grub2 or Ubuntu 9.10...

I forgot to mention that I don't have a working net connection yet on my new Linux machine so I can't install legacy grub using apt...

Thanks,
Keith

---

### Post by darkod on 2009-12-28
Excellent question. The documentation for grub2 and fakeraid seems to be late. :(
There is one thread for successful install of 9.10 on fajeraid but the person used grub instead of grub2 and used apt-get. You said you have no internet access.
Not exactly sure how you can proceed without internet right now. Raid is not my specialty.

[http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

### Post by Keithodulaigh on 2010-01-05
I decided just to deactivate RAID, it wouldn't work using a Fedora disk either. Anyway it's no big deal really I guess - I've got 9.10 installed now and working smoothly. It's a huge improvement to when I first tried Ubuntu 6 and within such a short space of time...

Thanks a lot for your time Darkod!!

All the best,
Keith

---

