---
title: "Improper naming of default applications"
date: 2009-06-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cleentrax on 2009-06-04
There are two strange ways default applications are named in Ubuntu menus.

There are three naming conventions, and I can't find any rationale for the way they are used.

#1: Some apps don't get a name, but just a description.

For example, Totem is called "Movie Player." Gedit is called "Text Editor."

I can't tell you how many times I have tried to launch Gedit unsuccessfully from Gnome Do and had to remember to type text editor instead of gedit.

Now why do we need a tool tip popup with a description, if we are already replacing the name with a description?

#2 Some apps get both a name and a description in their name, even some of the apps which are most obvious.

For example, Rhythmbox becomes "Rhythmbox Music Player" and Firefox becomes "Firefox Web Browser."

#3 Some apps just get their name in the menu.

Option #2 is annoying, but not a big problem. But I can see #1 being an issue. Imagine someone trying to figure out how to use gedit, and they think it is called text editor. How do you search for that online? how do you find it in synaptic, or install or uninstall it from the command line if you don't even know what it is called?

What do you think about the following?

A) consistent naming for all apps in menus, with real name of application, and a tooltip popup that describes what it does.
B) consistent and obvious way to find out what primary repository package is associated with an application (for example, that epiphany is epiphany-browser, not "epiphany" and that "Text Editor is "gedit".) This could be done with a right-click in the menu, or in the "About" item in the app's dropdown menu (sometimes it is there, but it is inconsistent).

---

### Post by davideotape on 2009-06-04
I think in all fairness that the names are designed so as not to alienate new users. Gedit means nothing to a new user whereas text editor does.

---

### Post by pferraro on 2009-06-04
Regarding #1, if you configure gnome-do to show the results window, you'll see that gedit is indeed one of the options (albeit not initially the 1st) after typing "gedit".

---

### Post by cleentrax on 2009-06-04
But why the inconsistency? Why do we put the names Brasero, Rhythmbox and Firefox in the title, but not the names Gedit or Totem? And why have both a popup description and a description in the title itself? It's not logical, consistent or elegant.

You don't see this type of thing in Windows or OSX. It's like Ubuntu is constantly apologizing for having strange applications with silly names, so it hides them.

---

### Post by davideotape on 2009-06-04
I suspect that there's something on brainstrom covering this. If not, start a new idea about menu consistancy :)

---

### Post by tom56 on 2009-06-04
If I recall correctly this is covered somewhere in GNOME's Human Interface Guidelines (HIG). There is a rationale behind what gets what name.

---

### Post by jblackhall on 2009-06-04
This sounds like a good topic for the Ayatana people.

---

### Post by yoasif on 2009-06-04
+1 from me. I think this definitely needs some attention, especially for all of main.

---

### Post by xebian on 2009-06-04
If you don't like the names/description, you can always change it to what your heart desire.  Have you ever heard of the menu editor?

---

### Post by Amaranth on 2009-06-05
Things like gedit and totem get generic names only because you don't need to know their name and it is unlikely you'll ever have more than one installed. Things like Rhythmbox get the name and description because with just the name you may not know what it is but you may install another media player and need some way to tell them apart.

Firefox only has the name included because more people know what "Firefox" is then know what "Web Browser" is otherwise it should be just "Web Browser" too.

Also, yes, you can use the menu editor to change the names or hide rhythmbox if you install banshee but that's not something a new user will know.

---

