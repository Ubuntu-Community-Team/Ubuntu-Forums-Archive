---
title: "&quot;Upgrade Ubuntu 11.04 to 11.10&quot; option disabled in desktop cd"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by KMKAR on 2011-10-22
Hi all,
I've a laptop with Ubuntu 11.04 installed and working perfectly and I want to upgrade to 11.10

But I'm currently without any chance of doing an online upgrade (I'm currently connected through 128k dsl that works very badly), so I've previously downloaded the desktop cd of Ubuntu 11.10

Using desktop cd, the option "Upgrade Ubuntu 11.04 to 11.10" is disabled. Any ideas about that?

Thanks!

---

### Post by raja.genupula on 2011-10-22
Hi , You can upgrade your system to Ubuntu 11.10 from the Live CD by booting it , go to the install and then at the step of before selecting the partition its gonna ask you for upgrade of your Ubuntu 11.04.From there you can move .

All The best.

---

### Post by KMKAR on 2011-10-22
> **raja.genupula said:**
> Hi , You can upgrade your system to Ubuntu 11.10 from the Live CD by booting it , go to the install and then at the step of before selecting the partition its gonna ask you for upgrade of your Ubuntu 11.04.From there you can move .

All The best.Thanks for your response, first at all!

I can not understand very well what actions I need to fullfil to achieve what you are saying.

Maybe a few screenshots to clarify my issue:
- Install01.png -> You can see the option "Upgrade Ubuntu 11.04 to 11.10" gray(ed), so, its disabled by default.

- Install02.png -> Actual Partition table from my /dev/sda(N)
I have:
./sda1 - ext4 of 20gb +/- (Ubuntu 11.04)
./sda6 - ext4 of 130gb +/- (Ubuntu data/programs/stuff/etc)
./sda5 - swap of 10gb +/-
./sda3 - ntfs of 320 +/- (my personal and work related data)

./sdb is an external drive.

So, having this "new" info about the issue, how can I proceed to upgrade my system, without having the option available?

Thanks and best regards!

---

### Post by raja.genupula on 2011-10-22
when you have downloaded that CD , i mean after releasing of Ubuntu 11.10 or before ? 

OK when you insert that after login in to your system automatically it gonna ask for upgrade , this is one possibility .

---

### Post by KMKAR on 2011-10-22
> **raja.genupula said:**
> when you have downloaded that CD , i mean after releasing of Ubuntu 11.10 or before ? 

OK when you insert that after login in to your system automatically it gonna ask for upgrade , this is one possibility .I've downloaded the desktop cd yesterday and my system its not giving any message to update when I do the login process.

I don't want to install 11.10 from scratch and loosing my /home and other related data in the systm! :(

---

### Post by KMKAR on 2011-10-23
Alright, yesterday at night I decided to move on, install 11.10 and feel OK to re-install all my software that was loaded over 11.04.

What I've done is the following:

I'm one of the (few?) people over there who has the "/home" mounted in a separated partition, so my user's data will not be wiped unless I format that particular partition.
So, Using the desktop-cd I choose the Install option and then the advance option to wipe and recreate all the "new" system in the partition mounted on "/".
After 20 min I was booting a clean installation of 11.10. After a few issues regarding Unity and the disappear of both (top and left) tool-bars I got the system running smoothly.

I've re-installed all my software again, but at least I didn't loose any Users data contained in /home

Thanks for the help.

I'll mark the thread as Solved, although I still don't understand why the desktop-cd doesn't gives (as enabled) the option to "upgrade"..

Regards.

---

