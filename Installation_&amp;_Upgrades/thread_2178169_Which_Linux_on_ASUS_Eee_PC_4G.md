---
title: "Which Linux on ASUS Eee PC 4G?"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by giobaxx on 2013-10-02
Good morning guys


A friend of mine gave me an old netbook  asking to reinstall an operating system for it . It 's an old ASUS Eee PC 4G. It has a 4 disk Giga, and a 512 Mb ram.
If has the original system, which should be a linux based.
You might recommend a lightweight version of linux? ... Lubuntu you think would be good?

tanks

---

### Post by Lars Noodén on 2013-10-02
Lubuntu would be the lightest pre-packaged distro.  What you might do is take the Alternate disc image and press F4 for "Install a command-line system" and then install just the pieces you will actually use.  Unless you install a lot of extra packages, everything should fit nicely within 4G.  But you'll probably want to keep data on removable USB devices to save space.

However, the biggest RAM and CPU hog will be the GUI.  I would recommend using plain Openbox or else FVWM-crystal inistead of LXDE.  For most things you really don't need a full Desktop Environment and can get by quite nicely with just a Window Manager.   If I recall correctly Oroborus is the smallest WM.

---

### Post by giobaxx on 2013-10-02
I think my friends will use this netbook only for internet....

---

### Post by Lars Noodén on 2013-10-02
If by Internet you mean WWW, then all you need is a Window Manager with Firefox and any helper applications it might need.  That should fit in way under 4GB.  

One thing that might be nice to have would be to fix up the computer with a little more RAM.  It's not necessary, but can help performance and is easy to add through the panel on the bottom of the machine.

---

### Post by ajgreeny on 2013-10-02
If it is really just for the internet you could use an installed puppy-linux system which takes only a few hundred MB of disk space, looks good and is fast.

Worth a try?

---

### Post by coldraven on 2013-10-02
I installed the normal version of Xubuntu 12.04 on an eeePC 900 and it filled the 4GB drive completely.
This PC has an extra 16GB drive so now I have to move /tmp to it.It does work and wifi worked straight away.

---

### Post by Lars Noodén on 2013-10-02
A plain-vanilla install of Lubuntu takes 1.9GB on the HD.  Going with a pared down installation will take even less.  Here it's probably more important to spare on RAM, which using a Window Manager by itself will do.  A heavy Desktop Environment like XFCE isn't really needed to just run Firefox, nor even a lighter one like LXDE.  However, the 1GB RAM on the Eee is enough for most web surfing scenarios.

---

### Post by mörgæs on 2013-10-02
A fast and easy option is [Lubuntu Core]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"), after which Chromium / Firefox and other webstuff is added. 

Remember to run 

```
sudo apt-get clean
sudo apt-get autoremove
```

once in a while to keep the small disk uncluttered. 

Adding Flashblock to the browser helps a lot on the speed.

---

