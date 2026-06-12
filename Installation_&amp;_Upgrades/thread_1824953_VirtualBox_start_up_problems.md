---
title: "VirtualBox start up problems"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by toolmania1 on 2011-08-14
Hello,

I have tried a few methods of setting up Virtual Box in Ubuntu 11 and have not had much luck.  I set up a new machine, but when I try to start it, it will not start.  I get an error:

Failed to open a session for virtual machine Windows XP.

The virtual machine 'Windows XP' has terminated unexpectedly during startup with error code 1.

The second pop up reads:

RTR3Init failed with rc=-1912 ( rc=-1912 )
Please install the virtual-ose-dkms package and execute 'modprobe vboxdrv' as root

------

I have tried to run sudo modprobe vboxdrv under root.  I think it worked since I saw no error.

I also have found other sites say that I should install directly from the Oracle web site which I did.

I also have opened Ubuntu software center and selected to comletely remove all virtual box items in the list.  Then, I user Ubuntu software center to install all of the virtual box items.

Another time, I tried using the synaptic to install.
apt-get install virtualbox-ose

No matter which method I had tried, I got that same error above.

I even found one more site in which I was to add the user to the group for vbox and this did not help.

sudo adduser [your username] vboxusers

---

### Post by Old_Grey_Wolf on 2011-08-14
Have you checked the version of VirtualBox you are using to determine if it supports Ubuntu 11.04? I think you have to use VirtualBox 4.1.0 with Ubuntu 11.04, and you have to download it from Oracle's website.

---

### Post by toolmania1 on 2011-08-14
Thanks for the reply.  I actually was able to get Virtual Box installed and running.  I had to use synaptic to do it.  ( Even though I tried this earlier in a different way and it did not work. )

[http://seogadget.co.uk/how-to-install-virtualbox/](http://seogadget.co.uk/how-to-install-virtualbox/)

---

