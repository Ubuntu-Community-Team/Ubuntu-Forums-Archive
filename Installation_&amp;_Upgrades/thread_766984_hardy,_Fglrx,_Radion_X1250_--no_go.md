---
title: "hardy, Fglrx, Radion X1250 --no go?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Jellman on 2008-04-25
Hello Every One. 
Im having a problem getting hardy to start the X server with my ati X1250 integrated GFX on my laptop. (Samsung R60+) 

The install procedure im about to go through worked on 7.10 but dosent on 8.04. 

Once installed via alt cd i just install FGLRX through sudo apt-get install xorg-driver-fglrx and then depmod -a and then aticonfig --initial (says theres no driver line so i add driver "fglrx" to xorg.conf and then it stops complaining.) and then aticonfig --overlay-type=Xv and finally startx.

That would boot me in to a usable GUI in 7.10 but it just returns a white screen and a curser in 8.04.

Any ideas? 

All the best, Scott

---

### Post by Pumalite on 2008-04-25
ATI has very little support for Linux.
Reconfigure your xserver and choose 'vesa'

---

### Post by Peter_72 on 2008-04-26
> **Jellman said:**
> Hello Every One. 
Im having a problem getting hardy to start the X server with my ati X1250 integrated GFX on my laptop. (Samsung R60+) 

The install procedure im about to go through worked on 7.10 but dosent on 8.04. 

Once installed via alt cd i just install FGLRX through sudo apt-get install xorg-driver-fglrx and then depmod -a and then aticonfig --initial (says theres no driver line so i add driver "fglrx" to xorg.conf and then it stops complaining.) and then aticonfig --overlay-type=Xv and finally startx.

That would boot me in to a usable GUI in 7.10 but it just returns a white screen and a curser in 8.04.

Any ideas? 

All the best, Scott
I have the same laptop model and the same problem.

Though I get a black screen without cursor when trying to get into X.

Have you found a solution?

---

### Post by Pumalite on 2008-04-26
You can also try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by BB_DaKraxor on 2008-04-26
I'd recommend downloading a driver from [http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html"). Stop the X server and run the downloaded file (should be something like ati-driver-installer-8-4-x86.x86_64.run) as root. No further actions should be necessary. I have a card from the ATI Radeon X1200 Series and I have no problems besides the very low FPS rate in some games.

---

### Post by Peter_72 on 2008-04-26
Thanks! It worked!
Envyng is a nice little tool!

---

### Post by toughengineer on 2010-05-20
> **BB_DaKraxor said:**
> I'd recommend downloading a driver from [http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html"). Stop the X server and run the downloaded file (should be something like ati-driver-installer-8-4-x86.x86_64.run) as root. No further actions should be necessary. I have a card from the ATI Radeon X1200 Series and I have no problems besides the very low FPS rate in some games.

i have this problem with my VGA card

~$ dmesg |grep fglrx
[ 3624.055564] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[ 3624.198992] [fglrx] Maximum main memory to use for locked dma buffers: 2754 MBytes.
[ 3624.199292] [fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[ 3624.199297] [fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
[ 4594.645349] fglrxinfo[14986]: segfault at 4 ip 0063eef6 sp bfe07510 error 4 in libGL.so.1.2[5d9000+a7000]

any help ...

---

