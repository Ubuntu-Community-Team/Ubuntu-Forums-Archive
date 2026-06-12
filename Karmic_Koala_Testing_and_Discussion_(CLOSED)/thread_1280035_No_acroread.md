---
title: "No acroread?"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2009-10-01
Does anyone know where Acrobat Reader (acroread) has hidden itself?

I've even installed Medibuntu, and I can't find the acroread package.

When I use aptitude to search the package list, all it finds is the package "acroread-fonts".

---

### Post by gordintoronto on 2009-10-01
In Jaunty's Synaptic, it is called acroread.

---

### Post by 23meg on 2009-10-01
[http://ubuntuforums.org/showthread.php?t=1275214](http://ubuntuforums.org/showthread.php?t=1275214)

---

### Post by utnubuuser on 2009-10-01
Just enable the Ubuntu partner repositories in your Synaptic sources.

---

### Post by christian.convey on 2009-10-01
Thanks.  So to summarize:

- It's in the Ubuntu Partner Repositories, which you have to explicitly enable in the Software Sources.  But only the 32-bit one so far.

- Use Okular (kde) or Evince (gnome) if you can, unless you really need 64-bit Acrobat Reader, in which case you just need to be patient.

---

### Post by NormanFLinux on 2009-10-01
Just download and install Adobe Acrobat from the Adobe website using the .deb package. Install with Gdebi. It Installs Adobe Acrobat Reader 9.

---

### Post by Hated On Mostly on 2009-10-01
If you need the 64-bit version (as well as the 32-bit version) of Adobe Reader (acroread), get it from the Debian Multimedia repository:

[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)

Get if from oldstable, stable, testing, or unstable depending on what version you want. I have installed this and several other packages from this repository with no problems in Ubuntu 8.10 (Intrepid Ibex).

Adobe Reader shouldn't have been removed from Medibuntu until Adobe released an official 64-bit version, not just a 32-bit version.

---

