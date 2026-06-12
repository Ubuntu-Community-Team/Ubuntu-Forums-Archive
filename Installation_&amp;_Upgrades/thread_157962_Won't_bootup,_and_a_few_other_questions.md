---
title: "Won't bootup, and a few other questions"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by vitaminz on 2006-04-10
Hi, I recently installed Ubuntu Linux using InstLux 
( [http://www.sourceforge.net/projects/instlux](http://www.sourceforge.net/projects/instlux) ) as for some it wouldn't boot from CD. The install went perfectly fine, up until it said the first stages of the install was complete. 

A few screens after that it says something about downloading 800 or so files. After that it says it's installing, and says some components couldn't be installed, and I should correct these when I boot into Ubuntu.

After that a command line comes up asking me to login. I login with my username and password, but Ubuntu doesn't boot :-k I'm not too good with command line interfaces so I wasn't really sure what to do.




And if these issued can't be resolved...Is it possible to uninstall Ubuntu without the Windows XP CD? Or if that's not possible, is there a way to make Windows XP my default operating system? Because at the moment it's Ubuntu.

Many thanks

---

### Post by ledonnell on 2006-04-10
Have you tried:
sudo apt-get upgrade

?

[QUOTE=vitaminz]Hi, I recently installed Ubuntu Linux using InstLux 
( [http://www.sourceforge.net/projects/instlux](http://www.sourceforge.net/projects/instlux) ) as for some it wouldn't boot from CD. The install went perfectly fine, up until it said the first stages of the install was complete. 

A few screens after that it says something about downloading 800 or so files. After that it says it's installing, and says some components couldn't be installed, and I should correct these when I boot into Ubuntu.

After that a command line comes up asking me to login. I login with my username and password, but Ubuntu doesn't boot :-k I'm not too good with command line interfaces so I wasn't really sure what to do.




And if these issued can't be resolved...Is it possible to uninstall Ubuntu without the Windows XP CD? Or if that's not possible, is there a way to make Windows XP my default operating system? Because at the moment it's Ubuntu.

Many thanks[/QUOTE]

---

### Post by vitaminz on 2006-04-10
[QUOTE=ledonnell]Have you tried:
sudo apt-get upgrade

?[/QUOTE]

Hmm no,  I just tried typing it into the command line and I got something like this:

E: dpkg was interupted

It asked me to type in another command about dpkg configuration, so I did and it said I had to have the right priveleges (Or something about that, sorry I have a bad memory :-|)

Thanks

---

### Post by vitaminz on 2006-04-10
Sorry if this is too soon to bump the topic. Can anyone help? I really want to get to grips with Ubuntu.

---

### Post by vitaminz on 2006-04-13
Please? Someone? :(

---

### Post by Sef on 2006-04-13
try this:  sudo apt-get -f install  

It installs dependencies that are missing.  If it doesn't work once, try it a few times.

---

### Post by vitaminz on 2006-04-14
Thanks for the reply. It still says something about E: dpkg being interupted :( Here is exactly what happens

I type in sudo apt-get -f install

It says "D: dpkg was interupted, you must manusally run 'dpkg --configure -a' to correct the problem"

So I type in dpkg --configure -a

Then it says "dpkg: requested operation requires supervisor privileges.



Also...I just noticed my Ubuntu partition has only 7.51MB of data on it :| That can't be the entire of Ubuntu, right?

---

