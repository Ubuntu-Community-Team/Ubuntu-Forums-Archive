---
title: "GUI broken"
date: 2009-01-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-01-17
Hi

I appear to have broken some component of my GUI (xserver or GDM?)

This is what happened:

I have a setup with Intrepid and windows on the hard drive and jaunty on a USB drive. I installed xubuntu-desktop on the USB drive to play with. It worked fine for a couple of sessions but now when I  select from Grub the 'Jaunty on USB' install the following happens:

I get the graphical display of the ubuntu logo with a growing orange line, then, on a black screen
Loading
1940 records in
1940 records out
kinit: name_to_dev_t(/dev/disk/by_uuid/xxxxxxxxxxxxxx):dev(8,4)
kinit: trying to resume from /dev/disk/by_uuid/xxxxxxxxxxxxxx
kiniy: no resume image, doing normal boot

uubuntu jaunty (development branch) nameofdrive tty1

and then the login prompt.

I can login to the command line. 

GDM is obviously running as sudo etc/init.d/gdm stop succeeds

I then tried sudo dpkg-reconfigure xserver-xorg and got a message that xserver-xorg was not installed or broken, so I tried

sudo apt-get install xserver-xorg

this installed 37 packages  and removed one (nvidia-glx-96 I think)


however sudo dpkg-reconfigure xserver-xorg again returned a message that xserver-xorg was not installed or broken, 

So in a nutshell: I cannot boot into, or get into a GUI session on my USB drive.
(I have tried booting from an alternate CD but unfortunately I get a repeating message about an I/0 error on a block on some drive, but that is another issue I am sure)

Can anyone help please?

---

### Post by dinxter on 2009-01-17
the nvidia 96 driver and xorg in the repositories are incompatible at the moment. installing one will uninstall the other. search for nvidia in this forum for a number of threads on this. i dont use 96 so i cant say for certain but you should

1. make sure xorg is installed
"sudo apt-get install xorg"
2. then either, 
switch to the open driver by changing the driver in /etc/X11/xorg.conf to nv from nvidia
or maybe try installing the driver manually from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). perhaps adding the ignoreabi option to xorg.conf, again, look for the other threads for more details from other 96 driver users

---

### Post by gspat on 2009-01-17
I had the same issue yesterday, let me get my head on straight and I'll tell you what I did to get it back... Once I remember it all... (need coffee!)

Strange thing though.. it installed the 96 driver, even though I can't use it (7600gs)

.:Edit

OK.. 

What you need to do is uninstall the 96 driver so that you can re-install xserver-xorg.

In my case it wasn't quite so cut and dried, because the 96 driver had set a diversion to libGL.so that it couldn't find. This made it impossible to remove with apt-get remove nvidia-glx-96 giving up with a error 1 from dpkg.

The solution was in two parts... 

First, I had to go into the installer shell script itself and remove the "set -e" from every shell script in /var/lib/dpkg/info/ that matched nvidia-glx-96.* (If you don't see "set -e" you will see "#!/bin/sh -e", if so change it to "#!/bin/sh"). This allowed me to uninstall the nvidia-glx-96 driver.

Then there was the diversion that had to be removed to the libGL.so file 

use sudo dpkg-divert --rename --remove /usr/X11R6/lib/libGL.so.1 (or change the filename to what is required). This will get rid of the check for the file.

Then do a "sudo apt-get -f install" and you should be able to install xserver-xorg with no problems, and dpkg-reconfigure xserver-xorg" will work.

Hope this was helpful!

P.S. A bit of coffee first thing in the morning is a wonderful thing! :P

---

### Post by ubername on 2009-01-17
Thanks all for the help. I have settled for the 'complete re-install' route seeing as the Jaunty alpha 3 is available and am busy rebuilding!

---

