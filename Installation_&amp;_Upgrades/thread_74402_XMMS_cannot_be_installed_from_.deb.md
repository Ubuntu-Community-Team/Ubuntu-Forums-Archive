---
title: "XMMS cannot be installed from .deb"
date: 2005-10-11
forum: Installation &amp; Upgrades
---

### Post by kurtkraut on 2005-10-11
Hi,

I need to listen to a SHOUTCAST radio. To do that, I need to use XMMS. When I attemp to install it from a .deb download from debian.org, I receive the following error:

root@ktk4:/home/ktk # dpkg -i xmms_1.2.10+cvs20050209-2_i386.deb
(Reading database ... 58489 files and directories currently installed.)
Preparing to replace xmms 1.2.10+cvs20050209-2 (using xmms_1.2.10+cvs20050209-2_i386.deb) ...
Unpacking replacement xmms ...
dpkg: dependency problems prevent configuration of xmms:
 xmms depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 xmms depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
dpkg: error processing xmms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xmms

-

I' ve attemped to use aptitude to get this missing packeges (libglib1.2 and libgtk1.2). For both I receive the following error:

root@ktk4:/home/ktk # aptitude install libglib1.2
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
No candidate version found for libglib1.2
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

I'm a linux newbie. How should I proceed ?

---

### Post by swerner on 2005-10-11
try ```
apt-get install xmms
```

---

### Post by kurtkraut on 2005-10-11
root@ktk4:/home/ktk # apt-get install xmms
Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

Any other suggestions ?

---

### Post by swerner on 2005-10-11
[QUOTE=kurtkraut]
Any other suggestions ?[/QUOTE]

Go to  [http://www.ubuntuguide.org/#xmms]("http://www.ubuntuguide.org/#xmms") and follow the step-by-step instructions, you will need to edit your /etc/apt/sources.list file.

essentially you just need to do steps 1 to 4 (and only the first line of step 4)

---

### Post by coolcehb on 2005-10-11
download libglib1.2 and libgtk1.2 manually from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), and put them in your home directory. Then install them using "sudo dpkg -i FileNameOfDownLoadedPackage.deb", on both of them. Now try to install XMMS. It might be better if you download XMMS from packages.ubuntu as well, but i am also a Linux newbie so I don't know.

---

### Post by kurtkraut on 2005-10-11
[QUOTE=swerner]Go to  [http://www.ubuntuguide.org/#xmms]("http://www.ubuntuguide.org/#xmms") and follow the step-by-step instructions, you will need to edit your /etc/apt/sources.list file.

essentially you just need to do steps 1 to 4 (and only the first line of step 4)[/QUOTE]


Hi,

Thanks for the help, but I followed all steps, from 1 to 8 and XMMS is not appearing on GNOME (Sound & Video) and when I double-click on an mp3 file, TOTEM MOVIE PLAYER opens insted of XMMS.

What should I do ?

---

### Post by swerner on 2005-10-11
Trying logging out and logging back in.

---

### Post by swerner on 2005-10-11
BTW, I use Rythmbox for listening to Shoutcast services.  But then I'm using Ubuntu 5.10 (which is due to be officially released in two days), but it should still work in 5.04.

---

### Post by kurtkraut on 2005-10-11
Hi,


I solved this downloading XMMS' package and all releated packages on packages.ubuntu.com

Thanks for the help.

---

### Post by coolcehb on 2005-10-11
glad to help :D

---

