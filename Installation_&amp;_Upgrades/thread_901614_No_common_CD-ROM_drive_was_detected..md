---
title: "No common CD-ROM drive was detected."
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Fr0ns on 2008-08-26
This is probably post #50 about this subject but since there is still no solution I have the feeling that this problem hasn't been taken serious.

Like so many other people, while installing Ubuntu Server LTS 8.04 I get the following error: "No common CD-ROM drive was detected".

What is there to do about this, i've tried all the "F6 commands" from other topics like "generic_ide" and such. No solution.

This thread will probably die unanswered. An I'll be force to look for another distro since this has been going on for quite some time.

Thanks in advance.

I'm using:
An old P3 based Compaq Deskpro.
Ubuntu 8.04 Server LTS Checksum of CD is OK.
2 different standard old cd-rom drives.

---

### Post by wpshooter on 2008-08-26
First, have you checked the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

Next how do you have your drives jumpered and connected to your motherboard ?  Assuming that these are IDE drives, I would recommend that you jumer both hard drive and CD-Rom drive as MASTER and place the hard drive on primary IDE connector by itself and then place the CD-Rom drive on the secondiary IDE connector by itself.

Next make sure that the CD-Rom drives have the latest & greatest FIRMWARE installed.  You my have to install a Version of M/S windows O/S to check the version of the firmware and then to update it if needed.

Make sure that you are trying to do the installation from the ALTERNATE version of Ubuntu instead of the desktop (live) version.

Good luck.

---

### Post by Fr0ns on 2008-08-26
The cd never is the problem, this occurs so often, it's not some random bug.

Both drives are master on their seperate cables and channels. Also there is no firmware for those old bats.

You can't wave this off as something to do with my hardware, this is happening all over (no offense).

---

### Post by wpshooter on 2008-08-27
> **Fr0ns said:**
> The cd never is the problem, this occurs so often, it's not some random bug.

Both drives are master on their seperate cables and channels. Also there is no firmware for those old bats.

You can't wave this off as something to do with my hardware, this is happening all over (no offense).

Do you find that you have these same problem(s) if you use Gutsy instead of Hardy ?

I have not found Hardy to my liking for many reasons, therefore I do not use it and am still using Gutsy very happily instead.

---

### Post by Fr0ns on 2008-08-27
> **wpshooter said:**
> Do you find that you have these same problem(s) if you use Gutsy instead of Hardy ?

I have not found Hardy to my liking for many reasons, therefore I do not use it and am still using Gutsy very happily instead.

Might go back indeed, but it's also a matter of principle. I would have never thought a big and mature distro like Ubuntu would a) have such problems and b) have so much issues trying to fix it.

---

### Post by wpshooter on 2008-08-27
> **Fr0ns said:**
> Might go back indeed, but it's also a matter of principle. I would have never thought a big and mature distro like Ubuntu would a) have such problems and b) have so much issues trying to fix it.

I could give you my thoughts on why this is, but since I don't have an inside track to the inter-workings of Ubuntu/Canoncial staffing, it would be just conjecture !!!

---

### Post by Fr0ns on 2008-08-29
Funny, tried to install the latest stable release of Debian, same problem.

---

