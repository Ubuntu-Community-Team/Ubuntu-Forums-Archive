---
title: "Need To Design Custom Ubuntu"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by chughes27 on 2012-02-02
So, for a course I'm taking, I am required to set up a new server for my school, at this thread here: [http://ubuntuforums.org/showthread.php?p=11660393#post11660393](http://ubuntuforums.org/showthread.php?p=11660393#post11660393) , please check that out if you are good with servers and could possibly help. 

But, along with this part of the project, I am also going to try and custom build the Ubuntu 11.10 Desktop edition installed on the tower we are using for the server.

Customizations include replacing the boot logo with our school's insignia, things like that.

Help with this would be greatly appreciated!


Thanks!

---

### Post by jerrrys on 2012-02-04
I do not do such things, but I can point you to this:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=customize+boot+grub+splash&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=customize+boot+grub+splash&sa=Search&cof=FORID:9)

Edit:  If you would like a really, really basic desktop to start with you can:

sudo apt-get install lightdm gnome-session-fallback

[http://packages.ubuntu.com/oneiric/lightdm](http://packages.ubuntu.com/oneiric/lightdm)

[http://packages.ubuntu.com/precise/gnome-session-fallback](http://packages.ubuntu.com/precise/gnome-session-fallback)

---

### Post by Bucky Ball on 2012-02-04
For the insignia you could try Grub Customizer. I think it is in the repositories now but if not add the ppa here:

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

Run it and 'Edit Grub Preferences', hit the 'Appearance' tab and you can add a custom image ... 

Good luck with it. ;)

---

### Post by chughes27 on 2012-02-05
thanks guys! I'll try that out!

---

