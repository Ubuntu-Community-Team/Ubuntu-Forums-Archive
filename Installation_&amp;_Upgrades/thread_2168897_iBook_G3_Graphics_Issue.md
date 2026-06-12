---
title: "iBook G3 Graphics Issue"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by alex47 on 2013-08-19
Hello All,

I've recently installed Lubuntu 13.04 on an ancient iBook G3 and I'm pleasantly surprised with how well it's working. My problem is when I boot to LXDE. Colors on the screen are inverted and very low quality. The log in window is displayed but merely as a shadow; I'm able to still access it though. 

Once I log in, certain windows like the Lubuntu Software Center, update manager, etc are able to display the title bar but the contents of the windows are blank. Firefox and the terminal work well. 

I'm assuming I need to change something in xorg.conf. Graphics issues seem to be pretty common on PPC machines. I've tried changing a few things in the Xorg file but either it doesn't change anything or it goes straight to tty1 upon boot. 

Does anyone know anything about this or have any suggestions? I'm at the end of my rope here; Lubuntu would be perfect were it not for this issue. 

iBook G3 Dual USB 600MHz, 256MB RAM, Radeon graphics

[IMG]http://i.imgur.com/8wLZQC1.jpg[/IMG]

[IMG]http://i.imgur.com/lLLlcxZ.jpg[/IMG]

[IMG]http://i.imgur.com/hZhQQOB.jpg[/IMG]

---

### Post by Boab1993 on 2013-08-19
Hi alex47

Not very familar on graphics problems, but ive seen them fixed in the past by kernel upgrades, so it could be a possibilty(?)

Documentation can be found here : [https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

Sorry i can't be more help.

---

### Post by alex47 on 2013-08-19
Followed the steps but I'm not sure any of these kernels will have the option to download for PPC. All I see is i386 and AMD

edit:

found the following. Testing it now. 
> sudo apt-get update
sudo apt-get install linux-image-powerpc-smp
sudo reboot




---

### Post by Boab1993 on 2013-08-19
[FONT=arial]Just tried the command out on terminal there to make sure there wasnt a hitch with lubuntu.

Mine outputted fine, with, screen shot below : 
[/FONT][FONT=arial]wget --no-check-certificate [https://github.com/medigeek/kmp-downloader/tarball/master](https://github.com/medigeek/kmp-downloader/tarball/master) -O kmpd.tar.gz

It sounds like just a typing error, try again, if it really doesnt work, ill see what i can come up with

Edit: well, if the info is ever needed in the future, it be here.
[/FONT]

---

### Post by Boab1993 on 2013-08-19
Ah, well as i said, graphics are not my strong point, and completely blanked the fact you had a Mac. Bit silly of me.

So ill redirect you to PPC FAQ page, on section 3 : [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

I checked to see if your mac is compatable, according to section 1.1, all iBooks are, so im assuming yours is.

Again sorry for the lack of direct help, Macs are another no go zone for me, but its best to try and get the ball rolling.

---

