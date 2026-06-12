---
title: "Ubuntu 8.10 install fails on all fronts"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by fanatic26 on 2008-11-05
I have never had a linux distro give me so many problems, especially when its supposed to be the most user friendly. I am using relatively generic and standard hardware and I am confused as to why I have so many issues with a basic *next* *next* *next* installer.

List of issues:

1.) Ubuntu Installer resizes an empty disk and only allocates 30% to Ubuntu, leaving the rest blank (fixed by forcing it to use the whole disk manually)

2.) Grub setup incorrectly by installer and will not boot. Set to use UUID instead of any standard convention (fixed by writing my own fstab and menu.lst)

3.)Ubuntu will not boot - Not Fixed.

"failed to execute sbin/v86d"

I have seen seperate bug reports all for this issue. Its been attributed to video drivers, usb hard drives, among other things with no clear method of resolution. Does anyone have any concrete facts on why this is happening? I have gone as far as reinstalling twice to the same issue.

---

### Post by Pumalite on 2008-11-05
Post your specs and:
sudo fdisk -lu

---

### Post by gnothi on 2008-11-05
I agree.

I've been using Ubuntu since Dapper and I've never been completely defeated by the installer before.

First the LiveCD tries to convince me that either my DVD drive or hard-drive is having i/o errors. Then the installer doesn't see my keyboard. And there were crash reports about some communications (?) thing.

The ISO file MD5SUM is okay, and the LiveCD-verify passes. Tossing Ibex aside, the Mandriva One 2009 LiveCD installs without a problem.

Funny, that the Ibex _Release Candidate_ LiveCD had installed okay two weeks ago. I'd given that disc away.

Seems I'll be sticking with 8.04 LTS until at least 9.04.

:/

---

### Post by Pumalite on 2008-11-05
You guys seem to be having all the problems. I've done 6 installations of Intrepied Ibex in 32 and 64 bit without a problem. I suspect incompatible hardware or you are using a Live CD where you should be using an Alternate CD. Maybe you need a lighter distro like Xubuntu. Without specifics, of course I'm just speculating.

---

### Post by gnothi on 2008-11-05
Read my post carefully.

No hardware problems: Ibex RC had installed OK two weeks ago, and Mandriva installs OK **today**.

The ISO file and LiveCD-burn pass all integrity tests.

I'm currently running 8.04 LTS on another partition of **the same PC**.

:(

---

### Post by Pumalite on 2008-11-05
Well, I used the Final Release.

---

