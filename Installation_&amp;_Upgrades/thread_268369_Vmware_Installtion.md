---
title: "Vmware Installtion"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by penguinchrissy on 2006-09-30
I'm trying to install vmware player and I'm having the following problems 
In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/bin/gcc-3.4

The path "/usr/bin/gcc-3.4" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/bin

The path "/usr/bin" is an existing directory, but it does not contain a "linux"
subdirectory as expected.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

[http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)

that is the site from which I was getting my instructions

---

### Post by jpkotta on 2006-09-30
```
sudo apt-get install linux-headers-`uname -r`
```
or maybe
```
sudo apt-get install linux-source-2.6.15
```
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by penguinchrissy on 2006-10-03
it was the second suggestion thanks very much.

---

