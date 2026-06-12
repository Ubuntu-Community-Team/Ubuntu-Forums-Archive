---
title: "Catalyst Installation help"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by scentsamillia on 2013-09-26
ok so I'm trying to install catalyst 13.4 and I've been trying to get all the requirements ([http://www2.ati.com/relnotes/catalyst_linux_installer.pdf](http://www2.ati.com/relnotes/catalyst_linux_installer.pdf))... I've got a Radeon HD 6310 so I can run it apparently if I can just get the other requirements met.  I've got kernel linux 3.5.0-40 generic so I'm good there now when I ran comand line X -version it said this:

X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux josh-ubuntu 3.5.0-40-generic #62~precise1-Ubuntu SMP Fri Aug 23 17:38:26 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-40-generic root=UUID=f67f3390-03d7-45d0-bb37-d1b837dd600b ro quiet splash radeon.audio=1 vt.handoff=7
Build Date: 11 April 2013  11:49:23PM
xorg-server 2:1.13.0-0ubuntu6.1~precise3

So I'm gonna assume I'm running with Xorg 11 (requirements say 6.9-7.6) so I'm not sure if that's a problem...
I haven't been able to find where I can update my glibc because I'm currently using 2.15 apparently and I need 2.2-2.3. And I have no clue about POSIX.... 

Any help would be appreciated.

---

### Post by QIII on 2013-09-26
Hello!

I'm on my cell phone on the train on the way to work right now, so it would be hard to help.

Please stop what you are doing -- you are making it too hard on yourself.

If you wait a while, there are a lot of folks here who can help.

In the meantime, please read through the link in my signature.

Cheers!

---

### Post by scentsamillia on 2013-09-26
Yeah I wasn't really planning to proceed without a little help, considering I don't know a whole lot about Ubuntu.  I was planning to wait and see if someone could help me on here before doing anything more.  I'm trying to install 13.4 because what I read from the release notes it could fix some of the problems I've been having with games crashing and stuff but I don't want to mess up my computer because I don't know what I'm doing...

---

### Post by scentsamillia on 2013-09-26
anyone know what I need to do?

---

### Post by QIII on 2013-09-27
Ah.  Looks like I forgot to get back to you.

The first question  is:  Is there anything you think you need from the proprietary driver  that the default open source Radeon driver is not currently providing?  

The Radeon driver has really gotten very good and should fulfill the needs of the vast majority of users quite well.

The primary benefits of the proprietary driver might be to laptop owners interested in saving some battery time and desktop owners who watch a lot of HD video or play games.

I would recommend just using the Radeon driver for a while to check it out.

If you want the proprietary driver, the first way to try to install it is from the repositories.  There have been some users who report that they get the "Unsupported hardware" watermark, but we can take a look at that if it happens.

If you look at the link in my signature, follow the steps in "2.1.1 Installing via the command line".  For 13.04, you can disregard the warning about fglrx-updates.  That seems to be working these days.  I think if I find that it continues to work in 13.10 after the release and I don't answer too many questions on the forum, I'll edit that section a bit.  Go ahead and use flgrx-updates and fglrx-amdcccle-updates.

Anyway, try that and let us know how it goes.

---

### Post by scentsamillia on 2013-09-28
Well I installed it and everything seemed fine... Till I rebooted and my resolution was 800:600 and I couldn't change it at all.  I removed it and it's back to normal, but I don't know if it's gonna work on my computer.  Oh well it's not worth screwing it up just to try to play some games, and I can already watch HD movies with not problem.

---

