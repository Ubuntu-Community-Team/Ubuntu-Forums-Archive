---
title: "upgrade dapper kernel to 2.6.17?"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by mrweirdo on 2006-07-21
Is there any easy way to upgrade the default kernel in ubuntu dapper from 2.6.15 to 2.6.17. also how to do i get it with smp support which i need for my system. there is some sort of a problem with .15 that causes the system to freeze using ubuntus 2.6.15 smp kernel when under heavy network loads. Hence one reason I want to try upgrading. Is it posible to download deb packages somewhere to upgrade or do I have to through the hassle of compiling?

---

### Post by nalmeth on 2006-07-21
You would have to compile it I believe, and I think it will be quite a task.

I'm not on Edgy yet, but that is the only place I would see it being doable in a practical sense.

Your freezing problem is odd, can you be sure it is due to the kernel? Have you found that there is a bug related to this, or have you filed one of your own?

---

### Post by mrweirdo on 2006-07-21
ya I have filed a bug report on it here
[https://launchpad.net/distros/ubuntu/+source/linux-686-smp/+bug/53605](https://launchpad.net/distros/ubuntu/+source/linux-686-smp/+bug/53605)

its definately related to the kernel because if i use the non smp kernel it goes away. Its definatly related to tthe smp kernel. Not sure if its just ubuntu or that particular version of linux 2.6.15. Also i can say before ubuntu i had windows 2003 on the same hardware without issues and I have tested for hardware problems with programs like memtest, etc since this issue popped up and the system passes those perfectly.

---

### Post by nalmeth on 2006-07-21
Good call on the bug report

One distro I know of using the 17 kernel right now is Knoppix, you should give it a shot. It will be much easier than the trouble of getting the 17 kernel on Dapper, or using unstable Edgy

---

### Post by neveceral on 2006-07-21
no, [http://www.ubuntuforums.org/showthread.php?t=200470&highlight=2.6.17](http://www.ubuntuforums.org/showthread.php?t=200470&highlight=2.6.17)

---

