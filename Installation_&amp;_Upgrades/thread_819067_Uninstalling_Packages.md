---
title: "Uninstalling Packages"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by BBurnham on 2008-06-05
right, so let's get start out with what all forums like to see, i'm a newbie when it comes to linux. i'm also a 3D modeling student who uses Autodesk Maya at my school. well i've downloaded the appropriate software, but what i downloaded were .rpm packages. I did not convert the .rpm to .deb like a few other forums had said <-- that was found out after the fact. well now i'd like to uninstall the .rpm and properly convert them to .deb for a cleaner install. the maya interface seems very sluggish and unresponsive, which is what i was hoping my linux os would not give me. 

here is the message i get when i try to uninstall the .rpm package

brian@Caveman:~$ sudo apt-get remove Maya2008_0-2008.0-116.i686.rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Maya2008_0-2008.0-116.i686.rpm
brian@Caveman:~$ 

thoughts?

---

### Post by iaculallad on 2008-06-05
> **BBurnham said:**
> I did not convert the .rpm to .deb like a few other forums had said <-- that was found out after the fact. well now i'd like to uninstall the .rpm and properly convert them to .deb for a cleaner install. the maya interface seems very sluggish and unresponsive, which is what i was hoping my linux os would not give me. 

here is the message i get when i try to uninstall the .rpm package

brian@Caveman:~$ sudo apt-get remove Maya2008_0-2008.0-116.i686.rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Maya2008_0-2008.0-116.i686.rpm
brian@Caveman:~$ 

thoughts?

Could that be possible? To install .rpm files without converting it to debian "readable" format?

Correct me if Im wrong: In the first place, if you did not convert your .rpm files to debian format (.deb), there's no need to worry. That maya application has not been installed on your machine. And to remove packages, you do not need to inpute the entire filename of the file (sudo apt-get remove Maya2008_0-2008.0-116.i686.rpm).

Run this on your terminal to get alien:

```
sudo apt-get install alien dpkg-dev debhelper build-essential
```

And to convert your .rpm file, input this in your terminal (Just be inside the directory where your .rpm file resides):

```
alien Maya2008_0-2008.0-116.i686.rpm
```

To install the converted package (Just be inside the directory where your .deb file resides):

```
sudo dpkg -i Maya2008_0-2008.0-116.i686.deb
```

---

### Post by warunsl on 2009-10-23
> Could that be possible? To install .rpm files without converting it to debian "readable" format?

Correct me if Im wrong: In the first place, if you did not convert your .rpm files to debian format (.deb), there's no need to worry. That maya application has not been installed on your machine. And to remove packages, you do not need to inpute the entire filename of the file (sudo apt-get remove Maya2008_0-2008.0-116.i686.rpm).
I think you can install .rpm files without converting to .deb packages (i.e., by not using 'alien'). You could achieve this if u have 'rpm' installed.

You could install an example.rpm package by :

```
rpm -ivh example.rpm
```If this gives an error saying /bin/bash is required by example.rpm then u could use the switch```
--no-deps
```

Correct me if i am wrong. I still haven't figured out how to uninstall packages, installed with 'rpm' as mentioned above.

---

