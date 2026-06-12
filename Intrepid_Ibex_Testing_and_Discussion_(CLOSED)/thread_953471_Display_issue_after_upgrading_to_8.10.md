---
title: "Display issue after upgrading to 8.10"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Brickedin21 on 2008-10-20
hey, i have been searching everywhere to a solution to this problem: I installed 8.10 with no issues, there was no problem what so ever, so then i went and did the updates, all 427 of them or something, and then after the reboot, i no longer have a display, nothing, i can hear the long on sounds clicking on and the welcome sound after i type in my name and password but that is it. I have been doing a lot of searching to find the answer to the problem but nothing has worked so far... I have tried doing sudo /etc/init.d/gdm stop  then reboot in recovery then fix x... and that didnt work, i have tried updating again... Not sure what else to do... anyone think they can take a crack at this?:confused:

video card is an ATI HD3470 

Thanks

---

### Post by Adahn on 2008-10-20
I'm going to bump you as I have the same problem.
fixx does not work.
dpkg-reconfigure xserver doesn't even include display options...only keyboard.
sudo apt-get upgrade gives 'can't resolve servers' type errors

---

### Post by Brickedin21 on 2008-10-20
bump

---

### Post by High Roller on 2008-10-20
This all sounds similar to the bug I just filed.  My display always worked in previous versions of Ubuntu.  But now there's some type of issue related to the frame buffer (apparently).

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/286227](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/286227)

Are you folks able to produce log files and attach to this bug if they're related?

---

