---
title: "No display after installation"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by adityasen on 2005-09-11
I got the Ubuntu distro ver 5.04 and tried installing it. But after the installation is completed, and the msg comes 'Starting Ubuntu'...the whole screen goes blank and the X-server wont start up. Nothing that I try works. Only pressing Ctrl-Alt-Del brings back the terminal and says 'Powering Off'. The same prob occurs if I use the live-cd. Please help me out.
My comp is a HP Compaq M2202 Notebook, with a Celeron 1.3Ghz, Intel Mobile Extreme Graphics, 256MB RAM, 40GB HDD, CD-DVD.

I also have a desktop P4 2.4Ghz. The Ubuntu installation works fine there, but if I access certain folders, eg, my USB Pen Drive or the 'My Documents' folder of my Windows FAT32 partition, I get an error "the application nautilus has quit unexpectedly". Then I am given options to retsart it, close it, or inform the developers. The 1st two options dont help.

SO pls help me out in any one of these probs..

Thankx a ton...peace

---

### Post by Thulemanden on 2005-09-12
It resembles trouble with the video driver. Try a generic one via xorgconfig in a terminal window or via new installation.

Wait for more experienced replies before you try it.

---

### Post by merovingian on 2005-10-19
Same problem here with a ThinkPad T43 .... 

Breezy is working but there is a need to run Hoary on this laptop


Any ideas? 


Merv

---

### Post by N8K99 on 2005-10-21
I have installed Hoary on a Toshiba Tecra 550CDT laptop (it's old) and I am have a similiar probelm, however, I am certain that everything is running. I just do not have anything on the screen, well, I have something on the screen but it resembles a sandstorm at night. I have installed this very same CD on two other machines and it works beautifully. I'm wondering if anyone knows how to alter Xorg so that it will work on this machine. Or at least where to start tweaking.  

BTW- Hoary does not see the laptop ethernet card for this machine. It is a Xircon Credit Card modem.

---

### Post by N8K99 on 2005-10-23
I have solved my display probelm and Ubuntu Linux is now working on a Toshiba Tecra 500CDT laptop. I opened [SIZE="1"]/etc/X11/xorg.conf[/SIZE] with nano, and read the instructions on how to reconfigure [SIZE="1"]xserver-xorg[/SIZE]. Once I got to the part where I needed to supply information about my monitor, I had looked up the specs for this model on Google ( being very specific about what I needed yeilded good results). These specifications were filled into the reconfiguration program and the end result is the same beautiful display that I have on the Desktop coomputer. Now if only I could get the network cards recognized then I'll be connecting to the internet and watch out world!!:D

---

