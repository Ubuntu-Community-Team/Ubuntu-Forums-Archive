---
title: "Removing upgrade"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by Don Cunningham on 2010-06-16
How do I remove an upgrade which has messed up my Ubuntu installation? Distribution is 10.04. Upgrade has caused the screen to expand to where the close screen and reduce screen controls are not reachable. Have to reboot to close a program.

 drc

---

### Post by leorolla on 2010-06-17
You can't remove an upgrade... downgrading is really messy.

But don't worry, you still can close buttons, and moreover you should set the screen size so that things work well.

Meanwhile, for emergencies: hold Alt and move the window with the mouse, move it down so you will see the "close button".

---

### Post by Don Cunningham on 2010-06-17
Thanks. Tried that. Didn't work. Guess I'll have to wipe the drive and reinstall.:confused:

drc

---

### Post by wojox on 2010-06-17
Alt+space bar works as well.

Hang in there and maybe they will reset on your next update.

---

### Post by leorolla on 2010-06-18
Don't panic. It cannot be that bad.

Try booting from a Live CD/USB with Ubuntu 10.04, and see if the live session works fine or not.

This will help understanding the problem with the screen.

---

### Post by Don Cunningham on 2010-06-18
Live CD works fine. The whole installation worked fine until the "upgrade". While the upgrade was installing there were dozens of items it said it could not find. One I suspect was the nVidia driver. Now Open Office screens appear as half screens and no way to enlarge them. 
  Am I the only one who is having problems with this upgrade?

drc

---

### Post by leorolla on 2010-06-18
So it is a recent Lucid install and plus update-upgrade?

In this case reinstalling doesn't sound that bad if nothing else works.

What exactly went wrong during upgrade? Can you do it again? Can you update-upgrade with the terminal and post the output here?

---

### Post by Don Cunningham on 2010-06-20
Yes, this was a recent install of 10.04.  During upgrade it failed to find most of the packages required by the upgrade. When I tried reinstalling the upgrade with synaptic it listed the number of items to be changed and then promptly rebooted after which there was no more activity.??

drc

---

### Post by wojox on 2010-06-20
```
/var/log/dpkg.log
```

Will tell you what packages were installed.:p

---

### Post by Don Cunningham on 2010-06-20
Thanks for trying to help guys. I've given up and wiped the drive. I will reinstall from my original disk and refuse any updates as long as it's working OK. From all the people who are having trouble with it it looks like this upgrade is a real loser. Oh, well MS had DOS 4.0 and Vista. :lolflag:

 drc

---

### Post by leorolla on 2010-06-21
I don't recommend having a 10.04 installed without any updates. There have been several hundreds of bug fixes since 10.04 was released. Upgrade at least once and then freeze from there.

---

