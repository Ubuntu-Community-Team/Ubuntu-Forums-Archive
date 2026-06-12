---
title: "Easycam installation in jaunty"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-03-24
I am trying to install easycam to install my webcam drivers in jaunty, but the repo provided in the ubuntu wiki is for hardy, and when i add it to my sources and try to install it, it just throws an error.

Anyone have any luck of getting it installed?

---

### Post by ajmorris on 2009-03-25
hi there,
what error are you getting?
The hardy repo (assuming these two are the ones you added:) (src is optional)

[I]deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main[/I]

should work fine on your jaunty system.

Also, as an alternative to installing them with apt, you could make sure you have all dependencies, and download the .deb file, and manually install it with dpkg. But first paste the errors you're getting here.

AJ

---

### Post by Polygon on 2009-03-27
> 
mark@Polygon:~$ sudo apt-get install easycam2-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-gtk: Depends: python2.4-glade2 but it is not installable
                Depends: python2.4-gtk2 but it is not installable
E: Broken packages
mark@Polygon:~$ 


yeah and i cant find those packages either....

---

### Post by executorvs on 2009-04-12
has anyone found a fix to using easycam in jaunty?

---

### Post by Polygon on 2009-04-12
there is none i dont think, the guy who makes the program has to package it for other distros, or provide the source at least...which i am not seeing

---

### Post by oserdavid on 2009-04-19
If anyone knows any workaround for getting easycam2 into Jaunty - I would also be very interested to hear about it!!
David

---

