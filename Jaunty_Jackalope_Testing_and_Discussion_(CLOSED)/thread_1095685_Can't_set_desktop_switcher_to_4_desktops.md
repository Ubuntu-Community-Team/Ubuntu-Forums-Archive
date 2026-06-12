---
title: "Can't set desktop switcher to 4 desktops"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eleifsp on 2009-03-14
Ok, so here's the full situation:

I have Compiz Fusion enabled with, of course, the Desktop Cube effect.  Now, a cube wouldn't be much of a cube with more or less than 4 sides, right?  Well, that's what I feel ;)

Anyway, when I try to set the number of desktops to 4 horizontal and any number of vertical, it resets the horizontal to 2.

I'm not sure if this is a bug with Compiz or the Desktop Switcher, because the problem occurs when I try to set either.

---

### Post by shane8002 on 2009-03-14
Just right click the workspace icons at the bottom and and change the number to 4. You dont half to change it in compiz.

---

### Post by michael37 on 2009-03-14
Ideal compiz settings so that cube works:

Horizontal Size: 4
Vertical Size: 1
Number of desktops: 1

For everyone else, the settings are in System/Preferences/CompizConfig Settings Manager/General Options/Desktop Size

---

### Post by Shrav on 2009-03-14
> **eleifsp said:**
> Ok, so here's the full situation:

I have Compiz Fusion enabled with, of course, the Desktop Cube effect.  Now, a cube wouldn't be much of a cube with more or less than 4 sides, right?  Well, that's what I feel ;)

Anyway, when I try to set the number of desktops to 4 horizontal and any number of vertical, it resets the horizontal to 2.

I'm not sure if this is a bug with Compiz or the Desktop Switcher, because the problem occurs when I try to set either.

Exact same problem here. Plus when I change from one desktop to the other I lose my bottom bar and have to log out then back in to get it back.

---

### Post by vredley on 2009-03-14
I've disabled Compiz for now, but I also had the same problem. Funnily enough, I could set the number of horizontal desktops to anything but 4, so I got to see a 9-sided 'cube'. :)

---

### Post by Nightstrike2009 on 2009-03-19
I have the same problem on Ubuntu 9.04 Alpha 6, thought it was the Nvidia driver (180.35) at 1st but I've updated it to Nvidia 180.37 (after many mis-adventures trying to find correct files)and it still happens my thread is [http://ubuntuforums.org/showthread.php?t=1099569]("http://ubuntuforums.org/showthread.php?t=1099569") > When you go to Compiz Config Settings Manager from the menu, General Options>Desktop Size> Horizontal Size>
The slider resets itself at 4 and goes back to 2, it doesn't seem to do this on any other value. 

Looks like we are far from being alone with this problem, I am using a rotating triangle until i sort its different but would like the normal 4 sides :(

To quote eleifsp: > I'm not sure if this is a bug with Compiz or the Desktop Switcher, because the problem occurs when I try to set either.

I think this is down to a bug with one or both of these too.:(

UPDATE: I recently signed up for a launchpad account and have reported this as a bug, the best I could for a first time bug report. :)

---

### Post by Nightstrike2009 on 2009-03-19
I can confirm that shane8002 is correct with his workaround;

> **By Nightstrike2009** I think this is down to a bug but a workaround is possible, (originally discovered by shane8002)

Right click virtual desktops on bottom gnome bar (where you actually select them) RIGHT CLICK>PREFERENCES>
Set Workspaces to 4
Set Rows to 1
Click X to close

There you have it desktop cube with 4 sides :) hope this helps, until bug is fixed ;)

---

