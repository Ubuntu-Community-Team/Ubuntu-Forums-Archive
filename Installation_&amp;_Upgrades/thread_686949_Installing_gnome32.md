---
title: "Installing gnome32"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Deep fried ice-cream on 2008-02-03
I have been putting some games on a ubuntu 7.10 computer (no network yet, using flashdrive to transfer programs). but Ive run into problems with groach. It depends on the packege ligbgnome32; I download this and tried to install it but I ran ito the a problem:

libgnome32            requires      gnome-libs-data
gnome-libs-data    requires      gnome-bin
gnome-bin             requires      libgnome32

**HELP?!?!?**

---

### Post by ryanVickers on 2008-02-03
make sure that the library is in the correct folder.  this could be /lib, /lib32, /lib64, the game folder, I think there are "lib" folders in /usr, as well, etc etc...

---

### Post by Deep fried ice-cream on 2008-02-03
Umm.. I just have a floder with .debs I download in it.
what exactly do you mean?

---

### Post by ryanVickers on 2008-02-04
well, you just need to install them all then I guess... I just thought you said you downloaded a ".so" library and didn't know where to put it.

EDIT: I see what's wrong now, ok, you have 3 packages that require each other in an infinite loop.  Well, as far as I know it's impossible then, but try using synaptic to do it instead ;)

---

### Post by Deep fried ice-cream on 2008-02-04
Umm... How?
BTW I dont have an internet conection, I'm using a flash drive.

---

### Post by ryanVickers on 2008-02-04
open synaptic, either by entering "gksudo synaptic" in a terminal, or by going "System > Administration > Synaptic Package Manager".  Search up (by name) "libgnome32", "gnome-libs-data", etc etc and check them off for installation. then hit the big checkmark "Apply"

---

