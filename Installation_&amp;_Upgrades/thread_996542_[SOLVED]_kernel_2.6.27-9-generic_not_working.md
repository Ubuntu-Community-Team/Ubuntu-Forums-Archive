---
title: "[SOLVED] kernel 2.6.27-9-generic not working"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by ZaHACKieL on 2008-11-28
Hi everyone. I have Intrepid installed on my Dell Studio 1735. Today I upgraded the kernel to version 2.6.27-9-generic. After making all the upgrades and rebooting I selected on grub the 2.6.27-9-generic option...the ubuntu loading bar appeard, finished to load and then the screen went black with the underline blinking. I've tried many times and it's always the same story. I have to select the 2.6.27-7-generic option in order to make ubuntu work...what can be wrong? anyone has that problem? Thanx!

ZL

---

### Post by crazyness003 on 2008-11-28
it may be possible that the -9 incantation is broken. Iv seen this with a hardy kernel (cant remember). Just hump it out with the older kernel (not that much of difference anyway, as long as you have all your hardware up and running).

I have 2.6.27-9 running on my 32bit pc, and I did run into a problem when I first booted into it. But I just restarted and everythign worked peachy.
If you enable the proposed packages, in the sources, you'll run into 2.6.27-10 (i have that installed on my 64bit lappy. Works like a charm).

But these things happen. If you dont mind, report a bug on [https://launchpad.net/](https://launchpad.net/)
But other than that. thats all i can help you with.

---

### Post by ZaHACKieL on 2008-11-28
> **crazyness003 said:**
> it may be possible that the -9 incantation is broken. Iv seen this with a hardy kernel (cant remember). Just hump it out with the older kernel (not that much of difference anyway, as long as you have all your hardware up and running).

I have 2.6.27-9 running on my 32bit pc, and I did run into a problem when I first booted into it. But I just restarted and everythign worked peachy.
If you enable the proposed packages, in the sources, you'll run into 2.6.27-10 (i have that installed on my 64bit lappy. Works like a charm).

But these things happen. If you dont mind, report a bug on [https://launchpad.net/](https://launchpad.net/)
But other than that. thats all i can help you with.
Thanx a lot for your answer ^^ . I'll report the bug.

ZL

---

### Post by ZaHACKieL on 2008-11-29
Oh, I solved the problem...I reinstalled the ATI drivers and now it's working fine =)

---

### Post by crazyness003 on 2008-11-29
nice. Little things always make other things go wonkers.

Since the you solved the problem, make sure you mark this thread as [SOLVED] using the  	 	 		[Thread Tools]("http://ubuntuforums.org/showthread.php?t=996542&nojs=1#goto_threadtools") 		 [IMG]http://ubuntuforums.org/images/misc/menu_open.gif[/IMG]

---

### Post by mtbsoft on 2008-12-02
> **ZaHACKieL said:**
> Oh, I solved the problem...I reinstall the ATI drivers and now it's working fine =)

Can I just get some clarification on this ('cos I have the same issue).  Did you reinstall the proprietory ATI drivers and did you do it under 27-7 or in text mode under 27-9, please?

---

### Post by ZaHACKieL on 2008-12-02
> **mtbsoft said:**
> Can I just get some clarification on this ('cos I have the same issue).  Did you reinstall the proprietory ATI drivers and did you do it under 27-7 or in text mode under 27-9, please?
Hi! Well, my grub menu allows me to start Ubuntu with 27-7 kernel because I kept that version also. So, I chose that option, so Ubuntu would load normally and after that I reinstalled the ATI drivers the usual way. I think the driver file's name is ati-driver-installer-8-11-x86.x86_64.run   , at least the one I use.

In case you didn't keep the 27-7 kernel, you have to install the ATI driver using the 27-9 safe mode option.

Please let me know if you solved it or still have troubles with it.

---

### Post by mtbsoft on 2008-12-02
Thanks mate, I keep the previous kernel too so did the same as you said and all is sweet again.

Many thanks, much appreciated.

---

