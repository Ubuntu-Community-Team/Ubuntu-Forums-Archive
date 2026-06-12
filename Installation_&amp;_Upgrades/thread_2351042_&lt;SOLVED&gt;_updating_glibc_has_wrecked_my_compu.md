---
title: "&lt;SOLVED&gt; updating glibc has wrecked my computer"
date: 2017-01-30
forum: Installation &amp; Upgrades
---

### Post by TheBigH on 2017-01-30
Hi all,
I am running Ubuntu 15, and needed to update glibc to at least version 2.23 to run some software for work. The repos only go up to version 2.21, but the newest seems to be 2.24. I tried adding ppa:ubuntu-toolchain-r/glibc to my repositories, but installing that way gave me 404 errors. So I tried downloading and compiling from source. I got as far as "make install", when it crashed with a segfault. After that, *anything* I tried running from the terminal segfaulted.

I then tried rebooting the computer. Now I can't even boot up. I just get kernel panics, even in recovery mode.

How do I fix this?

Thanks.

---

### Post by ian-weisser on 2017-01-30
Three big problems.

1) Ubuntu 15.04 and Ubuntu 15.10 (you did not specify) are both EOL. No support for them. Please consider installing a supported version of Ubuntu. We can help you better if you do.

2) glibc is a vital component of your OS. Don't tinker with it. If you do, you are likely to break your system...which seems exactly what you did. Upgrading versions in a linux distro is possible...if you have the proper skills, good backups, and plenty of time for troubleshooting.

3) Avoid upgrading Ubuntu in a Windows-like way (running first to PPAs, upstream websites, or other non-Ubuntu sources). Packages in Ubuntu are compiled to function with a specific release/version. When you download from PPAs and other non-Ubuntu sources, the versions don't match anymore, and you may encounter significant unexpected breakage.

glibc 2.23 is available in Ubuntu 16.04 LTS.
glibc 2.24 is available in Ubuntu 16.10 and will be in Ubuntu 17.04 when it is released.

We gently suggest you preserve your data and install 16.04.

---

### Post by TheFu on 2017-01-30
Ian nailed it.  Everything. 1, 2, 3. All correct.

libc is the core for almost all programs running on the system. Basically, if you swap out a libc version, then **every** program needs to be relinked (and maybe recompiled) to work with the new version.  In the Ubuntu world, that mean "new release."  16.04 is an LTS release. All the others are 9 months of support only from the release date.  Stay on an LTS, if you can. If not, plan to migrate to the next release every 6 months.

Ubuntu release support :  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  basically, support for 15.10 ended last July.

At this stage, the solution is to either roll back to the correct libc version or install a new release that has the version you want/need.  Backup anything you want to keep first, regardless.

---

### Post by TheBigH on 2017-01-31
Migrated to Linux Mint 18.1

---

### Post by mörgæs on 2017-01-31
Thanks for an attempt at marking the thread solved but please use Thread Tools.

---

