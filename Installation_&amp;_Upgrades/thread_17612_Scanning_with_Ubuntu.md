---
title: "Scanning with Ubuntu"
date: 2005-03-01
forum: Installation &amp; Upgrades
---

### Post by Jet2k5 on 2005-03-01
Ok hello guys, 

I sorta started using Ubuntu because I want to use a Linux Distro that works, and Ubuntu that fulfilled that to the max.

Now I'm having some problems with my All-in-one hp pcs1310 printer.  When I try to open up Xsane it says that no devices were found.  I have gotten the scanner working with Mandrake and Arch Linux, it's just that I completely forgot, what files and all to modify.  I know for a FACT that my scanner is compatible with SANE, so that option is out of the picture.

Any Ideas?

-Luis

btw, congrats on Ubuntu to all you developers, it's a job great done.  Seriously :!:

---

### Post by m4ng0 on 2005-03-01
Try to unplug/replug your usb cable before launching xsane. If this work search the forum for "usb scanner permission" and you can find some solutions.

---

### Post by polemicz on 2005-03-01
do sudo xsane. If that works you have to change permissions in /proc for your scanner. Check posts.

---

### Post by Jet2k5 on 2005-03-01
Ok thanks for the help guys.

What I did to fix this problem was go to Linuxprinting.org , typed in my printer name, and surprisingly I found a post from a guy that had just used the printer with Ubuntu.  What he mentioned is that everything works ( scanning & printing ) if you have both hpoj and hpij loaded.

So I already had hpij, according to apt-get, so what I did was,

```
sudo apt-get install hpoj
``` 

and installed hpoj, what that did is run this little set up program, and kaboom!  Ran xsane again and everything worked right out of the box!

So thanks again to this guy who wrote that valuable piece of information, and I recommend getting this package if you have a similiar hp printer.

---

