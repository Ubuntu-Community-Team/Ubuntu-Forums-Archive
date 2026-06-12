---
title: "Lost"
date: 2004-10-30
forum: Installation &amp; Upgrades
---

### Post by Branchsr on 2004-10-30
Good morning,

I am new to the use of linux on a hard drive, I need help. In an earlier post "Lost Display" I said the display failed just before going to the gui, just as I should be signing in. 

Well, I'm guessing from the amount of replys that wasn't the right way to phrase the problem. I'm using the ATI 8500DV video card, I've read the ATI install data for the fglrx but I'm still lost. How do I get to the location where I can load this? Is there a place I can go to read up on how to do this?

Thanks,

Dan

---

### Post by im_ka on 2004-10-30
i cant help you with ati, but google.com/linux is always a good place to go ;)

---

### Post by im_ka on 2004-11-04
see [this](http://www.ubuntulinux.org/wiki/BinaryDriverHowto/view?searchterm=nvidia) document.

after installing the the needed packages from universe (see [this](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto/view?searchterm=universe) document about adding repositories), you need to
```
sudo dpkg-reconfigure xserver-xfree86
```
to configure the x server ("graphical base" of linux).
change "ati" to "fglrx" when you come to that point.
you can set other things when configuring x (screen resolution, mouse settings, etc.), play around with it, but before you do that, make a backup copy of /etc/X11/XF86Config-4 in case you screw up something and can restore it.
```
sudo cp /etc/X11/XF86Config-4 /home/dan(or whatever it is)/
```
you can edit the file by hand doing
```
sudo gedit /etc/X11/XF86Config-4
```
if you don´t feel comfortable typing commands to manipulate files, install midnight commander (norton commander like app)
```
sudo apt-get install mc
```
(it´s in universe as well)
and run it with
```
sudo mc
```
to get root privileges (read: have write acces everywhere)
you´ll see that mc has a built in file editor as well, you can view (f3) and edit (f4) files as you browse.

hope this helps. tell us how things go ;)

---

