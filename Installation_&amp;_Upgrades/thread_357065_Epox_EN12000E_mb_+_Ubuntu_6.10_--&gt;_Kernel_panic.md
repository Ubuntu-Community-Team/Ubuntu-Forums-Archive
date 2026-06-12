---
title: "Epox EN12000E m/b + Ubuntu 6.10 --&gt; Kernel panic"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by ld99 on 2007-02-09
Hi all,

Not too sure what is wrong here. I am trying to set up a file server in my home network, and I am using the following hardware:

[EPIA EN12000E motherboard ]("http://www.via.com.tw/en/products/mainboards/mini_itx/epia_en/")
A generic memory stick (1Gb)
A few large HDDs

The motherboard is one of those ones with everything integrated, including the CPU itself. I prefer it because it uses no fan, low power consumption, and since it is only gonna have a software raid, and serving files, I figured it should be good enough.

I actually already has a server running with the same hardware (except this time my HDDs are a lot bigger). I used Ubuntu 6.06 server CD, and it has been working fine.

Anyway, I tried installing Ubuntu 6.10 using the server CD, but it ended up with a few error messages, and a kernel panic. I tried checking the CD, same problem. Tried the normal Ubuntu 6.10 CD (i.e. the one with desktop), same problem. The initial menu showed up fine, but kernel panic occur very quickly if I select "install" or "check cd".

But the memtest utility runs fine. And the server CD definitely works because I have used that same CD to install another box (with more traditional hardwares).

Any ideas? At the moment I am using the old 6.06 server CD to install the server. But it is just a little disturbing if 6.10+ will not be compatible with this motherboard.

Thanks...

---

### Post by wec on 2007-03-12
I just installed ubuntu 6.10 from the LiveCD (after first moving it to a USB stick) and got the same problem with **Kerner Panic**. It can be fiixed by adding **acpi=force** as a kernel start parameter.

---

