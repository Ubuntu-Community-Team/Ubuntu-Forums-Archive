---
title: "Wrong kernel version after upgrade to 10.4"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by jjvdgeer on 2010-05-02
I just upgraded to 10.4 LTS. However, I got some errors along the way, some about packages I do not care about (Tex), some about Samba and some about the kernel. I thought there'd be an installation log, so I did not note them down. Haven't found the log yet, though.

After the upgrade, I am on the previous kernel version:

jjvdgeer@ubuntu:~/tmp$ uname -a
Linux ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_6

(I think I should be on 2.6.32-something, right?)

I think I know the cause of my problems. When I installed Win7 on the other partition, of course Ubuntu stopped booting. I found some instructions for 9.10 to repair that and followed those. Unfortunately, it seems this assumed I had grub 2, but apparently I am on grub 1 (probably because I upgraded from previous versions of ubuntu).

In my attempts to repair the resulting mess I did some mounting and stuff and apparantly one of those commands did something nasty. It is some time ago and I do not remember what it was. Anyway, the system booted up once and the next time it had to fsck it's way through the filesystem and found lots of trouble.

Since then I had trouble with updates which did not work at all anymore. I googled each of the problems I encountered and managed to solve most of them. I had a problem upgrading to a later kernel though, which I did not found a solution to.

I thought an upgrade to 10.4 might help here, but it seems it has not.

Since I did not find an upgrade log, I found some other command that gives a bit of trouble, I hope this explains what my problem is. When I do a "sudo apt-get upgrade", I get the output from the attached upgrade.txt.

I notice it finds some grub 2 stuff there as well. I thought I'd removed that...

Any suggestions what to do next? I hope I do not need to do a fresh install, although I'm beginning to wonder if that might be the best option.

Cheers,
Jan-Jaap

---

