---
title: "Install blues"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by neenaoffline on 2006-03-27
I tried installing ubuntu the installer just gets stuck inbetween the process
I have:
       PIII - 450Mhz -OC'ed to 500 Mhz (katmai)](*,) 
       62 MB RAM (SD)](*,) 
       and some motherboard](*,) 

can i keep my existing windows installation along with ubuntu.:-? 
can someone help me with the installation process (i just don't understand it):-? 
I've used [www.damnsmalllinux.org](www.damnsmalllinux.org) (DSL) before just for records:KS

---

### Post by Bartender on 2006-03-27
Hi, neena -
Have you taken a good look at the hermanzone site?

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

He's got great instructions for dual-booting.  I used the "Ubuntu +NTFS" guide.  If you can, set your PC up next to another one that's connected to the web so you can follow the instructions.

I don't know what you mean by stuck in the process.  64MB of RAM is really borderline.  I don't know if insufficient RAM will trip up an install or not, but if you can scrounge up some compatible RAM that would be really good.  At least 256.

Are you using a stamped CD or did you download and burn a disc?  Stamped ones can be flawed but downloaded/burned CD's are more liable to cause problems unless you verified the download, used hi-quality media, burned at a slow speed (1X or 2X), etc.

People are often willing to help if you can give specific feedback on where your installation hangs up.

---

### Post by Sef on 2006-03-27
>  PIII - 450Mhz -OC'ed to 500 Mhz (katmai)
62 MB RAM (SD)
and some motherboard

With your system, I would do a server install.  At the prompt, type in server then hit enter.  

For a window manager, I would download a light weight one, e.g. xubuntu, fluxbox, icewm, etc.

Once the install is done, you will be at a prompt:

sudo apt-get update

sudo apt-get install (window manager)-desktop

---

### Post by neenaoffline on 2006-03-29
[FONT="Tahoma"][COLOR="Magenta"]Thanks for the link bartender.:D 
By the way does ubuntu work fast with X on your comp , coz if it does i'll just get 256 Meg's of RAM:-k .The installation *_[COLOR="Red"]had gotten[/COLOR]_* stuck while installing the kernel or while detecting the network settings for setting up apt.Yeah :-D  , that's rightubuntu got installed.I love X.I just needed some patience all these months.](*,) [/COLOR][/FONT]

---

