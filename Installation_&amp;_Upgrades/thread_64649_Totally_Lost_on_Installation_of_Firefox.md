---
title: "Totally Lost on Installation of Firefox"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by Shyly on 2005-09-11
I'm new to Linux and just starting to get the hang of it but I've never tried to install something on my own before, so if someone could please point me in the right direction I'd appreciate it. 

I just download Firefox 1.5b and it's in home/My Downloads.   Where do I go from here? 

Thanks

---

### Post by codejunkie on 2005-09-11
[QUOTE=Shyly]I'm new to Linux and just starting to get the hang of it but I've never tried to install something on my own before, so if someone could please point me in the right direction I'd appreciate it. 

I just download Firefox 1.5b and it's in home/My Downloads.   Where do I go from here? 

Thanks[/QUOTE]
well that version of firefox that your trying to install is in beta and doesn't have an installer included yet at least mine didn't what you have to do with the beta is extract the files to a folder for example /home/yourusername/firefox and inside there you'll find a file named firefox.sh or firefox double click on that file and then click run this will start firefox to put shortcut on your desktop to launch firefox rightclick on your desktop and choose create launcher and use this as the command /home/yourusername/firefox/firefox hope this helps.

---

### Post by Shyly on 2005-09-11
I had it in there once and I thought it was wrong.  Thanks

---

### Post by mental_noise on 2005-09-11
I too am new to Ubuntu and Linux in general.  I just downloaded Mozilla Firefox 1.0.6 and it is in **.tar.gz** format.  I was wondering how I could install this to Ubuntu.  And I would also like to ask that by installing ver 1.0.6, will this update ver 1.0.2 which is part of the Ubuntu installation?

I appreciate all the help I could get since I find Ubuntu very good. :)

Thanks!

---

### Post by wellery on 2005-09-11
[QUOTE=mental_noise]I too am new to Ubuntu and Linux in general.  I just downloaded Mozilla Firefox 1.0.6 and it is in **.tar.gz** format.  I was wondering how I could install this to Ubuntu.  And I would also like to ask that by installing ver 1.0.6, will this update ver 1.0.2 which is part of the Ubuntu installation?

I appreciate all the help I could get since I find Ubuntu very good. :)

Thanks![/QUOTE]

Even though it says that the current version is 1.02. It actually has all the pataches applied and is equivalent to version 1.0.6.

---

### Post by Thulemanden on 2005-09-12
I would forget about installing these from .gz (and compiling) as for now .

Open /etc/apt/sources.list and remove the # from the line with 'universe' in it (or is it universal?) 

Save it and then run as root: apt-get install mozilla-firefox in a terminal window (console) and it should install itsself correctly.

---

### Post by Elrohir on 2005-09-12
search for some enlightment on [www.ubuntuguide.org](www.ubuntuguide.org)

it helped me a lot!

---

