---
title: "Trouble Installing Packages (be nice to a newbie)"
date: 2005-09-19
forum: Installation &amp; Upgrades
---

### Post by schuttup on 2005-09-19
My linux computer doesn't have an internet connection, so I downloaded some new packages on another computer and transfered them using my thumb drive to the linux machine, but I can't figure out how to install them since I didn't download them with the APT. ](*,)   Can someone help me out?

---

### Post by Xian on 2005-09-19
If they are ubuntu packages (as they should be) then just place the packages in your /home/username/ directory and install them with the command below issued in a terminal:

```
$ sudo dpkg -i *.deb
```

---

### Post by schuttup on 2005-09-19
thank you so much.  I'm new to linux and I somtimes feel totally incompetent.  These forums save my life.

---

### Post by Haltcrypto on 2005-09-19
Don't worry I also just installed Ubuntu for the first time this weekend (using a virtual machine) and don't know how to install. It just seems a bit harder than i'm used to.

Do the packages HAVE to be Ubuntu packages?

---

### Post by Xian on 2005-09-19
They don't have to be Ubuntu packages for the install method to work (any .deb file will substitute) but it is always advisable to stay within the Ubuntu library, which would include backports, since not all debian based packages will transfer well to the Ubuntu environment. The idea here is to maintain the stability of your system.

---

### Post by Haltcrypto on 2005-09-19
So is there a library where it lists many Ubuntu packages for all purposes, such as maths and stats packages?

I will also be dowloading packages seperatly for later installation.

---

### Post by bsussman on 2005-09-19
[QUOTE=Haltcrypto]So is there a library where it lists many Ubuntu packages for all purposes, such as maths and stats packages?

I will also be dowloading packages seperatly for later installation.[/QUOTE]

You can browse the different package sections in Synaptic or other GUI frontend to apt.

If you can access the net from a machine that runs apt or an apt front end, like Synaptic or Kynaptic, you can get all the dependencies - they have a download only choice. then you could be sure that they will work when you get to your own machine. I fear you are going to be frustrated by dependencies otherwise.

Of course, the machine you are running apt on may make this frustrating anyway. However, Synaptic will tell you the dependencies for a package.

In Linux there is much more modularization - making a dependency manager/downloader important.

---

### Post by aysiu on 2005-09-19
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

