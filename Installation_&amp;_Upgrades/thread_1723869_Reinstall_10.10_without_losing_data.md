---
title: "Reinstall 10.10 without losing data"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by IsaacSchwarz on 2011-04-07
Ok, so I upgraded from 10.10 to 11.04 a couple of days ago, and I really don't like it. I want to reinstall Ubuntu 10.10, is there a way to do this without losing everything? By the way, My computer is dual boot with Windows XP.

---

### Post by wilee-nilee on 2011-04-07
> **IsaacSchwarz said:**
> Ok, so I upgraded from 10.10 to 11.04 a couple of days ago, and I really don't like it. I want to reinstall Ubuntu 10.10, is there a way to do this without losing everything? By the way, My computer is dual boot with Windows XP.

You can't downgrade safely, your best bet is backing up your needed stuff and reinstall Maverick. You might want in the future to just clone the distro before you do this, or save all the install information, from synaptic, or the file in home that saves this stuff. I forget the file name here, my basic method is never upgrading a distro, and keeping my stuff backed up and imaged on a external HD, I do fresh install every time it is much faster for me.

Here is a link to clonezila, if you have an image of the whole partition or partitions, you can just slip it back in, you can also clone the XP with this and do the same.
[http://clonezilla.org/](http://clonezilla.org/)

Your aware of the classic desktop choice at the login with Natty I assume.

---

### Post by IsaacSchwarz on 2011-04-07
Thanks, I did try the classic Ubuntu option, but everything is messed up (such as none of the windows having title bars).

---

### Post by wilee-nilee on 2011-04-07
> **IsaacSchwarz said:**
> Thanks, I did try the classic Ubuntu option, but everything is messed up (such as none of the windows having title bars).

Have you tried in the terminal.
compiz --replace

This restarts compiz which is okay if it brings back the title panel, and doesn't crash. Have you tweaked compiz? I ask this as I had everything working until I messed around with compiz and tweaked it to no title as well.

---

