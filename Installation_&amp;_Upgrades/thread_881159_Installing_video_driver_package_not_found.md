---
title: "Installing video driver: package not found"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by Psychicfriend on 2008-08-05
Hello,

I'm very new to Linux. I've had Ubuntu Studio 8.04 on my computer for a few days now and am unable to install a proper video driver to make my Intel 845GV work. I know it's old but this computer was free so I'm using it to play with Ubuntu until I get the hang of it then I'll install it on my other computers. Anyway I found a driver that is supposed to handle my Intel chip at Xorg. I downloaded it and then followed instructions and got message: E: Couldn't find package IntelGlx. I even tried other instructions I got from the Ubuntu Hacks book on how to install drivers and every-which-way I try I keep getting the same message. I've even tried to target the files inside to install.

$ ./autogen   (I get: No such file directory)
$ make
$ sudo -c "make install"

This is what xorg says to do to install it.
 
Please help my graphics look awful (blurry) on my LCD!

Thank you

---

### Post by spiderbatdad on 2008-08-05
a link to the instructions you are trying to follow might help.

Also check that you have autogen...from synaptic package manager. You should have build-essential also to compile packages...installing build-essential should install autogen for you.

---

### Post by tuxxy on 2008-08-05
is there one to enable in the hardware drivers?

---

### Post by Psychicfriend on 2008-08-05
Here is a link to the site and directions for the drivers which I downloaded.

[http://www.intellinuxgraphics.org/install.html](http://www.intellinuxgraphics.org/install.html)

Well I don't know how to make it a link yet on Linux but that's where I got it.  And I do have <autogen> installed.

Oh, it is a link.

---

### Post by spiderbatdad on 2008-08-05
This is an ambitious undertaking for a new user, to be sure. Building a driver into the kernel is not so easy. There are some other xserver-intel drivers in synaptic.

If you want to try...it looks like the problem is with not finding "IntelGlx" This may be due to rendering tool used by the existing driver...sorry not sure. You might want to look into the 915 resolution.

This maybe much easier, and may work for you. [http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/)

The nice thing about installing via deb is the ease with which the package can be removed.

---

### Post by Psychicfriend on 2008-08-05
spiderbatdad, 

I tried the 915resolution driver and it made my computer unable to shutdown without a hard shutdown and the resart function doesn't work with that driver either. 

I really like the Ubuntu Studio and all the cool features so i'm motivated to get the graphics working properly on my system. I'm commited to learning Linux.
I love the whole idea behind Gnu and Linux. I won't miss Windows.  

Thanks anyway. I'll check-out the link you sent.

---

### Post by Psychicfriend on 2008-08-05
Oh, one more question.  When installing from Synaptic is the software automatically and completely installed and available to use without further any actions?

---

### Post by spiderbatdad on 2008-08-05
generally changes to configuration files like xorg would require you to reboot or restart the app, or log out and back in ctrl+alt-bckspc.

If you want to reconfigure xserver to kernel defaults, you can use the command:```
sudo dpkg-reconfigure xserver-xorg
```and answer all the questions. Or
```
sudo dpkg-reconfigure -phigh xserver-xorg
```to only be asked high priority questions. Then reboot.

But programs installed via synaptic are basically ready to run.

---

