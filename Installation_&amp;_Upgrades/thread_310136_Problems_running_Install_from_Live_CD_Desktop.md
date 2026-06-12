---
title: "Problems running Install from Live CD Desktop"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by redwax on 2006-11-30
Hi

I have just downloaded the Ubuntu 6.10 iso and burned it, booted into the PE/Live environment (which is where I am typing this from!!) and that's all fine.  The only snag is, when i run the 'install' from the desktop, nothing happens. I right clicked the icon and checked out the command, which is shown as "gksudo --desktop %k ubiquity gtkui".  I thought I'd copy this into a terminal to see if there was anything more exciting it was going to tell me about why nothing was happening.  this is what happens:

ubuntu@ubuntu:~$ gksudo --desktop %k ubiquity gtkui
/usr/bin/ubiquity: 15: 
Installer

This is a installer program for a Ubuntu or Metadistros Live system.
This is the main program, but there are also a couple of libraries to
help it to work, such as the frontend.
The way it works is simple. It detects the frontend to use, then
load the module for that frontend. After that, it makes some calls
through the frontend in order to get the info necessary to install.

Once it has the info, partitioning, format, copy the distro to the disk
and configure everything.
: File name too long
/usr/bin/ubiquity: 17: import: not found
/usr/bin/ubiquity: 18: import: not found
/usr/bin/ubiquity: 19: import: not found
/usr/bin/ubiquity: 20: import: not found
/usr/bin/ubiquity: 21: import: not found
/usr/bin/ubiquity: 22: import: not found
/usr/bin/ubiquity: 24: Syntax error: word unexpected (expecting ")")
ubuntu@ubuntu:~$ 

Anyone got any Ideas?  I'm keen to get this sorted as I deleted my Fedora Core installation to give this a whirl in an attempt to boycott M$, seeing as their latest effort (Fista) is such an abortion.

Cheers

---

### Post by taurus on 2006-11-30
You double-click the install icon and nothing happens!  If you want to install Edgy on your machine, perhaps the alternate CD is what you want...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by redwax on 2006-11-30
Can I do this using the OEM install option on the Alternate CD then?

This said, I am interested to know why it would fail from the Live desktop, doesn't make any sense.

Thank you

---

### Post by taurus on 2006-11-30
You can use the oem option (second option) from the alternate CD but why not pick the first option, installing it!!!  Then, you don't have to run an extra command to create a username and password after you log in as an oem user first!!!  

What's the spec of your machine then?

---

### Post by redwax on 2006-11-30
Athlon XP 2600, NFORCE2 Chipset, 1GB DDR 400 (Dual Channel), 128MB NVIDIA 5200 Video Card, 40GIG IDE Drive, nowt special but plenty powerful enough for most OS's

Do you mean the Text setup (option 1)?  Is it not really hectic?  I have a little Linux experience as have been dual booting XP and Fedora Core for a while but not a demon by any means (obviously)

---

### Post by taurus on 2006-11-30
Yip, the text mode...

Your computer should smoke (run) good with Ubuntu...  ;)

Also, don't forget to burn the ISO image at a slower speed like 4x.

---

### Post by redwax on 2006-11-30
I'll give it a whirl tomorrow then.  Cheers

---

