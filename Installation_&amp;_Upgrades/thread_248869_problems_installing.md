---
title: "problems installing"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by el diablo on 2006-09-01
now, i saw this on the main page [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
about how to fix it...but i do not have ubuntu installed yet....therefore how would i go about logging in so i can update the xserver to install ubuntu?

im sorry if there is a thread on this already but i have been trying this for almost an hour and finally saw that....please help

thanks

---

### Post by taurus on 2006-09-01
If you haven't installed Ubuntu on your machine, then what are you talking about updating your xserver!!!  You MUST first install Ubuntu on your machine before you can update your upgrade it!  :roll:

---

### Post by el diablo on 2006-09-01
but thats the thing....i cant install it cause i get that error. mine is weird though and around the box is has all weird characters all over the place...so does this mean i cant use ubuntu onmy computer or somethingif im getting this error?

---

### Post by taurus on 2006-09-01
You mean you can't boot the desktop CD/LiveCD to install it on your machine!  Then, why don't you try using the alternate CD to install it and if you still can't get into X, then run that or 

```
sudo dpkg-reconfigure xserver-xorg
```
So, see if the alternate CD works on your machine or not and what is the spec of your machine anyway?

---

### Post by el diablo on 2006-09-01
alternate cd? and i assuming i would put that code into the DOS? btw i didnt DL the CD's i ordered them...i am trying to DL one now and it says 14 hours....

---

### Post by taurus on 2006-09-01
Do you have a dial up connection instead of a DSL or a broadband?  The desktop CD/LiveCD will boot into Live and you can install from it.  But if there is something wrong with your graphic card, then of course it will not start the Live and you can't install it.  That's why there is an alternate CD where the installer allows you to install it without booting into Live first.  It also uses text base.  So, don't worry about the code or the upgrade of xserver.  Just follow the instructions on the screen to install it and if you are experiencing problems with X after you install it, then you would configure your X again (from a command line--prompt) with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by el diablo on 2006-09-01
ok...i will try that and if not....=\ maybe i will try a diff distro.

---

