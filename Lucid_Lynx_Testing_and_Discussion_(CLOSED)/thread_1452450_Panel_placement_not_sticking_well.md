---
title: "Panel placement not sticking well"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-04-11
I run with both panels on top.  I put launchers on to suit my taste.  I do not like any of the docks I have tried at all.

The problem is that when I boot to some of my installations (it works fine on the upgraded ones) the original top panel, which should and needs, to be on top.  Is below the original bottom panel.

Ok, so I can click on properties and fix this every time.  I would like to know one or two things.

Is there something I am missing in gconf-editor?  I have set the panels the same as in 9.04 which is the same as it is in my 9.10>10.04 and 6.04>9.10>10.04 upgrades.  At least I think I got all the places in gconf-editor that should matter.

The other is, if there is no way to set this what package do I file the bug on and to whom (Ubuntu or Gnome)?

---

### Post by djchandler on 2010-04-12
I got it to stay where you like it by placing the hide buttons on the lower panel via the properties dialog. The lower panel kept its place after logging out and back in, and  after a re-boot.

What needs to be changed in gconf I can't tell you, but the button idea may give you a clue.

---

### Post by ranch hand on 2010-04-21
I have found that deleting the bottom panel and then creating another one then moving it to the top sticks fine.

I do have to log out and back in to be able to see the new panel.

---

### Post by djchandler on 2010-04-21
> **ranch hand said:**
> I have found that deleting the bottom panel and then creating another one then moving it to the top sticks fine.

I do have to log out and back in to be able to see the new panel.

Or maybe placing it somewhere else first as I did does about the same thing. I have been moving the bottom panel to the right side, so that's where it was before putting it up under the top panel to see what was going on with your situation.

Since you opened this can of worms, I've been playing around a lot with that panel. Right now I have it back on the bottom and auto-hiding, expand turned off and buttons visible. I like getting as much vertical height out of my windows as possible, and the bottom panel configured that way doesn't interfere at all.

---

