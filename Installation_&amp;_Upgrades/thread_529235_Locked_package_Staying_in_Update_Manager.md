---
title: "Locked package Staying in Update Manager ???"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by notwen on 2007-08-18
I have recently patched my version of tilda to enable true transparency and when I install the update from update manager it loses it's true transparency.  I have locked my current tilda package in Synaptic, but now I constantly have 1 update available showing up in my notification area.  Is there any way to make update manager ignore locked packages? I've also tried the "sudo aptitude hold tilda" command in terminal, but I always get the update available icon.  Any recommendations/ideas?  =]

---

### Post by notwen on 2007-08-20
*bump*

---

### Post by Warren Watts on 2007-08-20
I am having the very same problem with a different package and I can't get an answer.

[Persistent Update Manager]("http://ubuntuforums.org/showthread.php?t=529491")

---

### Post by notwen on 2007-08-21
additional *bump*  

Does everyone who locks a package have to deal w/ the update icon in the notification area if said package has updates?!?  I realize they are two different processes and that me locking a pacakge in Synaptic shouldn't affect the way Update Manager checks for updates, but is there a way to dismiss any updates for select packages in Update Manager?

---

### Post by Warren Watts on 2007-08-21
Between my [thread on the subject]("http://ubuntuforums.org/showthread.php?t=529491")  and this one, close to 100 people have read the two threads and not a single reply.

I guess no one loves us anymore...  :-(

---

### Post by notwen on 2007-08-21
I'm guessing since I'm still getting a notification from Update Manager that it(Update Manager) and Synaptic do not work together.  Can anyone atleast confirm this?   I'm trying to narrow down our situation if I decide to file a bug on launchpad.  Perhaps in the future they(Synaptic, Add/Remove Programs, & Update Manager) can share the same package listing to prevent this problem from occurring.    What's the point of locking a package in Synaptic to only have Update Manager update and over-write your locked package?  Maybe notify you that another package manager has locked this package and require a confirmation before upgrading/over-writing said package.  [-o< Please help, I beg of you. [-o<

I'm growing tired of the update icon in my notification area, been there for nearly a month now. =x

---

### Post by notwen on 2007-08-22
*bump* weeeeeeeeeeeeeeeeee

---

### Post by r_l on 2007-08-25
bump

---

### Post by r_l on 2007-08-25
> **notwen said:**
> I'm guessing since I'm still getting a notification from Update Manager that it(Update Manager) and Synaptic do not work together.  Can anyone atleast confirm this?   I'm trying to narrow down our situation if I decide to file a bug on launchpad.  Perhaps in the future they(Synaptic, Add/Remove Programs, & Update Manager) can share the same package listing to prevent this problem from occurring.    What's the point of locking a package in Synaptic to only have Update Manager update and over-write your locked package?  Maybe notify you that another package manager has locked this package and require a confirmation before upgrading/over-writing said package.  [-o< Please help, I beg of you. [-o<

I'm growing tired of the update icon in my notification area, been there for nearly a month now. =x

Has anyone actually filed this one to the launchpad?  If so, is there a link?

---

### Post by r_l on 2007-08-25
> **Warren Watts said:**
> Between my [thread on the subject]("http://ubuntuforums.org/showthread.php?t=529491")  and this one, close to 100 people have read the two threads and not a single reply.

I guess no one loves us anymore...  :-(

Hey, just dug out this one from the "hidden" third party forum, have not gotten time to install it yet - see if it works:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=532985]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=532985")

So it seems that the update manager does not have an option for you.  Rather, the patcher/alternative installer needs to program it into their code.  However, I think it only makes sense to have a feature to disable unwanted update package from the user.  I hope they will have that in the future.

---

### Post by deep-z on 2007-08-25
Maybe this will help you somehow:
[http://ubuntuforums.org/showthread.php?t=532266](http://ubuntuforums.org/showthread.php?t=532266)

---

### Post by notwen on 2007-08-28
> Hey, just dug out this one from the "hidden" third party forum, have not gotten time to install it yet - see if it works:
[http://ubuntu-utah.ubuntuforums.org/...d.php?t=532985](http://ubuntu-utah.ubuntuforums.org/...d.php?t=532985)

Any update on this by chance? I breifly skimmed over Uuntuzilla info, are you able to add additional packages to it other than Firefox/ThunderBird/etc to maintain?  And more importantly if you are, can you lock them down and force the current version of said package to not download upgrades. =]

---

