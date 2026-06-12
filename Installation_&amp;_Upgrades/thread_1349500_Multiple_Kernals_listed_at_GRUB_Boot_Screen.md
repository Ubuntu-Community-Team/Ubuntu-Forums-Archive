---
title: "Multiple Kernals listed at GRUB Boot Screen"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Scorpion2k5 on 2009-12-08
I have been Running Ubuntu Linux 9.10 since it came out in early November. I have updated the computer several time and not my GRUB boot screen has several different versions of of the Linux Kernel on it.. Is there anyway to get them off of the screen or do I have to deal with them... I only need the one not 4 or 5 like I have

---

### Post by phillw on 2009-12-08
> **Scorpion2k5 said:**
> I have been Running Ubuntu Linux 9.10 since it came out in early November. I have updated the computer several time and not my GRUB boot screen has several different versions of of the Linux Kernel on it.. Is there anyway to get them off of the screen or do I have to deal with them... I only need the one not 4 or 5 like I have

Yes you can. It is always advised to keep the last version of your kernel, however.

Was it a fresh install of Ubuntu, or an upgrade from 9.04 ?

Phill.

---

### Post by starcraft.man on 2009-12-08
> **Scorpion2k5 said:**
> I have been Running Ubuntu Linux 9.10 since it came out in early November. I have updated the computer several time and not my GRUB boot screen has several different versions of of the Linux Kernel on it.. Is there anyway to get them off of the screen or do I have to deal with them... I only need the one not 4 or 5 like I have

It is a bit bothersome after a while isn't it?

Best way is to uninstall the old ones assuming the latest works for you.

```
sudo apt-get autoremove
```

Usually removes the deprecated packages. If that doesn't say it's removing the linux kernels (i.e. named something like 2.6.31-14/15/16) then you'll have to remove em manually. Easiest way is to search for and remove them with your favourite package manager, synaptic works well or aptitude if you prefer terminal. Just search for 2.6.31 and remove every one except latest kernel number.

---

### Post by phillw on 2009-12-08
I'd use section 7, as detailed here --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Provided, of course you're running Grub2.

Phill.

---

### Post by starcraft.man on 2009-12-08
> **phillw said:**
> I'd use section 7, as detailed here --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Provided, of course you're running Grub2.

Phill.

That is basically what I was saying, the synpatic instructions aren't just for grub 2, but most other commands are (like ones related to turning off memory test).

---

