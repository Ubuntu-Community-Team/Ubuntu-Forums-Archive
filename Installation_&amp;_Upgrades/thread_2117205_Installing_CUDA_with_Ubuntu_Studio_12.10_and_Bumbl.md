---
title: "Installing CUDA with Ubuntu Studio 12.10 and Bumblebee?"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by jonathanfv on 2013-02-17
Hi! So, I'd have a few questions about installing CUDA without messing up everything on my computer. I tried reading NVIDIA's documentation, but I'm unsure of certain things, partly because I'm not a native English speaker. If someone could help me shed some light on the process, I would be very thankful.

I'm using a Thinkpad W530 with a Quadro K1000M as my graphics card. On it, I've installed Ubuntu Studio 12.10 with Bumblebee and the NVIDIA proprietary driver version 304.47 from the x-swat repository.

I've downloaded CUDA 5 for Ubuntu 11.10 (there was no version for 12.10, but I've seen somewhere on Google that it worked for other people). I decided not to install it just yet because I'm scared to screw up my system once again and I'm pretty tired of doing so.

I have a hard time understanding that part:

> **If you are using an Optimus system and are  installing the driver, you must pass the --optimus option to the CUDA  Toolkit installer.**                                         If you are instead installing a stand along  driver on an optimus system, you must pass --no-opengl-files to the  installer                         and decline the xorg.conf update at the end of  the installation.                                          You can select which packages you wish to  install at the start of the installation.

So, if I already have a driver installed from Bumblebee and the x-swat repo, do I have any argument to pass to the installer?

An other question is, what is the proper way of temporarily quitting the GUI on Ubuntu Studio? Do I just use *sudo stop lightdm*? And I just start it back after the installation?

Thanks to those who can answer that. I'd really like to make CUDA work so I can render faster with Blender, and I'm sure I'll find plenty more programs to accelerate. :)

---

### Post by jonathanfv on 2013-02-18
Alright, I figured everything out for my case.

They way that worked for me was the one from that blog:

[http://sn0v.wordpress.com/2012/12/07/installing-cuda-5-on-ubuntu-12-04/](http://sn0v.wordpress.com/2012/12/07/installing-cuda-5-on-ubuntu-12-04/)

It worked with Ubuntu 12.10. The one thing that didn't work was installing the driver from the CUDA installation, so I installed CUDA and the samples without the driver, then I installed Bumblebee and the driver after.

The compatible GCC was annoying. I ended up installing GCC 4.4 via apt-get, and to use that version while compiling all the CUDA stuff I simply made the symbolic link point to GCC-4.4 instead of GCC-4.7. I also had to do the same with G++ (install version 4.4 and change the symbolic link so it points to 4.4 instead of 4.7). And lastly, I've seen a method to use GCC/G++-4.4 only for compiling CUDA, so I'll find the page again and I'll do that.

Oh yeah, and for the shell without the GUI, you have to reboot or log out, and instead of logging in, press CTRL+ALT+F1.

Hope that can help others. Something else that helped me a lot when I crashed my GUI was to know how to set the PATH environment variable and how to set up a network connection from the command line. If you read this and want to try to play around with NVIDIA, I strongly advice you test the shell without any graphical interface, try to enter a few commands (and learn to set the PATH variable), and learn to setup a connection so you can use apt-get or access the Internet.

---

