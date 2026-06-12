---
title: "Stuck at 'Ready When You Are'"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by VolatileVoid on 2011-02-01
Hi -
 
I've been trying to resurrect an **old** laptop (think Pentium 800 old :)) by installing Ubuntu on it. I thought I was in the clear after downloading and booting, but then I get stuck at the 'Ready When You Are' screen. This is Ubuntu 10.10
 
I have seen previous such issues caused by caps in the username, but I've not been prompted to even enter a username yet so I really don't know what could be causing this, and I don't know where to begin searching...
 
Thanks!

---

### Post by tommcd on 2011-02-01
First things first:
Be sure to check the **md5sum** of the iso image you downloaded to be sure it is not corrupted: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If that passes, then when you boot the Ubuntu live CD be sure to run the option 
*Check Cd for Defects*: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
This will insure that the CD you burned is valid and has no corrupted files.

For such an old computer I would use Lubuntu, [http://lubuntu.net/](http://lubuntu.net/) since it is much lighter on resources than the full on Ubuntu with that resource hungry scourge that is pulseaudio.
How much memory is in your computer?

Write back if you need more help.
And welcome to the Ubuntu forums!

---

