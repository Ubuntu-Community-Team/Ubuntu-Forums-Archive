---
title: "How to Uninstall Gnome from Xubuntu"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by FoggyMtn on 2006-06-11
HEy Ya'll

Well, I've done it now....   I have been running xubuntu happily for a week or two now.  Tonight I apt-get installed gnome-desktop to see what I was missing.  Well, I don''t want to keep all that extra stuff.  I tried apt-get remove Gnome-desktop.  Of course, I find out now that doesn't take everything back out.

How do I remove Gnome and leave xubuntu intact?

Thanks 

(ps I found the links on removing KDE from Gnome, but not gnome from xubuntu)

rob

---

### Post by glotz on 2006-06-11
See [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Note, as stated in the article, it's a good idea to use aptitude to install stuff you might want to uninstall later...

---

### Post by FoggyMtn on 2006-06-11
Thank you!  That's just what I needed.   You can probably smell my 300 mhz pent II smoking from all the install, remove-ing going on!! LOL

My 6 gig hard drive thanks you too! (not to mention the meager 128 ram!!)

Thanks again, and lesson learned.  Next time will be aptitude!!!!

Rob

---

### Post by glotz on 2006-06-11
Hehe, you're welcome! Since you're on a small disk, you might want to remove your package manager cache (sudo apt-get clean) and maybe uninstall any old kernels you're not using. The default install comes with hundreds of megs of fonts like 5 different chinese variations for example... Don't know about you but I got rid of those ASAP... :) Also, you might get a tiny weeny boost from installing the i686 kernel instead of the default i386 kernel. See [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by FoggyMtn on 2006-06-11
[QUOTE=glotz]Hehe, you're welcome! Since you're on a small disk, you might want to remove your package manager cache (sudo apt-get clean) and maybe uninstall any old kernels you're not using. The default install comes with hundreds of megs of fonts like 5 different chinese variations for example... Don't know about you but I got rid of those ASAP... :) Also, you might get a tiny weeny boost from installing the i686 kernel instead of the default i386 kernel. See [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)[/QUOTE]


Thanks!  I;ll run the apt-get clean when it gets done removing all this.

How do I remove the fonts and old kernels?

Thanks for the 686 link, I'll study up on it tonight

Rob

---

### Post by glotz on 2006-06-11
It's easiest to open Synaptic and select it to display packages by status (lower left corner) and selecting installed packages. There you see their names and short and long description of what they do. (Note that some packages have very very strange dependencies and generally those should be left alone. I think that's where you'll find your kernels too.)

---

### Post by FoggyMtn on 2006-06-11
Thanks!  That got it!!  

Have a great week
rob

---

