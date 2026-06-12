---
title: "Feisty Install w/o Internet Connection"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by woody22075 on 2007-09-26
Im new to linux and am trying to  install Feisty on my laptop (HP 6715b).  I have got it installed but my video card (ati x1250) isnt supported by default.  i can get the drivers from ati's website but when i try to install them im notified that i need xorg-driver-fglrx in order to install.  

The problem is that i dont have an internet connection for the laptop (long story).  how can i download (from another pc) xorg so i can transfer it to the laptop for installation?

Thats alot for the help!

---

### Post by pxwpxw on 2007-09-26
download the single package via other pc to a usb stick -> laptop -> install the single package (if this is the package you need)
  
[http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx](http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx)

---

### Post by woody22075 on 2007-09-26
pxwpxw,

Thanks alot for the response!  One more new question, how do i initiate the install from the terminal (what commands do i use)?

Thanks again!

---

### Post by reckless2k2 on 2007-09-26
```
sudo dpkg -i <the packagename>
```

if you are installing a bunch that have dependencies, put the all in 1 folder and navigate to the folder then install all at the same time

```
cd /home/yourusername/thefolder
```

then

```
sudo dpkg -i *.deb
```

---

### Post by woody22075 on 2007-09-28
i looked at the url referenced and there were a lot of dependencies required for xorg (i know that i am missing at least a couple).  Is there an easy way to download all the required dependencies at once?  or is it nec to download them one by one?

Thanks again for the help!

---

### Post by pxwpxw on 2007-09-28
maybe if you try to use synaptic to install it, might pickup the dependencies.

---

### Post by woody22075 on 2007-09-28
unfort i cant use synaptic--i dont have a direct internet connection for the laptop.  any suggestions?

---

