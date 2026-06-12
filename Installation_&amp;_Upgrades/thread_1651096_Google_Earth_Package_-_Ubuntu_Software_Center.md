---
title: "Google Earth Package - Ubuntu Software Center"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2010-12-22
I've just installed "googleearth-package" from the Ubuntu Software Center.

Now what do I do with it?



Thanks, Hannibal

---

### Post by sanderd17 on 2010-12-22
press ALT+F2 and type "googleearth"

---

### Post by coljohnhannibalsmith on 2010-12-22
Wow,

That was fast!

I get the following error message when I try it:

Error stating file '/home/sophie/googleearth': No such file or directory

---

### Post by karthick87 on 2010-12-22
Dont you find google-earth in Applications Menu???

---

### Post by coljohnhannibalsmith on 2010-12-22
Sorry, no.

I checked for it twice!

---

### Post by karthick87 on 2010-12-22
How did you installed it??

---

### Post by ottosykora on 2010-12-23
there is no app resulting from this install, this is just some kind of life installer to grab and compile the gogle earth from google itself. The app itself does not do anything.
Check for some man files which came with it.

---

### Post by tdockery97 on 2010-12-23
The googleearth-package downloads Google Earth and makes it into a .deb package.  Open terminal and type:

make-googleearth-package --force

It will then download the googleearth .bin file and convert it into a .deb file.  Then just use dpkg or gdebi to install the .deb package.

Don't be alarmed when it gives a bunch of error messages while building the .deb package.  This is normal.

---

### Post by coljohnhannibalsmith on 2011-05-02
> **tdockery97 said:**
> The googleearth-package downloads Google Earth and makes it into a .deb package.  Open terminal and type:

make-googleearth-package --force

It will then download the googleearth .bin file and convert it into a .deb file.  Then just use dpkg or gdebi to install the .deb package.

Don't be alarmed when it gives a bunch of error messages while building the .deb package.  This is normal.

Thank you,

That worked; but it wouldn't run when I tried to launch it.  It was then removed from the repository stating that the architecture was incompatible.  The .deb from Google earth wouldn't run either.

Does anyone know if this has been corrected?

---

### Post by coljohnhannibalsmith on 2011-05-03
Finally,

Their x64 .deb package now works under Unbuntu..


while true; do echo -n "Yeah! "; done

---

