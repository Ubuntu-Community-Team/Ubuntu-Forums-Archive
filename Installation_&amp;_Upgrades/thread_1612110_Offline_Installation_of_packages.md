---
title: "Offline Installation of packages"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by GK.Design on 2010-11-02
Is there a way to install ubuntu packages offline without a cd?

---

### Post by kostkon on 2010-11-02
Check [Keryx]("http://keryxproject.org/")

---

### Post by gordintoronto on 2010-11-02
Yes, you can download .DEBs from packages.ubuntu.com, save them on a flash drive, install from there.  You have to be really careful about dependencies, which are displayed on the web site. In other words, you need to install things in the right order.

---

### Post by GK.Design on 2010-11-03
How would I do that?:shock:

---

### Post by mutex023 on 2010-11-03
If you have another machine having ubuntu and is online, then first do the following on it - 
1. Delete all .deb files from /var/cache/apt/archive
2. Install the required packages from synaptic. (this will also install the dependencies)
3. Now copy all the downloaded .deb files from /var/cache/apt/archive to your usb drive. 

Next, on the machine which is offline, plug in the usb drive, and start installing by double clicking each .deb file. You might get an error in RED saying 'dependency not satisfiable....' , it will also mention the package name. In that case, install the dependency .deb file first, and THEN install this one.

---

