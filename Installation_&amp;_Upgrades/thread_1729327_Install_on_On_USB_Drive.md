---
title: "Install on On USB Drive"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by crazzzme on 2011-04-14
I have a Netbook that Im helping a friend out with. He Broke his Hard drive im simplest terms Long Story dont want to explain it. So i cant insatall to the hard drive becuase the bios wont even recognize it. Now i have a 4 gb Flash Drive  and I know its possible to do as ive done it with other usb devices with ubuntu before but can som e one tell me how to install the full os to the Flash Drive. Not a Live Bootable USB but just install the OS to the drive.
Ive Tried Using Wubi and that doesnt recognize my Flash drive only my C drice and Ive tried using Pendrive linux's tool to install it but it just made a live cd.
Also because the hard drive is pretty much just dead. WHen it boots  it tires to what i guess is find the hdd it keeps giving me the error 
ata1: soft rest failed(device not ready)
ata1:link is slow to respond, please be patient
ata1: sata link is up to 3 gbps
then it repeats that error  while the error code on the side keeps incrementing

---

### Post by Hedgehog1 on 2011-04-15
To do a real Ubuntu install on a USB stick, you will need a desktop computer that can boot from a CD.

1) Create a LiveCD of Ubuntu from an ISO

2) With power off, disconnect the hard drive in the desktop PC

3) Power-on the desktop, boot from the CD.

4) Insert the USB stick into a USB port.

5) Select 'install' and the installer will install on the USB stick because it cannot find a hard drive.

6) Reboot when the install says to and remove the CD.

7) Allow the USB install to do it's updates, but DON'T INSTALL ANY RESTRICTED VIDEO DRIVERS YET (do that later from the busted netbook). 

8 ) Once the updates are done, power down and plug the hard drive back in.

9) Insert the USB stick (Now an **Ubuntu-On-A-Stick!**) into the netbook.  It is ready to run!


***The Hedge***

:KS

p.s. I run a Partiot XT Rage USB stick with Ubuntu 10.10 and use it to demo Ubuntu.  Works very nice!

---

### Post by Hedgehog1 on 2011-04-15
By the way - is it possible to remove the dead hard drive from the netbook?  It is just wasting battery plugged in and dead.

Just a thought...

---

### Post by crazzzme on 2011-04-15
Yes it is its out most of the time. When it not being used i put it in just so i can remember where it is

---

