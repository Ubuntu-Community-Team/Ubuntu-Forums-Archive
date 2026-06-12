---
title: "Your session only lasted less than 10 seconds"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by pigbig842001 on 2007-07-29
Hello Ubuntu Users,

I downloaded the Ubuntu 7.04 i386 iso image file from ubuntu's site. Burned the iso to a CD at 32X, nero 7 didn't show any problems. Now popped the CD into the drive and restarted the PC.

Ubuntu booted up. Then asked to select from a group of 5-6 options. Selected the first option. It started loading then after a while showed "Your session only lasted less than 10 seconds".

I am pretty frustrated as I devoted 7 hrs to download it and then what I see is that I can't even get a glimpse of ubuntu desktop. I am pretty new to linux. Plz help me out so that I can atleast view ubuntu.

---

### Post by pigbig842001 on 2007-07-29
Hello Ubuntu Users,

I downloaded the Ubuntu 7.04 i386 iso image file from ubuntu's site. Burned the iso to a CD at 32X, nero 7 didn't show any problems. Now popped the CD into the drive and restarted the PC.

Ubuntu booted up. Then asked to select from a group of 5-6 options. Selected the first option. It started loading then after a while showed "Your session only lasted less than 10 seconds".

I am pretty frustrated as I devoted 7 hrs to download it and then what I see is that I can't even get a glimpse of ubuntu desktop. I am pretty new to linux. Plz help me out so that I can atleast view ubuntu.

---

### Post by dabl on 2007-07-29
> **pigbig842001 said:**
> 

 Burned the iso to a CD at 32X, nero 7 didn't show any problems.



OK, 2 suggestions:

1. Use the md5 checksum to verify that your downloaded ISO image is 100% correct.  The md5 checksum is on the site where you got the ISO file.

2. Turn down the Nero burning speed to 4X.

Let us know if this helps!  :)

---

### Post by pigbig842001 on 2007-07-29
> **dabl said:**
> OK, 2 suggestions:

1. Use the md5 checksum to verify that your downloaded ISO image is 100% correct.  The md5 checksum is on the site where you got the ISO file.

2. Turn down the Nero burning speed to 4X.

Let us know if this helps!  :)
ok, i am going to burn another cd at 4x. how do I md5 check it?

btw, this is what i am getting again and again.

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

view details (~/.xsession-errors file)

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u/var/run/utmp -x "/var/lib/gdm/:0.xservers"
/etc/gdm/xsession: Beginning session setup...
Failed to execute message bus daemon /usr/bin/dbu-daemon: Exec format error. Will try again without full path.
/usr/bin/dbus-daemon: 1: Syntax error: "(" unexpected
EOF in dbus-launch reading address from bus daemon.

---

### Post by pigbig842001 on 2007-07-29
> **dabl said:**
> OK, 2 suggestions:

1. Use the md5 checksum to verify that your downloaded ISO image is 100% correct.  The md5 checksum is on the site where you got the ISO file.

2. Turn down the Nero burning speed to 4X.

Let us know if this helps!  :)
It's my fault. I should have checked md5sum before burning the CD. Finally, checked md5sum and found out that "./casper/filesystem.squashfs" didn't clear the test. That very file is 630 MB in size. Checked the ISO file too and the same error is there. Seems like the downloaded copy is damaged.

From now on I will be checking it before burning (don't want to lose another CD).

---

### Post by dabl on 2007-07-29
> **pigbig842001 said:**
> 

 I should have checked md5sum before burning the CD.

 

Now that's what I call a learning experience!

:)

Good luck with the next burn!  Don't forget --- 4X!

:popcorn:

---

