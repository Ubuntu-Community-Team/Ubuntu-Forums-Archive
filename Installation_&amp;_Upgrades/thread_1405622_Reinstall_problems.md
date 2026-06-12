---
title: "Reinstall problems"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by ozguy on 2010-02-12
I have a dual boot windows XP/ubuntu 9.10 set up on one hard drive. Everything was working fine. The 9.10 install had been updated from 9.04. I recently had problems with the XP partition (XP basically collapsed) so I re-installed XP on the same partition it was on before. 

Everything was fine. I then attempted to reinstall Ubuntu ( I decided I wanted a new 'clean' installation of Ubuntu as well). When I got to the partition function it refused to recognize that there is a Windows partition, or a previous ubuntu partition, but states 'No operating system installed' or similar, and offers the entire hard drive for installation.

When I look at the partitions using Windows partition software the Windows and the ubuntu partitions are clearly in evidence.

I have also tried to reinstall GRUB but it doesn't appear to exist.

Any suggestions?

Sorry I'm only an occasional Linux user so be gentle with me.

---

### Post by raymondh on 2010-02-12
> **ozguy said:**
> I have a dual boot windows XP/ubuntu 9.10 set up on one hard drive. Everything was working fine. The 9.10 install had been updated from 9.04. I recently had problems with the XP partition (XP basically collapsed) so I re-installed XP on the same partition it was on before. 

Everything was fine. I then attempted to reinstall Ubuntu ( I decided I wanted a new 'clean' installation of Ubuntu as well). When I got to the partition function it refused to recognize that there is a Windows partition, or a previous ubuntu partition, but states 'No operating system installed' or similar, and offers the entire hard drive for installation.

When I look at the partitions using Windows partition software the Windows and the ubuntu partitions are clearly in evidence.

I have also tried to reinstall GRUB but it doesn't appear to exist.

Any suggestions?

Sorry I'm only an occasional Linux user so be gentle with me.

Hello ...

Let's try:

-Boot into the 9.10 liveCD and go live session (try ubuntu without any changes)
-In live session mode, access a terminal (applications > accessories) and type

```
sudo remove dmraid
```

-Exit the terminal and continue with the install.  When you get to step 4, see if it recognizes the partitions.  If so, proceed with the install.  If not, exit and we'll try to research more on this problem.

Regards,

Raymond

---

### Post by ozguy on 2010-02-13
Thanks for your help. I tried it but I got the message 'no remove command' or similar.

 Anyway I solved the problem by removing the linux partition through windows.There must have been a problem with the original ubuntu install. Ubuntu then used the 'unused' partition to install to.

Thanks for your interest anyway.:D

---

### Post by raymondh on 2010-02-13
glad you got it working.  In my rush, I made a mistake ... it ought to have been

sudo apt-get remove dmraid

happy ubuntu-ing.

Raymond

---

