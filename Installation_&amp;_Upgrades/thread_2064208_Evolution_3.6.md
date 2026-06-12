---
title: "Evolution 3.6"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by Jeannijhuis on 2012-09-28
If I had a package, eg "evolution-3.6.0.tar.xz" to install, I read that you should be able to do this by the following commands.
-. / Configure
- make
- Make install

But I get the following message back.
"make: *** No targets specified and no makefile found. Stopped."

What goes wrong?

---

### Post by Frogs Hair on 2012-09-28
That may happen if there are missing dependencies . Evolution 3.6 is in the 12.10 repository which uses a different version of Gnome and it may not be compatible with 12.04 or earlier.

---

### Post by darkod on 2012-09-28
First of all, to compile software you must install the build-essential package (or build-essentials, not remember if it had S at the end).

So install that first:
sudo apt-get install build-essential(s)

Then, you need to unpack the .tar.gz if you didn't do it. Usually it will unpack in a folder of the same or similar name as the file. Go into that folder.

Once you are in the folder try the:
sudo configure
sudo make
sudo make install

---

### Post by vigyani on 2013-01-01
Hi
Did you succeed in compiling and using latest version of evolution? Please share your experience?
What are the steps you followed?

Thanks 
Vig

---

