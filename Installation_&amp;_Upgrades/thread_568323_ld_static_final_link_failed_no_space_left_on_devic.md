---
title: "ld_static: final link failed no space left on device"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by 5318doug on 2007-10-05
I am a complete beginner with ubuntu, although worked with 68000 based unix systems many years ago so all this talk of mount, chmod etc rings some bells. 

Anyway have just installed 7.04 on an old PC - 633 MHz Celeron with 64 MB RAM using the text installer on the alternate CD. 20 GB disk and allowed ubuntu to set the partitions as it wanted so should be bags of space. But during boot I get "ld_static: final link failed no space left on device". The system is excruciatingly slow - 10 times slower than the Windows ME which was there before and the disk appears to be thrashing. Also although the installer said it had made DHCP work ok, Firefox can't access the internet and the network properties are not reporting an IP address

First thought - when it did the partition, although it warned me that all data would be deleted there seemed to be no long format process. Could the disk still be full of Windows?

Just run df and it shows as expected /dev/sdal having 16G out of 19G available. There are then various other things such as varrun, varlock which all seem to have plenty of space. lrm is showing as 86% full is this a concern?

---

### Post by Pumalite on 2007-10-05
With 64 MB RAM, if you want a fast system, you should stick to smaller distros. Xubuntu Alternate will install but still be slow. Puppy is your best bet. You can also try: Zenwalk, DSL.

---

### Post by 5318doug on 2007-10-07
ok, I've ordered some more RAM, but realised UK post strike may mean I don't get it for a bit. I'll let you know if his helps. I also looked up Puppy - I'll try that if the RAM doesn't help. What do I lose with Puppy compared with Ubuntu?

---

### Post by Pumalite on 2007-10-07
Not much. Puppy is known for recognizing a lot of hardware, has lots of programs and is a FLASH.

---

### Post by 5318doug on 2007-10-16
512 MB now installed and Ubunto working fine - thanks. 

I did also try puppy, but this was also hopelessly slow in 64 MB RAM - certainly in its default config. I was very impressed how fast it was on my other PC, but Ubunt is fast enough and comes much more pre-set up.

---

### Post by florentx on 2007-12-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/176562](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/176562) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **5318doug said:**
> Anyway have just installed 7.04 on an old PC - 633 MHz Celeron with 64 MB RAM using the text installer on the alternate CD. ... 

I installed Xubuntu 7.10 on an old PC, 64 MB RAM and 4 GB hard drive.

> But during boot I get "ld_static: final link failed no space left on device".

I had similar issue when installing restricted modules.

> First thought - when it did the partition, although it warned me that all data would be deleted there seemed to be no long format process. Could the disk still be full of Windows?

Just run df and it shows as expected /dev/sdal having 16G out of 19G available. There are then various other things such as varrun, varlock which all seem to have plenty of space. lrm is showing as 86% full is this a concern?

Definitely, the problem is on the lrm mount. I posted a bug report in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/176562](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/176562)

The workaround is to add few lines in /etc/default/linux-restricted-modules-common.

-- 
Florent

---

