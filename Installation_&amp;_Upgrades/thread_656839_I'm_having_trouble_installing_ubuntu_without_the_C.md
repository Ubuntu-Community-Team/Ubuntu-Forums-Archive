---
title: "I'm having trouble installing ubuntu without the CD. Help?"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Dec_lan on 2008-01-03
Hi, this is my first post. I checked the similar threads, and none of them are my problem.

I have an old HP laptop. It has about 40 billion hardware problems, but manages to run alright with Windows XP. It has 10GB HD, 128 MB RAM, and a pretty shitty processor.

But here's the catch...one hardware problem does matter. It's fan is dead, which resulted in the CD drive being burnt out a long time ago. It doesn't read CD's at all.

So I googled and found this page: [http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

Unfortunately, the links are broken. However, I went a few directories back, and found the same files, kind of. All in all, I really have very little idea what I'm doing here, but I'd like Ubuntu on this computer because it's the only one I can afford to have it on.

Can anyone help? Thanks!

---

### Post by ~LoKe on 2008-01-03
How about trying [this](https://wiki.ubuntu.com/install.exe/Prototype)?

---

### Post by logos34 on 2008-01-03
The link Loke gave you is for a Wubi install--Ubuntu runs INSIDE windows on a loopmounted ext3 filesystem.  If you decide you want to keep ubuntu you can convert it to a permanent install on a dedicated partition with LVPM.  

However, if you've already decided you want to dual-boot ubuntu on it's own, separate partition then I'd opt for UNetbootin.

---

### Post by Dec_lan on 2008-01-03
Thanks, Loke! That's great.

So, what you're telling me now is that if I want to boot Ubuntu permanently (not dual boot, only ubuntu), I'd have to make a partition and use that LVPM thing while I'm inside Ubuntu? Do I have to make a partition if I plan to use all the HD space for ubuntu?

Thanks!

---

### Post by Niniel on 2008-01-03
WinXP with 128 MB of RAM? Wow, that's... brave.
Not sure you'll enjoy Ubuntu proper a lot with that kind of RAM, you may want to look for alternative, more lightweight distributions. 

If you have USB on your box, there are ways to get Linux installed via USB stick.

---

### Post by logos34 on 2008-01-03
> **Niniel said:**
>  you may want to look for alternative, more lightweight distributions. 

yes, good point, like Xubuntu or something that uses fluxbox wm

---

