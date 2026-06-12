---
title: "Kernel Upgrade - Borked System. My fault??"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2010-08-08
Long story short, a month ago I got a kernel update via update manager, so I installed it. It gave me an error, but I ignored it. I noticed when I would install applications from the software center, it would always install, but I always got an error it failed to install - even though the new item appeared in the menu and worked fine.

Then came a new kernel update, so I installed it, thinking it would solve the problem. It didn't. Again, I was lazy and ignored it. Weeks pass, and there's another kernel update. Fearing I'd have the same issue again, I boot to an older kernel (the first that came with Ubuntu 10.04) and removed the other kernels from synaptic. I noticed when doing this, it also removed linux-generic-headers, or whatever it is.

I went ahead with it, and sure enough, problems pursued. I read up on the issue and tried a number of things and received a ton of help from other users in the Ubuntu IRC chat. But I didn't get anywhere.

So basically what happened is, I had a problem w/ update manager with a kernel, and got 2 newer kernels since then that backfired, and yet a newer kernel was available, so to avoid issues I uninstalled old kernels and it took out the corresponding kernels + linux generic headers. 

I've since reinstalled Ubuntu, but I'd like to know what exactly happened. Was removing the kernels a bad idea? Was anything I did make things worse? I'm just trying to understand what happened and what I could have done to fix it, not so much *how* to fix it now since I already reinstalled.

(btw have I ever mentioned how nice it is having partitions split? It took Ubuntu exactly 8 minutes to install and I was back in business with all of my personal data intact).

---

### Post by Rubi1200 on 2010-08-08
Since this is after the fact, I think that tracking down the cause could be pretty much nigh impossible. If you had log files with error messages to share etc. that would be different.

And who knows? Perhaps you accidentally deleted the wrong linux-image or linux-header file? Or maybe there was some other issue at play?

Bottom line is that you reinstalled and everything is working!

:)

---

### Post by Roasted on 2010-08-08
> **Rubi1200 said:**
> Since this is after the fact, I think that tracking down the cause could be pretty much nigh impossible. If you had log files with error messages to share etc. that would be different.

And who knows? Perhaps you accidentally deleted the wrong linux-image or linux-header file? Or maybe there was some other issue at play?

Bottom line is that you reinstalled and everything is working!

:)

I agree. But the fact is, this happened when I was not screwing around. It happened by clicking "install updates" in update manager. And why? What for? I have no idea why the issue surfaced. SURE - maybe me uninstalling stuff made it worse, but I'm trying to understand why it happened in the first place...

---

### Post by ingeva on 2010-08-08
> **Roasted said:**
> I agree. But the fact is, this happened when I was not screwing around. It happened by clicking "install updates" in update manager. And why? What for? I have no idea why the issue surfaced. SURE - maybe me uninstalling stuff made it worse, but I'm trying to understand why it happened in the first place...

Just a comment:
After I upgraded to 2.6.31-22, one of my computers won't start properly because the disks are not found. It's left completely disk free but has only a RAM Disk, and can't do much.

There are two IDE controllers that are used only for CD/DVD, and two SATA disks on controllers numbered 2 and 3. On the computer with only SATA controllers there's no problem.
This is evidently a but introduced by the latest kernel. 10.04 reports an error after boot and suggests a change of a BIOS setting that does not exist.  So 10.04 won't run either - but who cares... it's been so tampered with that I wouldn't use it anyway! :(

---

### Post by alphacrucis2 on 2010-08-08
> **Roasted said:**
> I agree. But the fact is, this happened when I was not screwing around. It happened by clicking "install updates" in update manager. And why? What for? I have no idea why the issue surfaced. SURE - maybe me uninstalling stuff made it worse, but I'm trying to understand why it happened in the first place...

In you initial post you said:

> I got a kernel update via update manager, so I installed it. It gave me an error, but I ignored it. I noticed when I would install applications from the software center, it would always install, but I always got an error it failed to install - even though the new item appeared in the menu and worked fine.

It is very possible that this "error" was significant but without knowing exactly what the error was then it is rather impossible to diagnose such a problem.

---

### Post by Roasted on 2010-08-09
Is it possible to remove kernel updates from update manager like Linux Mint does?

---

