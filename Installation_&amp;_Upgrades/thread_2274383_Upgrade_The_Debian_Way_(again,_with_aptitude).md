---
title: "Upgrade: The Debian Way (again, with aptitude)"
date: 2015-04-20
forum: Installation &amp; Upgrades
---

### Post by quequotion on 2015-04-20
So it's 2015, and [I still trust this kind of method more than 3rd party installers]("http://ubuntuforums.org/showthread.php?t=1485604").

I had a very good experience this time with aptitude.
Aptitude's decision making is better than it used to be.
The computer this was tested on is an old 32bit intel without a graphics card, so the package dependency complications are few.

Step 1. Install aptitude:```
sudo apt-get install aptitude
```
Step 2. Replace **a** for **b** in all source files:
::TODO:: sed magic to replace **trusty** for **vivid** in **/etc/apt/sources{,.list.d/*}**; not hard to do in gedit.

Step 3. Update:```
sudo apt-get update
```
Step 4. Distribution Upgrade with aptitude:```
sudo aptitude dist-upgrade
``` Aptitude might need some time to think about it. If it can't find a solution, it will fall back on apt-get's approach to fulfilling dependencies. Generally this solves a lot of problems, like not having to reinstall the boot-loader (best way to make a brick), and keeping your custom package selections (no need to start over from scratch--this *isn't* Winblow$ after all).

---

