---
title: "File Manager Craziness"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by puzzler995 on 2010-02-07
I have Alpha 2 and, my visuals had crashed so I force-restarted my computer with the power button. When I restarted GNOME there was a LOT of of programs rapidly cycling on the bottom bar. I moused over them and they all say "Starting File Manager". When I opened System Monitor I noticed the process number for Nautilus was also changing rapidly. I tried logging out and in several times, logging into Failsafe GNOME, and killing nautilus. 
I have taped this and posted it on YouTube so you can see what I am talking about [http://www.youtube.com/watch?v=_Qh9jxbIymk]("http://www.youtube.com/watch?v=_Qh9jxbIymk")

---

### Post by Gourgi on 2010-02-08
best chance in fixing this bug or at least the developers know about it is :
```
ubuntu-bug nautilus
```
explain the situation and attach the link to the screen captured video.

for now you can create another user and check if this happens to the new user too..
if not happening to the new user, try moving (backup) the 
~/.gconf*
~/.config
~/.local
~/.cache
~/.gnome*
 directories from the old user and see if it is reproducible.

---

### Post by puzzler995 on 2010-02-08
Well its gotten weirder. Now my desktop icons are gone, apport doesn't work, nautilus doesn't open at all, and when I try to log out when it is happening this pops up...

ubuntu-bug doesn't work... should I just completely reinstall GNOME???

---

### Post by lime4x4 on 2010-02-24
I have almost the same problem. Running the 64 bit version all updates applied.I only get the file-manager error when i try to enable 2 lcd monitors. Running the latest version of nvidia's drivers. If i try to enable the secong monitor i get a file-manager starting non stop in the lower left corner of my screen.

---

### Post by Ancanus on 2010-03-04
I got the same problem as the original post on Lucid Lynx Alpha 3. Needless to say, I am unable to browse my files with the GUI.

~$ ubuntu-bug nautilus
Could not import module, is a package upgrade in progress? Error: /usr/lib/pymodules/python2.6/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_spinner_stop
[I][U][B]
UPDATE[/B][/U][/I]

**REAL CAUSE:**
~$ python -c 'import gtk'
This should return a blank line, but I was getting some errors due to python pulling in some outdated libraries.
[B]
FIX:[/B]
I did 'make uninstall' on the following packages that I had a built a time ago:
glib-2.22.2
gtk+-2.18.2
gvfs-1.4.0

**AFTERMATH:**
File manager does not act up on Lucid Lynx Alpha 3 anymore, and ubuntu-bug opens up (but there's nothing to report anymore. =3 )


Make sure that if you manually installed any of those packages, remove them. Or somehow find how to point the programs to the updated ones.

---

