---
title: "No more entries in System menu"
date: 2009-12-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-12-03
With last upgrade (I think gdm was one of items) I've lost all entries in system menu, except Ubuntu SW Center, File Management, MM System Selector ... and got two Byobu entries. Is there an easy way to get them back? I've tried Edit Menus but there are no entries there either, to re-enable.

---

### Post by godhika on 2009-12-03
Just realized the same thing - strange. But the changelogs for GDM just said that the devs are disabling xsplash for the moment.

---

### Post by ayates on 2009-12-03
It's gnome-menus_2.28.0.1-0ubuntu2. I reverted to previous version and it fixed it. I'll post a bug. Back in a minute.

[https://bugs.launchpad.net/ubuntu/+source/gnome-menus/+bug/491937](https://bugs.launchpad.net/ubuntu/+source/gnome-menus/+bug/491937) if someone could confirm.

---

### Post by MacUntu on 2009-12-03
Pitt made it (ka)putt. :P

Confirmed.

---

### Post by SevenMachines on 2009-12-03
is it possibly related to this...
$ sudo update-gnome-menus-cache /usr/share/applications 
Segmentation fault

or does no-one else get this

---

### Post by zika on 2009-12-03
Gnome-control-center is also affected. So, there is no easy bypass...

---

### Post by cariboo on 2009-12-03
I installed the daily build this morning in vbox, everything thing seemed to go well. I shut it down, to do some other things in vbox, and when I restarted System-->Preferences is missing and the only thing in System-->Administration is the Software Center.

Has any one else seen this?

---

### Post by Merk42 on 2009-12-03
[Looks like they do](http://ubuntuforums.org/showthread.php?t=1344744)

---

### Post by cariboo on 2009-12-03
I've got to start searching for similar threads :)

---

### Post by sports fan Matt on 2009-12-03
+1 please add me to that list! :)

---

### Post by ranch hand on 2009-12-03
Just for giggles I did a complete update on Lounge Lizard and now I can say that I have all these problems too.

My other two installs are fine as I just did the apt-get upgrade on them.

Well, that isn't completely true.  Still have the "udevadm settle" crap on Stoned Lizard but I can boot "recovery" and do a CLI loggin with "startx" and all is good.

---

### Post by VMC on 2009-12-03
What happened to me was I lost my top panel. Created another one and put it at the top, then noticed that at the top there was space for another one. Thinking the original was there but hidden somehow.

Then I just rebooted and everything is back to normal. Even the second panel is gone. Try rebooting.

---

### Post by VMC on 2009-12-03
With recent updates I just now noticed the "System > Administration", has only "Add/Remove Applications" & "Computer janitor".

Anyone else have this problem. I tried adding a new panel with System, but it too had the limited programs.

---

### Post by sports fan Matt on 2009-12-03
[http://ubuntuforums.org/showthread.php?t=1344744](http://ubuntuforums.org/showthread.php?t=1344744)

Ran into it myself:)

---

### Post by 23meg on 2009-12-03
Three threads on the same issue merged.

---

### Post by zika on 2009-12-04
Problem is solved. Now, I have just a growing list of packages that are kept back:> The following packages have been kept back:
  gnome-games python-glade2 python-gtk2 totem totem-mozilla totem-plugins 
  x11proto-xinerama-dev{a} xserver-xorg-core 
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
What is the proper meaning of markings {a}, {u} ...?

---

### Post by jppr on 2009-12-04
there is now new version gnome-menus and works fine  = )

---

### Post by VMC on 2009-12-04
Not entirely fixed. Now I have two of System>Administration, **Computer janitor** & **Add/Remove Applications**

---

### Post by zika on 2009-12-04
> **VMC said:**
> Not entirely fixed. Now I have two of System>Administration, **Computer janitor** & **Add/Remove Applications**I have two Byobu ... But one is my creation that I can not edit now ...

---

### Post by jppr on 2009-12-04
> **zika said:**
> I have two Byobu ... But one is my creation that I can not edit now ...

i don´t have any problem, system is mormal and there is what there must to be.

---

### Post by YosefKaro on 2009-12-05
I'm noticing the same problem. Um, why has this thread been marked as solved? I thought that I was going to find the solution to this problem here. Maybe I over-looked it?

-Yos

PS All that I have in Preferences is: IBus Preferences
   All that I have in Administration is: GParted, Hardware Drivers, Login Screen, Ubuntu Software Center

---

### Post by zika on 2009-12-05
> **YosefKaro said:**
> I'm noticing the same problem. Um, why has this thread been marked as solved? I thought that I was going to find the solution to this problem here. Maybe I over-looked it?

-Yos

PS All that I have in Preferences is: IBus Preferences
   All that I have in Administration is: GParted, Hardware Drivers, Login Screen, Ubuntu Software CenterSolution came with upgrade ...

---

### Post by plun on 2009-12-05
a ```
sudo apt-get install ubuntu-desktop
```

solved it for me

---

### Post by PaulInBHC on 2009-12-05
I just ran safe-update and then install ubuntu-desktop which stated I already have the newest version.
Still no system menu.

---

