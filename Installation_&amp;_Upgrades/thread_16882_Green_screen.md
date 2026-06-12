---
title: "Green screen"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by kjmorris on 2005-02-24
I just installed Ubuntu Linux 4.1 from the install cd to my laptop. The
laptop is a Dell Inspiron 1150 with Celeron 2.8 Ghz and a 20 GB HDD. I
installed Partition Magic 8 on Win XP HE SP2 and created a 500 MB Linux
Swap partition and about 5.5 GB of free space. I installed Ubuntu in the
free space and the installation seemed to go fine. However, when I
choose Ubuntu at the Grub screen, it takes about a minute or so to scroll 
through the startup process (during which I noticed a couple of "Errors" 
mentioning "Hotplug" but haven't been quick enough to get the exact 
text just yet). Then it takes me to a lime green screen and stops. 

It does not respond to anything from this point on - not
Ctrl-Alt-Del or Ctrl-Alt-Backspace or whatever. After a cold reboot, 
I can choose recovery at the Grub screen and get to a command line 
but I don't know what to do once I'm there. 

I'd appreciate any guidance. TIA

kjmorris

---

### Post by alastair on 2005-02-24
If you can boot into a text mode shell, login.

Then you could have a look at the log files e.g. :

/var/log/syslog

and see if you can see the errors in there.

For the graphical startup (GDM perhaps), look in :

/var/log/gdm/

For X itself, look in :

/var/log/Xorg.0.log

---

### Post by kjmorris on 2005-02-28
I was able to get to a CLI and ran

sudo dpkg-reconfigure xserver-xfree86

Then, I set the display to vesa and the color depth to 16 (from 24) and that did the trick.

kjmorris

---

