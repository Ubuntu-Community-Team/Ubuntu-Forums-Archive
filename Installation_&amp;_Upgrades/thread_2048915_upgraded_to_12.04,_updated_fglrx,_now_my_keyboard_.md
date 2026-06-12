---
title: "upgraded to 12.04, updated fglrx, now my keyboard and mouse dont work"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by nariub on 2012-08-27
I had a 10.04 machine with an ATI radeon video card.

I updated to 12.04, everything was cool
went to upgrade fglrx to the binary version from the website
"amd-driver-installer-12.6-legacy-x86.x86_64.zip"

I used the .run file to create the deb package
I used dpkg -i to install the deb package

it wanted to reboot..  this is where things went awry..
upon reboot I get the login screen and no keyboard or mouse.

..
I can ssh into it from another box.. and she seems to be fine.. except I cannot seem to get it to recognize my keyboard and mouse on the login screen.

lsusb says the keyboard is there..
I can get into and use bios with the keyboard and mouse
but I cant even interrupt the boot to get into grub on this thing..

I have uninstalled fglrx, reinstalled it, removed it and tried installing the one from the repositories, same same..  no keyboard or mouse..  anybody know what is going on with this.. ?

---

### Post by nariub on 2012-08-28
An update,
  since it is a new upgrade..
  i held down the left shift while booting
    the offered 3.2.0-29 is the one that has no keyboard.
      (pressing e from that menu tells me that is a virtual image of some sort)
    selecting the recovery image from the main grub menu gives me an ansi graphic with no keyboard or mouse..

   if i select other linux versions, i can see my old 10.04 kernels  and two other generic versions of 3.2.0-29 
       main one gives me mouse and keyboard (i think because the video is black) but the numlock works on the keyboard..  if i blind login i see the numlock blink where it always does when i log in.. 
      if i log in using the generic recovery, and hit resume to normal boot

  and she logs in and keyboard worked and everything

went through the following to reinstall fglrx 
> sudo apt-get purge fglrx*
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
sudo dpkg -i fglrx*.deb
sudo update-alternatives --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf 100 --slave /usr/lib/x86_64-linux-gnu/xorg/extra-modules x86_64-linux-gnu_xorg_extra_modules /usr/lib/fglrx/xorg/modules/
sudo ldconfig


and which installed the fglrx on the generic kernel.
and now i startx in recovery mode on the generic and she looses the keyboard and mouse..  curious  as to what is going on   anyone??

---

### Post by nariub on 2012-08-28
uninstalled the drivers from amd
mounted the alternative cdrom and reinstalled the fglrx from the debs on 12.04.1 disc

generic-recovery mode is graphical again..  still real curious about what is going on and how to fix it..

---

### Post by nariub on 2012-08-29
uninstalled the fglrx drivers.
running the generic kernel with vesa drivers and gallium..

sure wish i could get fglrx to work with a keyboard and mouse.

---

### Post by nariub on 2012-08-29
Followed the direction on this url. (used my 12.6 installer)

[http://ubuntuportal.com/2012/03/new-ati-catalyst-12-3-has-been-released-how-to-install-in-ubuntu-12-04-and-linux-mint-12.html](http://ubuntuportal.com/2012/03/new-ati-catalyst-12-3-has-been-released-how-to-install-in-ubuntu-12-04-and-linux-mint-12.html)

did this on the generic kernel.
I seem to have a functional amdcccle and fglrx info says i am using the right OpenGL

Jockey still has no idea what I am doing.. it reports the fglrx driver is not active
when i attempt to activate /var/log/jockey.log says the binary has no trusted source and rejects it. ... mmm maybe.. 



meantime,
 and when i boot off the virtual image, i still have no mouse and keyboard.

---

### Post by nariub on 2012-09-05
I am simple

I must have installed the virtual kernels at somepoint in the past..

they are for VM's not for real boxes, (so I am told)

I have removed them and their headers and each of the images with 
apt-get remove 

i re-ran update-grub
rebooted

installed fglrx 
apt-get install fglrx

other than the System Settings > Details saying I am running VESA RV620
it seems to be working,  amd-cccle works 

installed Compiz  and I even have my wobbly windows back.

Marking this one solved.

---

