---
title: "I know!!"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-08-28
I know this isnt even the right website, but I dont want to make an account on another. i am trying to edit the /etc/X11/xorg.conf in openSUSE, but when I run "sudo gedit /etc/X11/xorg.conf", i get this message:```
william@linux-464s:~> sudo gedit /etc/X11/xorg.conf
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
william@linux-464s:~> 
```

what can I do so that I can modify this as root?  Thanks a ton!

---

### Post by Pumalite on 2007-08-28
gksudo gedit blah blah blah

---

### Post by ErusGuleilmus on 2007-08-28
no luck, 
```
william@linux-464s:~> gksudo gedit /etc/X11/xorg.conf
bash: gksudo: command not found
william@linux-464s:~> 
```

---

### Post by Pumalite on 2007-08-28
Try sudo su

---

### Post by kerry_s on 2007-08-28
> **ErusGuleilmus said:**
> I know this isnt even the right website, but I dont want to make an account on another. i am trying to edit the /etc/X11/xorg.conf in openSUSE, but when I run "sudo gedit /etc/X11/xorg.conf", i get this message:```
william@linux-464s:~> sudo gedit /etc/X11/xorg.conf
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
william@linux-464s:~> 
```

what can I do so that I can modify this as root?  Thanks a ton!

yep, you need to "su" first than "gedit /etc/X11/xorg.conf". funny though the last time i used suse there was a gui for that sort of thing. :confused:

---

### Post by merlinus on 2007-08-28
> **kerry_s said:**
>  funny though the last time i used suse there was a gui for that sort of thing

xorg-edit_07.06.15-0ubuntu1_i386.deb

-merlin

---

### Post by ErusGuleilmus on 2007-08-29
that did work. thank you. In on my laptop in Ubuntu, I had to go into the xorg file and change the driver from "nv" to "nvidia". This enabled 3d, I did this in suse, and it didn't break x, but it appears as if I still don't have 3d. :( Oh well, its not an Ubuntu forums problem. Thanks again.

---

