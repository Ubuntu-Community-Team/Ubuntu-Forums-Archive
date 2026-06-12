---
title: "LiveCD help"
date: 2006-04-24
forum: Installation &amp; Upgrades
---

### Post by inclininwirefree on 2006-04-24
hi,

People tell me it should be the easiest thing to run a LiveCD but I can't get beyond the following screen:

DETECTING HARDWARE TO FIND CD-ROM DRIVES

-------------------------------92% completed

LOADING MODULE 'ISOFS' FOR 'LINUX ISO 9660 FILESYSTEM'...


This occurs right after language, keyboard selection, etc. Its not that the laptop freezes coz ctrl-alt-del does work.

Wud appreciate some thoughs here.


Best,
inclininwirefree

---

### Post by matelot on 2006-04-24
Have a look at the thread - *Is there as case here...*

Like so many others, I have the same problem. As yet it's unresolved. I've tried different 'Distros', but so far only Mandriva works on my Dell, but not on a P2 350 (apparently it's too old!)

---

### Post by Sef on 2006-04-24
inclininwirefree: I have a few questions for you.

1) Have you tried the Live CD in another system?  (This is to make sure it is a good copy and not a bad one.)

2a) After you downloaded the iso, did you md5sum it? (This is to make sure it downloaded right.)   

2b) If you used bittorrent to download the iso, then it automatically did an md5sum.

3) Did you burn at 4x or slower? (Faster burn speeds can corrupt the burn.)

4) The disk could be bad.  (Even if you did the above or got it from Ubuntu.)

---

### Post by inclininwirefree on 2006-04-24
matelot - Do you have an idea what the problem is related to?

Sef - Your questions answered below:
1) No but I have tried two different CDs
2) Yes, the md5sum was done and found to be correct.
3) I burned @ 8x

---

### Post by matelot on 2006-04-25
[QUOTE=inclininwirefree]matelot - Do you have an idea what the problem is related to? ...[/QUOTE]

In a kernel (nutshell :mrgreen: ) No. I d/l ubuntu-5.10-live-i386.iso and verified the checksum. Burned the ISO and burned it back again and verified the checksum. All OK. It gets to 20% on the progress bar saying it can't load installer components. The last thing I could read was *LIBC6-UDEB*.

I want to breathe new life into an old P2 350, but some are saying that that's too old... Beats me. Anyway, I've tried to run the LiveCD initially on a year-old Dell 3000 desktop, 512Mb RAM, 160Gb HDD, XP Home single partition etc. No joy.

BUT, I can run Mandriva Live, DSL Live and gparted-livecd (for NTFS partitioning). So, the CD-DVD RW is OK, and the PC is OK.

Is it the case that some distros just aren't happy on some PCs? :confused:

Be pleased for some pointers.

---

