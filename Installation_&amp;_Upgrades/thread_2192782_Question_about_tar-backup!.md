---
title: "Question about tar-backup!"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by Nane_89 on 2013-12-09
Hello, im new to Linux!

I have a question about backing up my system from the terminal with tar (i found [this]("http://ubuntuforums.org/showthread.php?t=35087") guide).

Lets say im backing up my Ubuntu 12.10. Is it possible to make a clean install with Ubuntu 13.10, get all updates, and then restore my ubuntu 12.10 backup?

Thank you!

---

### Post by Irihapeti on 2013-12-09
I'm assuming that you're talking about your user files. Otherwise, you'd end up with a mashup of 12.10 and (mostly) 13.10 system files.

You can quite safely restore your visible user files. That is, the folders Documents, Music, Videos etc and any folders that you've created.

Restoring the invisible files and folders, that is, ones starting with a dot such as .config, .cache, is a different story. Programs change their configuration layout and what worked nicely with an earlier version may not work with the new version. The best idea there is to try replacing them program by program. If it works, great; if it doesn't, remove it and the program will regenerate a new configuration.

---

### Post by sudodus on 2013-12-10
Welcome to the Ubuntu Forums :-)

I don't know exactly what you want to do. Please explain with more details!

- Backup of files, there are several program packages for it
- Backup of whole system, there are several program packages for it
- Cloning of partition or whole drive (exact copy or image),  there are several program packages for it

You can use the [One Button Installer]("https://wiki.ubuntu.com/phillw/OBI"), and create a tarball, that can be restored into the same or another computer. This is one example of what can be done (and ***tar*** is only one of many tools under the hood of a graphical user interface, that does the work, ***rsync*** is another tool).

---

