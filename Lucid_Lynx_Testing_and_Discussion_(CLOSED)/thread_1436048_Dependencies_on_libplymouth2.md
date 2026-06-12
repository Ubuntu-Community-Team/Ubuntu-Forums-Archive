---
title: "Dependencies on libplymouth2"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-03-22
Why is libplymouth2 a dependency of so many packages ? Plymouth has never worked on my system and frankly I don't care, I don't want a boot splash of any kind . Please note ! I am not saying that those who want plymouth should not have it or even that it should not be default .What I am saying is allow me to remove every trace of it If I do not want it. Making a completely optional package a dependency of a huge number of completely non related packages  can only be for the purpose of not allowing us to remove it . Exactly what does a boot splash have to do with apport or cairo-doc or gimp  and a list of other packages extending literaly from A to Y ( somehow they missed Z ) ?

---

### Post by keybuk on 2010-03-22
> **ronacc said:**
> Why is libplymouth2 a dependency of so many packages ? Plymouth has never worked on my system and frankly I don't care, I don't want a boot splash of any kind . Please note ! I am not saying that those who want plymouth should not have it or even that it should not be default .What I am saying is allow me to remove every trace of it If I do not want it. Making a completely optional package a dependency of a huge number of completely non related packages  can only be for the purpose of not allowing us to remove it . Exactly what does a boot splash have to do with apport or cairo-doc or gimp  and a list of other packages extending literaly from A to Y ( somehow they missed Z ) ?

Because one of the primary uses for Plymouth is not its graphics, but because it solves the issue of multiple difference asynchronous parts of the boot sequence prompting for questions or providing progress during boot.

The key ones are filesystem checking, filesystem errors, missing filesystems and encrypted filesystems.  You'll find that the dependencies on libplymouth2 should come from those.

If you find that the graphical version of boot doesn't appeal to you, leave plymouth installed but just remove "splash" from your kernel command line (edit /etc/default/grub)

Though, to be frank, since you're using Lucid you should be contributing to testing - and have filed bugs about your problems.

---

### Post by mc4man on 2010-03-22
> Why is libplymouth2 a dependency of so many packages 

It's not libplymouth2 per se, it's mountall which depends on libplymouth2 that leads to all those packages that would be removed

---

### Post by ronacc on 2010-03-22
@ keybuk  If I only remove the splash at the end of the boot line ( I also remove quiet ) plymouth still crashes and generates a crash report at each and every boot I therefore removed plymouth and plymouth-x11 (which can be removed without destroying your system ) .It is only libplymouth2 that tries to cause destruction .

---

### Post by keybuk on 2010-03-22
> **ronacc said:**
> @ keybuk  If I only remove the splash at the end of the boot line ( I also remove quiet ) plymouth still crashes and generates a crash report at each and every boot I therefore removed plymouth and plymouth-x11 (which can be removed without destroying your system ) .It is only libplymouth2 that tries to cause destruction .

Curious.  I can't find any crash reports from you in Launchpad?

Are you sure the report isn't just the "plymouth did not terminate at shutdown" report, which has been clearly marked as a bug in the crash reporting software - and not in Plymouth?

---

### Post by ronacc on 2010-03-22
I reported it the first time it happened back when plymouth was first introduced . It had already been reported so I added my affects me and comment . Note! my launchpad nick is sojourner . Now since it keeps telling me it has been reported ,I just cancel it  .

---

### Post by keybuk on 2010-03-22
> **ronacc said:**
> I reported it the first time it happened back when plymouth was first introduced . It had already been reported so I added my affects me and comment . Note! my launchpad nick is sojourner . Now since it keeps telling me it has been reported ,I just cancel it  .

Sounds like it's just the error in the reporting software that most are seeing; you should be quite safe to reinstall plymouth (otherwise later on, when you hit genuine errors during boot, you won't be able to do anything about them!)

---

### Post by ronacc on 2010-03-22
I really do not want plymouth , I habitually use the proprietary Nvidia driver and it has been stated in another thread that there is no intention to support that with plymouth therefore plymouth is a dunsel on my system .

---

