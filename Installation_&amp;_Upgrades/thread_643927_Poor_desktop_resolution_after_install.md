---
title: "Poor desktop resolution after install"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by odindio on 2007-12-18
I have a trident blade 3d video card.  I just installed gutsey gibbon yesterday and I can only get 600x800 resolution for the deskop.  I've run sudo dpkg-reconfigure -phigh xserver-xorg and that did not help.  Have I any options etcept a total reinstall?

---

### Post by brennydoogles on 2007-12-18
> **odindio said:**
> I have a trident blade 3d video card.  I just installed gutsey gibbon yesterday and I can only get 600x800 resolution for the deskop.  I've run sudo dpkg-reconfigure -phigh xserver-xorg and that did not help.  Have I any options etcept a total reinstall?

Did anything pop up asking you if you would like to use a restricted driver?? If so, this should fix your problem. To manually try again, go to System -> Administration -> Restricted Drivers Manager   in your menus, and you should be all set!

---

### Post by odindio on 2007-12-18
I just tried that and I get a message that my system does not need any restricted drivers.

---

### Post by Myglaren on 2007-12-18
Try going to System->Administration->Screens & Graphics and make sure it knows what monitor you are using, worked form me!

---

### Post by odindio on 2007-12-18
my monitor is not listed and i've tried the closest model to that monitor its an hp fl905e

---

