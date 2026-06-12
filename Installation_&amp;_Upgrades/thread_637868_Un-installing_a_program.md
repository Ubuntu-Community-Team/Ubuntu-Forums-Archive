---
title: "Un-installing a program"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by delilahjed44 on 2007-12-11
Hey everyone, I am not able to use this program and I went through the terminal and tried to un-install it as did the Add/Remove programs < of course it is not there.  So here are the un-install directions, I am doing something wrong here and cant seem to burn the image in my to do an exact as if calls for with un-installing, can anyone help? when I try to use this path in my terminal it sais no command....

Thank you.

Sherri  

  Screem installation instructions
---------------------------------

There are 5 simple steps to installing Screem:

1) ./configure        (or ./autogen.sh for CVS builds)
2) make
3) su 
4) make install
5) exit

optional further steps
----------------------
6) make clean

Step 3 will prompt you for the root password.
Step 5 will exit from running as root
Step 6 will clean up the files used when building Screem that aren't needed
now.  All this will do is give you a bit more disk space so there is no
need to worry about it.

By default Screem installs itself in /usr/local.
If this isn't where your Gnome installation is then you may want to do the
following at step 1

./configure --prefix=<gnome install path>

where <gnome install path> is where gnome is installed
(For RedHat 6.x this is /usr)


Should you wish to uninstall Screem and you still have the source directory 
around then follow these 2 steps:

As in step 3 for installation step 1 here will prompt you for the root
password. step 3 here does the same as step 5 for installation.

1) su
2) make uninstall
3) exit

If you no longer have the source then you can do it by hand. although this
will leave a couple of files on your system, ie. the screem icon and
.desktop file (used for the gnome panel menu entry) 

1) rm <install path>/bin/screem
2) rm <install path>/lib/screem -r
3) rm <install path>/share/screem -r
4) rm <install path>/pixmaps/screem -r

---

