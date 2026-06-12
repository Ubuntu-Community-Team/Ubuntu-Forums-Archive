---
title: "Desktop env"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by ascus4 on 2007-03-13
Hi all,

Do repositories, packages and software installed in one desktop environment become available in the other desktop environment?

Thank you,

---

### Post by ajgreeny on 2007-03-13
Yes, they do.  I have a bog standard Ubuntu with kubuntu-desktop added afterwards, and I can use gnome programs in KDE and KDE programs in gnome without any problems of note.  many people do the same; it's one of the joys of linux - you can configure it and change it as much as you want and you're not stuck with just one available desktop.

---

### Post by mojoman on 2007-03-13
Yes.

Repositories are enabled in /etc/apt/sources.list and that's the only file used for this. Regardless of who or what, i.e. what user and what desktop environment or window manager, this stays the same. 

It's the same with the packages and programs installed. As long as you're booting from the same partition and using the OS it all goes inte the same filesystem.

However, some applications might not be visible in the menu but if you install the debian meny (it's been a while but I think it's "sudo apt-get install menu") and update the menu (was that "update menu"?) it should show up in the debian menu. You could probably add it with for example ala carte menu as well. 

/mojoman

---

### Post by ascus4 on 2007-03-14
I suspected that was the case.  Wanted to be sure.

Thank you.

---

