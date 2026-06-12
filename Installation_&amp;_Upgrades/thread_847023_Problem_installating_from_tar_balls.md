---
title: "Problem installating from tar balls"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by motapa on 2008-07-02
Hi all. I have just moved from openSuse 10 to ubuntu trying to run away from its deamons, however I am meeting with others on this distro. I can't install from tar balls applications that need X11. The all claim that they can't find x11 includes.

I have noticed that ubuntu puts its x11 include in /usr/include/x11 instead of /usr/XR6/includes. How do I go about cheating this. I do not have an Internet connection at home so I cannot use apt-get, so I am stuck with tar balls. Please help (doing windows is not an option).

---

### Post by iaculallad on 2008-07-02
You need the build-essential files in order to install tar balls:

```
sudo apt-get install build-essential
```

---

### Post by motapa on 2008-07-02
Thans iaculallad, but that will not solve my problem. I do not have an internet connection on my machine. I rely on Internet cafes to help me, and I can't subscribe to them. Which is why I am stuck with tar balls.

---

### Post by Partyboi2 on 2008-07-02
build-essential package is on the ubuntu cd, stick the ubuntu cd in the drive and a window should pop up with the option to add it to Package Manager.
[https://help.ubuntu.com/8.04/add-applications/C/offline.html](https://help.ubuntu.com/8.04/add-applications/C/offline.html)

Edit: I would recommend using aptoncd if you do not have a working internet connection, this will allow you to install packages alot easier then having to installing missing dependencies one by one.

---

### Post by erginemr on 2008-07-02
You can also consider downloading the Ubuntu DVD, which packs quite a few packages, from an Internet Cafe.

Synaptic also has a tool to make a list of the selected packages (and their dependencies) into a text file, which you can then use in an Internet cafe to download those in *.deb packages. You can then take all of them with you, put in a folder and issue "sudo dpkg -i *.deb" to install them.

---

