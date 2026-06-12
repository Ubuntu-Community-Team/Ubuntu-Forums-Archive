---
title: "Install Problem on Dell Dimension E520"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by scannerdarkly on 2006-10-28
I'm trying to install Ubuntu on my new Dell Dimension E520 and I'm trying to load the live cd but I get an error saying that it can't load X.  I've installed on my dell laptop with out a problem.  Any ideas?

---

### Post by scannerdarkly on 2006-10-28
It has the Intel 3.0 GHz with Hyper Threading and I have the Intel G965 Express Chipset that comes with the Integrated X3000 Graphics accelerator.

---

### Post by Xoctor on 2007-02-21
Did you end up getting anywhere? I have am just discovering how difficult it is to get the E520 (and the X3000 in general) working reasonably under Ubuntu.

I have a Dell 2707WFP 1920x1200 monitor, and I can't do any better than unaccelerated 1600x1200 - which is unacceptable really.

Its starting to look like the only option is either a new motherboard or a PCI-E video card, which I don't want to do because not only is it a waste of money and natural resources, but it will also use more electricity, make more noise and more heat.

---

### Post by allen248 on 2007-03-06
For what its worth... I have a Dell E520, and I'm having quite a few problems too.  

To get around the video issue, I booted from the CD using the safe graphics mode and installed that way.  It installed OK.  You could also try using the alternative CD and doing a server install.  However, you will probably run into a network card problem.

Anyway, I have Ubuntu Dapper Drake installed on my E520, but the network card drivers do not load at all.  Looking at the forums, this seems to be a common problem, and nobody has yet posted the fix.  It appears as if Edgy installs OK, however.

---

### Post by allen248 on 2007-03-06
I finally got my network ethernet card to work using Dapper on a Dell E520.

Symptom...  I installed from the CD.  After reboot, when I ran ifconfig, only the 'lo' interface appeared.  There was no 'eth0' because the driver for the E520 did not appear.

The thread below has all the information needed, but it is very hard to comprehend for a new linux user like myself.

[http://ubuntuforums.org/showthread.php?t=276126&page=2](http://ubuntuforums.org/showthread.php?t=276126&page=2)

So, if you have a new Dell E520 and you want to get the ethernet to work for a Dapper install, try this:

     1.  Insert the installation CDROM.  Use the Syaptic Package Manger (from the System Menu) to install gcc, make, and the kernel source headers using the CD as the source.  
     
     2.  Download the driver source tarball from Intel.  The one that worked for me was named e1000-7.4.27.tar.gz.  Use a USB drive to move this file from a computer having internet to the Dapper computer without enternet.

     3.  Untar the driver source to a temporary directory.
 
     4.  navigate to the src directory of the driver source and run 'sudo make install'

     5.  the make may give an error about 'cannot write ... catman mode' which can be ignored

     7.  'sudo modprobe e1000' to install the driver

     8.   I also had to configure DNS 

All this should take about 1 hour.

Also note:  When I updated my kernel, I had to rebuild the driver again.  So if you upgrade to i686 then be sure to download the kernel headers and the driver source first.   Sure it is work, but the price is right.

---

### Post by Xoctor on 2007-03-06
I've been using Edgy, so the graphics worked well enough to boot, its just that without the proper drivers I can't get the native resolution for my screen or proper acceleration. I solved the networking problem by slotting in a PCI network card. Actually, I've solved the video problem that way too - I bought an nvidia 7100GS for AUD$80. It has the advantage of being fanless, having dual monitor support and having a DVI output.

The E520 seems like a very good machine. Quite powerful, yet it doesn't generate much noise or heat. I really hope the Ubuntu team are able to fully support it in the next release.

---

### Post by antonyb on 2007-03-20
Hi 

For what its worth, Feisty Herd 5 installed practically out of the box for me on an E520. The only problem was that it defaulted to the "vesa" driver in xorg.conf. I changed that to i810 and everything now works great.

Let me know if I can provide any useful info.

Ant.

---

