---
title: "[SOLVED] glipper crashes every time in Intrepid"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by the real omni on 2008-09-30
Just updated from 8.04 to 8.10 alpha 5 and now glipper crashes 100% of the time, doesn't even make it as far as placing the icon into the gnome panel.

[https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/257052](https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/257052) <-- that's the Launchpad bug report, which states:

> This happens because "/var/lib/python-support/python2.5/glipper/keybinder/_keybinder.so" is linked against libffi4, but libffi5 is installed in Interpid and libffi4 is not a dependency of glipper.

I've tried installing libffi4 but 'sudo apt-get install libffi4' gives me this output:

> Package libffi4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  lib32ffi4
E: Package libffi4 has no installation candidate

So of course the next step is to try 'sudo apt-get install lib32ffi4' but that errors out with:

> The following packages have unmet dependencies:
  lib32ffi4: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.4-3ubuntu2 is to be installed
E: Broken packages

How do I get libffi4 installed in Intrepid so I can have a clipboard manager that works?

I've tried installing parcellite and it installs with no problems, and it runs with no problems, but the problem that I run into with parcellite is it doesn't seem to do what it's supposed to do.. It sits in my gnome panel and I can click on it to get a list of previous clipboard entries, but if I copy something in FireFox and then close FireFox the clipboard is still emptied. :( So it seems I'm going to need to get glipper working... Just need to know how!

---

### Post by the real omni on 2008-10-03
Fixed as of 08-10-02

---

