---
title: "Ubuntu 9.04 alpha 2 video card issue"
date: 2008-12-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TheMixtureMedia on 2008-12-24
Hi there I install Ubuntu 9.04 alpha 2 and my nivida card will not work it only works in low mode any idea??

---

### Post by Coder543 on 2008-12-24
I cannot be certain, but you probably don't need to be running 9.04... it is an **alpha 2**. Try 8.10, it is the current version of Ubuntu.

---

### Post by Twitch6000 on 2008-12-24
This is an alpha 2 bug as it is running the newest xorg version.

Which Nvidia,ATI,and I think even Intel graphics drivers are not availble for yet.

---

### Post by ronacc on 2008-12-24
see this thread , the solution is posted in several places , you really should search already existing threads before starting a new one .

---

### Post by TheMixtureMedia on 2008-12-24
I tried and could not find it must not have looked hard enough sorry

---

### Post by TheMixtureMedia on 2008-12-25
ok looked but could not find anything about my issue please help

---

### Post by autocrosser on 2008-12-25
dinxter & I posted the two-part fix here:  [http://ubuntuforums.org/showthread.php?t=1011847](http://ubuntuforums.org/showthread.php?t=1011847)

You need to modify your xorg.conf file as per dinxter's info & then add the restricted PPA that I reference later in the thread.

Remember: Xorg is the "control" for your drivers--the mod to Xorg caused almost all the drivers to go "bad"--- anytime you have a problem with lo-rez--look for xorg issues

---

### Post by Gina on 2008-12-25
I too now have problems with nvidia and Jaunty (AMD64) after a recent update.  Not got round to sorting it out yet - too busy with Christmas :lol:

---

