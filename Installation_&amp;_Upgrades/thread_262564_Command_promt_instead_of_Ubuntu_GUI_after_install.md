---
title: "Command promt instead of Ubuntu GUI after install"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by Ubobtu on 2006-09-21
Ive just installed Ubuntu on a spare laptop. The install went well, but after the final reboot for the first use, I get a command prompt (oem@ubuntu) but no sign-in screen or desktop.

Im sure the solution is total easy, but Ive been unable to find a similar thread of someone else having the same issue.

Thanks for any help.

---

### Post by dlehman on 2006-09-21
I did have a similar problem, is the laptop very old. I installed Ubuntu on and Old p1 200mhz with 64mb ram and it does not load usplash and when I first installed I don't think it installed any desktop software.  what I did was use apt-get to installed the edubuntu-desktop package, and I believe you could change it for ubuntu-desktop or kubuntu-desktop take your pick.  after that it still did not load usplash but it does load gdm with a login screen.  this may be the case with your laptop if it is a bit old its worth a shot.

---

### Post by Ubobtu on 2006-09-21
Yeah, it's a pretty old laptop. I had previously used Puppy Linux on it.

I'll give this a try. Since Im somewhat of a N00b, please tell we which command to type in. Thanks!

---

### Post by dlehman on 2006-09-21
Ok the command is aptitude first we will update it to make sure we get the latest verson of everying then we will installed the ubuntu desktop 

```
sudo aptitude update
```
```

sudo aptitude install ubuntu-desktop
``` 

this should do the trick and doblue check my spelling before putting in the commands

---

### Post by Ubobtu on 2006-09-22
Sucess! Thanks so much for the help!
It runs a little slow, as expected, but its working great!

Woo hoo!

---

### Post by carontis on 2006-09-22
Hey, boyz! On old and dated machines it's better use something like Xubuntu, with less heavy interfaces. You will have in a lter time to installa OpenOffice and all programs you need, but surely you'll have less troubles. Xubuntu is another distro from Ubuntu.

---

