---
title: "Need help installing gnome-ppp"
date: 2004-11-30
forum: Installation &amp; Upgrades
---

### Post by jozmak on 2004-11-30
Hi
I am trying to install  gnome-ppp but the configure command cannot find c compiler. 
But there is a gcc compiler installed. it is in the usr/lib directory.
This is the error I get
root@ubuntu:/home/mak/programs/gnome-ppp-0.3.17 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for intltool >= 0.21... 0.30 found
checking for perl... /usr/bin/perl
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Could anyone suggest what to do?

jozmak

---

### Post by WanderingStar on 2004-11-30
Hello, I did this a few days ago, and my memory might be rusty so if there are errors in my description forgive me please.

That error means you have no compiler.  You need to install from Syanptic GCC, G++, GTK+-dev, and libgnomeui-dev to compile the software.  If your get more errors in the ./configure try searching for the missing thing in synaptic (i.e. error missing libblah - so search for libblah).  Good luck, it does work however.

---

### Post by az on 2004-11-30
Easy way:  Use modem-lights applet.  Click on your panel and add modem lights.

Other way:  Install the package called build-essential.  Then carry on.

---

### Post by jozmak on 2004-11-30
Thanks for both of the advises. Now, I went through the configure and the make run successfully; but when I issue the make install command I get the following message;

make: *** [install-recursive] Error 1

What does this mean?
Who knows.

AZZ, I did what you said. I downloaded the essentials. So what is the procedure of connecting now. Because the reason i want to install gnome-ppp is to have a graphical program to connect to the Internet because now, i use the pon on the command line. 

 I also downloaded gpppon-0.2 but i cannot install that one either. 
With that i get the following error.

make: *** [gpppon.o] Error 1

A bit disappointed because so far i havn't managed installing one single program on Ubuntu. Nothing. Only errors, errors, errors everywhere. 

jozmak

---

