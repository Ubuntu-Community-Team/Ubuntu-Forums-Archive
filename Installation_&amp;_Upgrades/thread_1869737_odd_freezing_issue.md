---
title: "odd freezing issue"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by cavanholi on 2011-10-26
First of all, I'm not sure if this is the proper place, if it is not, please, forgive me.

Ok, I bought recently a netbook accer aspire one (choice by the cheapest) which came with win 7 starter.

As I do not like windows but couldn't remove it I installed, at the time the latest version, ubuntu 11.04.
First using Wubi, experiencing lots of freezing, than properly installing it, the problem became less frequent.

So I gave up a while until Ubuntu Oneiric was released.
Installed, updated, everything seemed fine. And yesterday the problem back.

I've looked in syslog, dmesg, kern.log and the only things I saw that were 'wrong' was a warining about about bluez and an erro while trying mount /home=remount.

But this happen when it start properly as well, not only when it freezes at login screen (even in text mode).

I boot in windows to look for a solution and when restart to boot in ubuntu it did not freeze at all.

So this morning I made a test:
1- Boot ubuntu first: it freezes.
2- Login in windows and restarting
3- Boot ubuntu again without any problem.

My conclusion from this is that I can only start ubuntu after boot windows first, which doesn't make sense for me at all.
So, any one have any idea, experienced anything similar because I don't know what to do!

---

### Post by dino99 on 2011-10-26
i hope you does not still run wubi but a real install

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

what give: sudo jockey-gtk

you should have your graphic driver activated and in use.

---

### Post by cavanholi on 2011-10-26
> **dino99 said:**
> i hope you does not still run wubi but a real install
[
yes, I'm using a real install since 11.04.
As for the graphic driver, it's not active 'cause when I've tried activating it (ATI Radeon) it screwed up everything to the point that a second install (erasing the whole content of the root directory and also creating, this time, a partition for /home) was faster than trying to solve it.

As I said before, this really doesn't make sense. How possibly booting in windows first will make a reboot to ubuntu work when boot direct to ubuntu won't.

(I've done this test again since I posted, same result!)

---

