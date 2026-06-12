---
title: "Missing libraries in 18.10: programs won't start"
date: 2018-10-25
forum: Installation &amp; Upgrades
---

### Post by raif on 2018-10-25
After a fresh install of Ubuntu 18.10 I'm finding that multiple programs I use just won't start. Trying to start them from the command line reveals that various libraries are missing, e.g.:

```
$ megasync
megasync: error while loading shared libraries: libQt5Svg.so.5: cannot open shared object file: No such file or directory
$ gimp
gimp: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

I've looked up the libraries and found one belongs in this package 
[https://packages.ubuntu.com/search?suite=cosmic&arch=any&mode=exactfilename&searchon=contents&keywords=libgtk-x11-2.0.so.0]("https://packages.ubuntu.com/search?suite=cosmic&arch=any&mode=exactfilename&searchon=contents&keywords=libgtk-x11-2.0.so.0")

But seems it's already installed.

```
$ sudo apt install libgtk2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-0 is already the newest version (2.24.32-3ubuntu1).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

I then found this post about missing libraries in 18.04, suggesting reinstalling them

[https://askubuntu.com/questions/1029206/ubuntu-18-04-lts-libqt5xml-so-5-cannot-open-shared-object-file]("https://askubuntu.com/questions/1029206/ubuntu-18-04-lts-libqt5xml-so-5-cannot-open-shared-object-file")

```
~$ sudo apt install --reinstall libgtk2.0-0

```

and have reinstalled libqt5xml5, libqt5svg5 and libgtk2.0-0. This has solved the issue with gimp but not with megasync, well I get a new message saying I'm missing the following but I can't seem to find this to install
```
$ megasync
megasync: error while loading shared libraries: libQt5Widgets.so.5: cannot open shared object file: No such file or directory

```

any ideas? and assuming this is a bug where should it be reported? many thanks in advance

---

### Post by dino99 on 2018-10-25
Which version are you using ? installed from ?

[https://mega.co.nz/linux/MEGAsync/xUbuntu_17.10/](https://mega.co.nz/linux/MEGAsync/xUbuntu_17.10/)

As you can see that program has not been updated for recent ubuntu version.

---

### Post by raif on 2018-10-25
Good spot dino99, though I chose the 18.10 option on mega.nz, it's actually just the 17,10 version as you point out. Though didn't have any problems using it with 18.04. Have flagged this to Mega.

But there still seems to be the broader issue with 18.10 that some core programs like Gimp don't work without reinstalling libraries. I've been using Ubuntu for over a decade and never had this problem before when upgrading to a new version. Is it just me or are others affected?

---

### Post by raif on 2018-10-30
So after reinstalling a lot more libraries, everything is working, whether programs installed from universe or .deb files. 

sudo apt install --reinstall libxcb1 libxcb-xinerama0 

Can anyone explain what went wrong here and if I need to file a bug somewhere?
thanks

---

### Post by dino99 on 2018-10-30
Do the syncing ubuntu tools not able to satisfy your needs ?  (rsync, clsync, ...)

You might glance at 'journalctl -b -1' (or -2/3/4...) to find errors about your previous trouble.

---

