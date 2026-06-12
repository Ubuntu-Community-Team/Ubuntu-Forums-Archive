---
title: "ubuntu on low ram computer"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by sammywham on 2008-04-15
I have a computer with these specs:
Toshiba Satellite Laptop 
pentium III 500mhz
64 megs of ram
5gig harddrive
Dvd rom drive
floppy drive
1 usb port
What os should i install for usable gui?:confused:

---

### Post by aysiu on 2008-04-15
Try Damn Small Linux or Puppy Linux.

---

### Post by Gen2ly on 2008-04-15
Possibly XFCE (Xubuntu), more likely Fluxbuntu.  Everything there is good expect that 64 MB of RAM is a killer.  I don't have the spec in the noggin' but their respective web pages should.  Ubuntu will need about 256MB 2 begin.

---

### Post by kerry_s on 2008-04-15
dsl would be best for such low ram-> 
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)
there's now screenshots for both versions, so you can see what they look like.

if you can get more ram it would be much better, you'll have even more options.
my systems 450mhz 256mb ram, i use a custom debian install.

---

### Post by stream303 on 2008-04-15
This might be just what you are looking for:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

With such low memory, you'll have to live realistically within the 64mb limitations, ie using ImageMagick instead of Gimp for photo editing, getting comfortable with the commandline etc.

I personally like using LWM as my window manager, and just use command lines for file management, or if I'm feeling bloaty, I use lynx in file-manager mode, ie

```
lynx /usr/share/doc
```

and browse the docs.  For browsing through your home directory, just

```
lynx .
```

will do the trick.  Lynx isn't just for web-browsing. :)

I've used lynx as an idea of how to think-small, but sometimes I find that low-memory installs get the most creativity out of me. :)

---

### Post by kerry_s on 2008-04-15
very creative, i use mc swallowed to the desktop, with a term swallowed under mc for term work so i don't have to press ctrl+o to pop back and fourth from term to file manager. :)

---

