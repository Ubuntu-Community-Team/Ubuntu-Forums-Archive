---
title: "manual uninstallation"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by silversun on 2005-04-19
Hi, 
sorry if this question sounds dumb, but how do you uninstall a software which you manually installed by compiling the source and doing make install?

note: i am not referring to packages installed by apt-get. 

Thanks :)

---

### Post by heimo on 2005-04-19
If you're lucky, *make uninstall *in the same directory where you did *make install, *may work. Otherwise.. I don't know. Manually file by file? :-/
 
EDIT: I'm not dpkg / apt-get guru (I'd like to be), but I recall faintly that there's a way to find which files came from deb packages - that could give a clue which files to remove, if make uninstall is not possible.

---

### Post by silversun on 2005-04-19
[QUOTE=heimo]If you're lucky, *make uninstall *in the same directory where you did *make install, *may work. Otherwise.. I don't know. Manually file by file? :-/
 
EDIT: I'm not dpkg / apt-get guru (I'd like to be), but I recall faintly that there's a way to find which files came from deb packages - that could give a clue which files to remove, if make uninstall is not possible.[/QUOTE]
 I think there isnt a make uninstall for what i am looking at. 
would i have to manually delete all the files?

---

### Post by heimo on 2005-04-19
Perhaps not manually file by file, but making a script - compile the program again (if not already), check which files would be installed with make install and figure out how to reverse this operation (make a list of those files, move or remove the installed files). There's probably some more clever way - and this method may be tedious, but if there's only handful of files installed for that program, this method may be quite ok, I guess.

---

### Post by Dr Gonzo on 2005-04-20
There's a program called checkinstall that will allow you to build deb packages out of software you compile from source.  Generally, they're only good on your system, but it allows dpkg (apt-get's backend) to keep track of everything.

Do it the Debian way.  Google for checkinstall and install it using apt-get.  It's in universe.

---

### Post by heimo on 2005-04-20
Oh, that's good advice! I was speaking from the point of view where something has already been installed, but it's much better to prevent getting in that kind of situation. Using only package managers packages to install software will make life a lot easier. (or installing non-deb software under home or opt)

---

### Post by codejunkie on 2005-04-20
[QUOTE=silversun]Hi, 
sorry if this question sounds dumb, but how do you uninstall a software which you manually installed by compiling the source and doing make install?

note: i am not referring to packages installed by apt-get. 

Thanks :)[/QUOTE]
open up gnome-terminal go to the directory where you uncompresed the folder and installed and compiled from probably cd  /home/yourusername/name-of-file-installed/ and type sudo make uninstall that should do it unless you already deleted that folder.

if you already deleted that folder/file i think you could download it again recompile and at make install -n, --just-print, --dry-run, --recon that should point out installed items then manually delete them.

---

