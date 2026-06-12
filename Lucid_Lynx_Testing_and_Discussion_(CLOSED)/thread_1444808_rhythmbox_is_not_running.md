---
title: "rhythmbox is not running"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hourna on 2010-04-01
when i start rhythmbox, the rhythmbox icon appears on the navigation area. however, when i click on it, rhythmbox won't appear and icon in the notification area gets highlighted but nothing happens. also it has no right click menu.

any ideas?

---

### Post by drs305 on 2010-04-01
I'm not on my Lucid machine at the moment, but I think you can right click the icon and select an option that opens the GUI interface. That will get you started, someone else will have to look at the options to tell you how to change the default behavior.

---

### Post by hourna on 2010-04-01
as i said in my first post, there is no right click menu.

---

### Post by drs305 on 2010-04-01
Sorry about that. Have you tried opening it in terminal or checked the man page. In the version in Karmic, there is a terminal option to show the UI options (--help-gnome-ui). Using some of those may allow you to attempt to open the interface and may provide an error message.

Or perhaps it's just a bug, which you can search for on Launchpad to see if anyone else is experiencing the same problem.

Added after sgage's post:
Did I say *right* click. I obviously meant *left* click. ](*,)

---

### Post by sgage on 2010-04-01
They've changed the way it works, presumably because the rhythmbox icon is now operating out of the indicator applet (?). You now left-click on the icon, and get more or less the same options you used to get with a right-click. 

It's working that way here - I left-click and see:

- the name of the playing song
- a checkbox to play/not play
- previous
- next
- show rhythmbox
- quit

---

### Post by hourna on 2010-04-01
ok, i have found a way to fix it. i remove the "indicator applet" from the panel, and re-added it and now it is working. thanks for helping me sorting that out =)

---

### Post by hourna on 2010-04-01
on second thought, i realized that it is still not good. after i close and re-open it to see if it is really fixed, i end up with the same proplem.

if indicator applet is removed from the panel, rhythmbox just starts fine and it minimizes to the lower panel. if i add indicator applet to the panel while rhythmbox is running, it minimizes to its icon and when i click on the icon everything looks fine. it works as it should. however, when i close the rhythmbox and start again, its icon on the indicator applet appears but it clicking on it does not work.

---

