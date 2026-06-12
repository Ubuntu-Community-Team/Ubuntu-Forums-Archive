---
title: "How to change the gnome menubar icon"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-04-15
How to change the gnome menubar icon in Lucid?

This is something I have had problems with in every gnome version I have ever used.

The latest "solution" I found was to create a mirror of the current icon theme in your ~/.icon directory containing only the "start-here.svg" with the icon you want to use as a replacement.
Even this failed (as did trying start-here.png).

I am actually wanting to use a transparent icon so I can use my custom "favourites" menu, which then appears as the menubar icon but is a separate menu in it's own right.

I hate having to change the actual icon in /usr/share/icons (presuming that still works) because they get overwritten after updates.

<sigh>

---

### Post by Ibidem on 2010-04-15
man dpkg-divert
#Looks promising to me, especially the example:
dpkg-divert --divert /usr/bin/example.foo --rename /usr/bin/example

FYI: dpkg-divert makes sure that packages rename a specified file (/usr/bin/example above) to  another name; that way your local changes will not be overwritten.
I presume you restarted GNOME?...

---

### Post by x-shaney-x on 2010-04-15
Oh dear, my fault <ahem>
Turns out I made a slight typo in one of the folders in .icons <blush>

I never thought about dpkg-divert but thanks for that I'll remember that in future.

I still think there should be a much more straight forward way to do this.

---

