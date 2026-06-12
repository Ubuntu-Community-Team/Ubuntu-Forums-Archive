---
title: "Synaptic Segmentation Fault"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by john@ukgillies.com on 2011-02-14
Hi everyone,

I have a nasty little problem with synaptic.

Been using this faultlessly for two years now. No problems.
Today I am unable to run synaptic.

System - kubuntu
Linux LynxCast 2.6.32-29-generic #57-Ubuntu SMP Sun Jan 30 06:01:15 UTC 2011 x86_64 GNU/Linux

KDE 
Qt: 4.7.0
KDE Development Platform: 4.5.3 (KDE 4.5.3)
kde4-config: 1.0

Here is what happens when I try to run synaptic

~$ synaptic

This runs synaptic OK but obviously without the root privileges.

~$ sudo synaptic
sementation fault


Examination of the syslog shows this


Feb 15 00:10:58 LynxCast kernel: [  365.871471] synaptic[3018]: segfault at 0 ip 00007f3127562dd6 sp 00007fff79d0ad60 error 4 in libstdc++.so.6.0.13[7f31274bb000+f6000]



Apt-get works OK and I have purged and reinstalled synaptic using apt-get - no difference.

Does anyone have any thoughts on how to correct this?

Thanks,

John

---

