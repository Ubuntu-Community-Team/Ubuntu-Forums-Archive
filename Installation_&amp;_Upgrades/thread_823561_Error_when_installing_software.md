---
title: "Error when installing software"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by raylistic87 on 2008-06-09
hi i got this error while trying to install a software.

error: can't create transaction lock on /var/lib/rpm/__db.000

Is there any way to overcome this?

---

### Post by Rallg on 2008-06-09
First, does the file exist? Certainly /var/lib exists, but does the folder /var/lib/rpm exist, and if so, is there /var/lib/rpm/__db.000 within it?

If not, then you may need to manually create the folder (and possibly the file, and give them the correct permissions, so that root and [your username] can create and delete files within the folder, and read/write to the file.

After that, you might need to reboot.

Understand that the above is not necessarily the solution to your problem. But it's easy to do, and it won't hurt.

---

### Post by raylistic87 on 2008-06-09
It does not allow me to manually create the folder. Is there another way i can do it?

---

### Post by arpanaut on 2008-06-09
What are you trying to install?

It appears that you are trying to use a .rpm installer which is not natively supported by Ubuntu.

Try to find a .deb file for installation, failing that there is a program -> alien that allows installation of .rpm pacckages to your system, BUT this sometimes creates other issues with updating, and stability so the preferred way to install is with deb packages or compiling from source.

Have you checked in synaptic package manager if there is a native version for the program you need?

Hope this helps!

---

### Post by Rallg on 2008-06-09
Arpanaut is correct, about *.rpm files, and using the "alien" package to make them usable as native *.deb install files. If you can find your software in *.deb format, use it; otherwise install alien and convert the *.rpm to *.deb.

Now, back to my first response: You say that you cannot manually create the folder (I assume you mean /var/lib/rpm). That is correct, if you are simply going to the /var/lib folder and attempting to create something within it, the way you would do it in Windows operating system. The reason is that most places within Ubuntu (generally, Linux) require permission to do something. You will need to obtain the necessary permission.

In Terminal, try this:

gksudo nautilus

That calls up the file manager (in Ubuntu, it is Nautilus, but in other versions it will be something else). But by calling the file manager this way, you have additional permissions. Now, you may be able to create folders and files that you otherwise could not create.

It can get more complicated if you need to be in Terminal as root, particularly if you need to change permissions. But this is probably not the problem.

---

### Post by raylistic87 on 2008-06-09
Hi, I am trying to install maya 2008 and it comes in rpm format. I got this error when i am trying to install the software.

```
(Reading database ... 135601 files and directories currently installed.)
Preparing to replace awcommon 10.80-14 (using awcommon_10.80-14_i386.deb) ...
Unpacking replacement awcommon ...
/usr/bin/test: invalid integer `upgrade'
Setting up awcommon (10.80-14) ...
cd: 13: can't cd to /aw/COM/bin
cd: 14: can't cd to /aw/COM/bin
cd: 15: can't cd to /aw/COM/bin
cd: 16: can't cd to /aw/COM/bin
cd: 17: can't cd to /aw/COM/bin
cd: 18: can't cd to /aw/COM/bin
cd: 19: can't cd to /aw/COM/bin
cd: 20: can't cd to /aw/COM/bin
cd: 21: can't cd to /aw/COM/lib
cd: 22: can't cd to /aw/COM/lib
cd: 26: can't cd to /aw

```

```
rayster87@rayster87-desktop:~/Desktop/Maya$ sudo dpkg -i maya2008-0_2008.0-117_i386.deb
Selecting previously deselected package maya2008-0.
(Reading database ... 135601 files and directories currently installed.)
Unpacking maya2008-0 (from maya2008-0_2008.0-117_i386.deb) ...
dpkg-deb: unexpected end of file in between members in maya2008-0_2008.0-117_i386.deb
dpkg: error processing maya2008-0_2008.0-117_i386.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 maya2008-0_2008.0-117_i386.deb
```

Does anyone has any idea what went wrong?

---

