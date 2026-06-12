---
title: "Is there any way to install multiple version of gtk on Ubuntu?"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by Ravi Gadhia on 2011-11-18
Hello all
      I recently upgrade to Ubuntu 11.10.

Ubuntu 11.10 come with gtk(2, 24, 6). 
Now I want to test one of my program with gtk (2,16,1) 
So how can I install gtk(2,16,1) and compile my pygtk program

when I try to install gtk(2,16,1) using
gtk+-2.16.1$ ./configure --prefix ~/Home/opt/gtk2.16

it's gave following error:

checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.19.7    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

Is there any way to install multiple version of gtk on Ubuntu

Thanks in advance
Help really appreciated
RGA

---

### Post by durand on 2011-11-19
Why do you need an old version of gtk? You might need that if you compiled a statically linked app but python doesn't care. Your pygtk app should work with a newer version of gtk as long as it isn't using outdated functions. What error do you get when you run it?

---

### Post by Ravi Gadhia on 2011-11-19
> **durand said:**
> Why do you need an old version of gtk? You might need that if you compiled a statically linked app but python doesn't care. Your pygtk app should work with a newer version of gtk as long as it isn't using outdated functions. What error do you get when you run it?

thanks for reply
actually i want to test this bug.
[https://bugs.launchpad.net/openobject-client/+bug/885098](https://bugs.launchpad.net/openobject-client/+bug/885098) 

it's required to start OpenERP gtk client with gtk2.16.1 it's work fine with gtkX.X.X > gtk2.16.1

Thanks 
RGA

---

### Post by durand on 2011-11-19
Right so it looks like the add_objects_from_file function was added in 2.14 according to the pygtk docs but your bug reporter is running 2.16 so it should work correctly. Maybe he has older python bindings somehow? You could test it by using this guide to compile the right version of gtk in a local folder. [http://ubuntuforums.org/showthread.php?t=1149198](http://ubuntuforums.org/showthread.php?t=1149198)  The problem is that you will need to compile the correct versions of all the relevant libraries as well and link them correctly. Then, you need to install the python bindings for the correct version. They might come with gtk but I'm not sure. I think it would be much easier to just find which ubuntu came with that version of gtk, download its live cd and test it off that. Or use a virtual machine like virtual box.

EDIT: I've requested for it to be moved to the Packaging and Compiling sub form, you might get more help there.

---

