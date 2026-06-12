---
title: "Help with Package Removal for Ubuntu Desktop to Server"
date: 2019-06-22
forum: Installation &amp; Upgrades
---

### Post by alissals96 on 2019-06-22
Hi, so it looks as my machine only let's me install Ubuntu Desktop and not Ubuntu Server by default. I hear people saying they converted Ubuntu Desktop to Ubuntu Server by using a program called Tasksel. Once installing Ubuntu Server, can I wipe all default packages from Ubuntu Desktop so what's left is the shell for Ubuntu Server to start working on?

Thanks

Alissa

---

### Post by dino99 on 2019-06-22
Better and easier to do a fresh server iso installation ):P

---

### Post by TheFu on 2019-06-22
Tasksel is just a metapackage installation program. Basically, it installs 5 services and configures them to work together.  You can run it on desktops too.

There is nothing special about "desktop" or "server" installs.  Just the default programs included.  If the programs you want aren't there, install them. Doesn't matter if they are server or desktop programs.  

I have never used Tasksel.  If I want a group of programs installed, then I'll install those and configure them to work together the way I want.

Removing Ubuntu-Desktop won't do much. It just removes the metapackage that says ubuntu-desktop programs were installed.  If you want to remove all the programs included, that means removing the GUI and ... lots of other desktop-specific packages.  [https://packages.ubuntu.com/disco/ubuntu-desktop](https://packages.ubuntu.com/disco/ubuntu-desktop) has a list.

---

### Post by alissals96 on 2019-06-22
> **TheFu said:**
> Tasksel is just a metapackage installation program. Basically, it installs 5 services and configures them to work together.  You can run it on desktops too.

There is nothing special about "desktop" or "server" installs.  Just the default programs included.  If the programs you want aren't there, install them. Doesn't matter if they are server or desktop programs.  

I have never used Tasksel.  If I want a group of programs installed, then I'll install those and configure them to work together the way I want.

Removing Ubuntu-Desktop won't do much. It just removes the metapackage that says ubuntu-desktop programs were installed.  If you want to remove all the programs included, that means removing the GUI and ... lots of other desktop-specific packages.  [https://packages.ubuntu.com/disco/ubuntu-desktop](https://packages.ubuntu.com/disco/ubuntu-desktop) has a list.

So does this mean that if I remove the GUI, it removes the packages with Ubuntu Desktop if I check uninstall Ubuntu Desktop after installing server?

---

### Post by TheFu on 2019-06-22
No.  It means "ubuntu-desktop" is a metapackage.  If you remove 1 package included in that metapackage, then the "ubuntu-desktop" metapackages is removed, but not all the real packages included inside it.   

Fixating on important things is good.

If you must have exactly "ubuntu server", then use virtualization like the entire world does.
If you don't need exactly the server install, then just install the server packages you need, when you need them.

---

### Post by cruzer001 on 2019-06-22
I have not tried this, but seems others have.

[https://ubuntuforums.org/showthread.php?t=870455&p=9174671#post9174671](https://ubuntuforums.org/showthread.php?t=870455&p=9174671#post9174671)

This may also work:
```
sudo tasksel remove ubuntu-desktop
```
Tasksel also has a test mode the will go through the process without changing anything, using the "-t" switch.
```
sudo tasksel remove ubuntu-desktop -t
```

It would be interesting to find out if this actually works.

Edit
Taskel can be very aggresive at package removal, taking too much at times.  The link above removes the desktop and installs the basic server (console) at the same time.  I think a better route to go.

---

