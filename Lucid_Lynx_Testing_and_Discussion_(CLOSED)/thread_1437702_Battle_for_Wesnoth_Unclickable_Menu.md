---
title: "Battle for Wesnoth Unclickable Menu"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Xorlathor on 2010-03-24
I'm using Ubuntu 10.4, which probably means alot here. My problem:

I installed Battle for Wesnoth fine via the Software Center and there weren't any errors. I double checked to make sure it had all the right packages, and it had all of them. I started up BfW and it worked perfectly - showed the loading bar, the opening slide animation, and then showed the menu.

However, whenever I click any of buttons, nothing happens. My mouse is working, and whenever I mouse over a button it shows the description on the bottom. This same problem results when I start the BfW Map Editor - I can move the mouse around, but clicking has no effect.

Is this a common problem for BfW? How can I fix it? Thanks for your help!

---

### Post by gibbylinks on 2010-03-24
I have same problem here also running Lucid

---

### Post by Xorlathor on 2010-03-24
Okay, looks like this might be a common bug with Lucid - anyone know a fix?

---

### Post by donkyhotay on 2010-03-24
Check and see if this has been reported in launchpad yet. If it hasn't you should probably file one.

---

### Post by _h_ on 2010-03-24
I'm downloading Wesnoth right now, and will also see if I get the same issues.

Standby.

---

### Post by _h_ on 2010-03-24
Indeed, I am getting the same issues.

---

### Post by Xorlathor on 2010-03-24
So, what should we do?

---

### Post by _h_ on 2010-03-24
> **Xorlathor said:**
> So, what should we do?

Exactly what donky said:

> **donkyhotay said:**
> Check and see if this has been reported in launchpad yet. If it hasn't you should probably file one.

---

### Post by donkyhotay on 2010-03-24
This is obviously not an upstream bug (something specific to wesnoth) but a problem with 10.4 itself since I run 9.10 and have no problems with wesnoth whatsoever. As I suggested previously, check launchpad to see if the devs are aware of this bug already and if not file a bug report.


//edit: Ninja'd!

---

### Post by Xorlathor on 2010-03-24
Sorry for being stupid here - how should I file a bug report in launchpad?

---

### Post by Perfect Storm on 2010-03-24
read this about testing and all you need to know; [http://ubuntuforums.org/showthread.php?t=1343449](http://ubuntuforums.org/showthread.php?t=1343449)


Thread moved.

---

### Post by gibbylinks on 2010-04-04
Apparently this is a known bug in Lucid. [http://forums.wesnoth.org/viewtopic.php?f=4&t=29433&p=419561#p419561](http://forums.wesnoth.org/viewtopic.php?f=4&t=29433&p=419561#p419561)

You can get around it by using full screen (ctrl+f) :guitar:

---

### Post by zekopeko on 2010-04-04
The bug should be reported against libsdl in Launchpad.

---

### Post by gibbylinks on 2010-04-04
It has been

[https://bugs.launchpad.net/libsdlgame/+bug/528957](https://bugs.launchpad.net/libsdlgame/+bug/528957)

;)

---

### Post by gare on 2010-04-04
Hello -

This is reported bug:

[https://bugs.launchpad.net/debian/+source/wesnoth/+bug/528957](https://bugs.launchpad.net/debian/+source/wesnoth/+bug/528957)

> workaround is to play wesnoth in full screen mode:

open terminal window

> wesnoth --fullscreen

---

### Post by LKjell on 2010-04-04
The game is a bit addictive :)

---

