---
title: "OS freezing"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by Fahl Guy on 2013-03-05
Just got a brand new machine:  Toshiba Satellite C855D S5320/AMD dual core e2-1800, upgraded with 16gig kingston ram.  Win 8 preinstalled and I hated it.  Changed UEFI to legacy and disabled secure boot.  Still would not let me partition and install ubuntu so I erased win 8 and started fresh with Ubuntu Secure Remix.  It took several days of tinkering but finally installed correctly (machine would freeze at same point of install or not show at boot, tried several live disks until success).  I ran boot repair.  

Current problem-laptop freezes as various stages (sometimes right after boot, sometimes 45 min. after running smoothly).  

Boot repair tag:  [http://paste.ubuntu.com/5586393/](http://paste.ubuntu.com/5586393/)

Any help would be greatly appreciated.

Thanks
Fahl Guy
[h=1][/h]

---

### Post by sanderj on 2013-03-05
I would run memtest86+ for at least one night, and see what it says.

---

### Post by buddy_t on 2013-03-07
> **Fahl Guy said:**
> Just got a brand new machine:  Toshiba Satellite C855D S5320/AMD dual core e2-1800, upgraded with 16gig kingston ram.  Win 8 preinstalled and I hated it.  Changed UEFI to legacy and disabled secure boot.  Still would not let me partition and install ubuntu so I erased win 8 and started fresh with Ubuntu Secure Remix.  It took several days of tinkering but finally installed correctly (machine would freeze at same point of install or not show at boot, tried several live disks until success).  I ran boot repair.  

Current problem-laptop freezes as various stages (sometimes right after boot, sometimes 45 min. after running smoothly).  

Boot repair tag:  [http://paste.ubuntu.com/5586393/](http://paste.ubuntu.com/5586393/)

Any help would be greatly appreciated.

Thanks
Fahl Guy


I have the same laptop with the same symptoms, running memtest now, however shows no errors so far. I am using 12.10, 12.04 would not install at all.  Wireless does work with no tweeks though, not much help when all it does is lock up though.

---

### Post by Fahl Guy on 2013-03-11
OK, so not a RAM problem.  Replaced my 2 new sticks with factory original and same problem.  Ran memtest86+ for several hours.  As soon as I started, test 1 reports 31 errors.  Second run of memtest shows 18 errors on test 1.  Not sure how long the computer was really running the test.  Second run froze after about 30min.  No other errors reported on either run (think I got to test 7 on first run).

Here's a little more info

Dumped Win 8 
Install Uberstudent from live CD.  Starts installation fine, freezes at exact same spot.  After installation almost finished loader says something about "USB modules to usb"
Installed Edubuntu: installation finishes, shows up after boot, OS starts from hard disk, computer freezes
Tried Linux Secure Remix 64-same as above.  I can get secure remix running for about 30 minutes.  Any more and she dies.  Computer really doesn't like my wireless.  It recognizes my network and lets me enter my key and connects.  Then every 30 seconds it asks for my security key and she dies.


I called Toshiba support because my "y" and "h" keys weren't working.  Mysteriously, keys started working after registering the product and on the phone with the guy.  

Anyway, am I up stink creek?  What can I replace (keeping in mind this is a $300  machine)?  Hard drive?  Motherboard?  My futile self-injurious hostility to Windows  OS?

As always, any help is greatly appreciated and those that provide it are greatly respected.

Aaron

---

### Post by sanderj on 2013-03-11
> **Fahl Guy said:**
> OK, so not a RAM problem.  Replaced my 2 new sticks with factory original and same problem.  Ran memtest86+ for several hours.  As soon as I started, test 1 reports 31 errors.  Second run of memtest shows 18 errors on test 1.  Not sure how long the computer was really running the test.  Second run froze after about 30min.  No other errors reported on either run (think I got to test 7 on first run).


I really do not understand what you're saying: memtest86 tests memory and reports errors, but you say "no a RAM problem"? :confused:

Please explain.

---

### Post by Fahl Guy on 2013-03-11
Sorry, I meant to indicate I ran the tests, they did come back with errors.  I then reinstalled the original factory ram instead of my upgraded ram.  The problem was not fixed.

---

### Post by sanderj on 2013-03-12
> **Fahl Guy said:**
> Sorry, I meant to indicate I ran the tests, they did come back with errors.  I then reinstalled the original factory ram instead of my upgraded ram.  The problem was not fixed.

So, it **is** a RAM problem?

If memtest86 reports problems and/or locks up, it is a pure hardware problem (not OS related). You have to solve that first.

---

