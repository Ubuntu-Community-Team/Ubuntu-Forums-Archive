---
title: "desktop install locking, normal and alt"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by Uaine on 2008-03-29
I have tried installing ubuntu on a compaq presario 7000, and had no luck.  I have used ubuntu-7.10-desktop-i386.iso and ubuntu-7.10-alternate-i386.iso (both verified as having no defects).  Memory test also passed with no problems.

Using the standard install, the install freezes at 95% when it is looking for packages to remove.

Using the alternate install disc, I tried a normal install, then a command line system.  Both attempts locked at 83% (installing the kernel - retrieving and installing linux-generic...).

I'm completely at a loss, and I've tried every possible solution I've seen in the forums.  I would greatly appreciate any suggestions.

---

### Post by Uaine on 2008-03-30
Well, I figured this one out for myself, I think.  This computer was a fairly new acquisition, and I hadn't had much time to spend with it.  I was tinkering with the bios for a while, and it actually managed to lock up there too - so, not a problem with Ubuntu, problem with the computer.

Some searching other forums led me to think that the problem might be overheating, so I cracked open the case, aimed a big fan right at the CPU, and tried again, and it actually worked!

Aiming a fan at an open case isn't really tenable for the long term, so I'll have to find out why it's not cooling properly.  Anyway, thanks to those of you who took the time to read my post.

---

### Post by warp99 on 2008-03-30
You may have to install use the noapci parameter in the kernel line or maybe a different parameter depending on your system. The guide should be helpful:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

