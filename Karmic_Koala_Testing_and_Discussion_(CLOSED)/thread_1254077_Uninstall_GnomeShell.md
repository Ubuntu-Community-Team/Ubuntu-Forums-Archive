---
title: "Uninstall GnomeShell"
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pedro3005 on 2009-08-30
I installed GnomeShell via source code (only option available). It was not a normal './confire && make && make install', rather some jhbuild thing. How can I uninstall it? Thanks.

---

### Post by psyke83 on 2009-08-30
> **pedro3005 said:**
> I installed GnomeShell via source code (only option available). It was not a normal './confire && make && make install', rather some jhbuild thing. How can I uninstall it? Thanks.

Go back to the source and run "sudo make uninstall".

If you need to build something from plain source, *always* use checkinstall. 

The checkinstall program builds a quick and dirty .deb package based on the files that "make install" wants to place on your system, and therefore makes uninstallation much, much easier.

---

### Post by pedro3005 on 2009-08-30
Uhm, I kinda stated that it wasn't a normal install, but used some sort of jhbuild, all I downloaded was a script, IDK where source is. But anyway, someone on IRC told me, I just purged jhbuild and everything it put on autoremove after that and deleted the ~/gnome-shell/ folder.

---

### Post by psyke83 on 2009-08-30
> **pedro3005 said:**
> Uhm, I kinda stated that it wasn't a normal install, but used some sort of jhbuild, all I downloaded was a script, IDK where source is. But anyway, someone on IRC told me, I just purged jhbuild and everything it put on autoremove after that and deleted the ~/gnome-shell/ folder.

Sorry, I missed the "not" in your original post ;).

---

### Post by qamelian on 2009-08-30
Just delete the gnome-shell folder that jhbuild creates in you home folder.

---

### Post by pedro3005 on 2009-08-31
Just also figured out, you need to go into gnome-shell/source and make uninstall. But I'm thinking that will only uninstall files inside gnome-shell, but who knows :)

---

### Post by nhasian on 2009-08-31
> **qamelian said:**
> Just delete the gnome-shell folder that jhbuild creates in you home folder.

hey thats what i said in irc :)

---

### Post by qamelian on 2009-08-31
> **nhasian said:**
> hey thats what i said in irc :)
Couldn't be any easier unless it deleted itself! :)

---

