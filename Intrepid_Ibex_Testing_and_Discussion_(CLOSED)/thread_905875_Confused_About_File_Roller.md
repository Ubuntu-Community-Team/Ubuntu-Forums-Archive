---
title: "Confused About File Roller"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-08-30
Im confused about file roller and a bug I reported earlier that Im now checking up on. Somehow I was doing tests of 7z archives in file roller after that got added.

Now on a fresh install I dont have 7z available in the file roller menus.

Im confused if file roller changed but I dont see that in the package changelog. Is anyone else doing 7zs in a default install???

Here is my bug

[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/257812](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/257812)

And upstream:

[http://bugzilla.gnome.org/show_bug.cgi?id=547727](http://bugzilla.gnome.org/show_bug.cgi?id=547727)

And the package changelog:

[http://changelogs.ubuntu.com/changelogs/pool/main/f/file-roller/file-roller_2.23.6-0ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/f/file-roller/file-roller_2.23.6-0ubuntu1/changelog)

---

### Post by gspat on 2008-08-30
I had to install the 7zip package... forget the command though!

---

### Post by Nullack on 2008-08-31
This is why Im confused. The new file roller was supposed to use 7zip and its not dependant on 7zip? And its not in the menus as a format by default? I cant remember if I installed it or not when I originally reported the bug.

---

### Post by amano on 2008-08-31
The new file roller needs p7zip to be installed now for several formats, among them zip. In my eyes that would require p7zip to be promoted to main.

Or do I understand wrong?

---

### Post by Nullack on 2008-08-31
file roller has been packaged to not install p7zip. Im installing it now to test my other bug but I am going to bug this as it should be installed by default. The rar non free library is in another package so no closed source issues.

---

