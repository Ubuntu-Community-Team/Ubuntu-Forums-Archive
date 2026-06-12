---
title: "Shutdown problem on Toshiba C655 laptop"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by hufemj on 2010-11-29
I just bought a Toshiba C655 laptop and installed ubuntu 10.10 64 bit on it. Shut down does not complete. I disabled the splash screen to get the text display on shutdown. The display announces that the system has halted. However, the power remains on. A quick click of the power button and it will power down. What do I need to do to get the shutdown process to take that final step of actually shutting off the power?

---

### Post by AirWreck on 2010-12-19
Same problem here...anyone shed any light?  Thanks.

---

### Post by rekrapenator on 2010-12-20
> **AirWreck said:**
> Same problem here...anyone shed any light?  Thanks.

Yep me too - toshiba satellite c650
Would like some ideas thanks

---

### Post by rekrapenator on 2010-12-21
Did a fresh install using 10.10 and all seems sweet - what a relief. Shutting down starting up, wireless and network, sound and usb whew!!!

---

### Post by javiersc on 2011-03-19
I just install ubuntu 10.10 and got this issue any time I touch the power button, this work like a reset button, so I always forgot and make worried about my hard disk, on the other hand I got a triple boo-table computer with W7 (the original OS with my computer), linux mint that make me got ubuntu but in a more easy way, and edubuntu for the school children, so I got a lot of trouble with the installation of edubuntu 2 attempts and the 2 fail after 15 minutes, so I install ubuntu 10.10 and then download edubuntu and choose this distro for my 3er OS.

But the power button don work when I shutdown edubuntu, any got an idea about how to fix it on the terminal with out reinstall for 4 time ubuntu!

Thanks

](*,)

---

### Post by Julian Lewis on 2012-09-30
I have installed Ubuntu 12.04 on a Toshiba C655. The alt1c driver freezes when Ubuntu is booted with no wired Ethernet cable in place. This is what I did to fix the problem.
Install Ubuntu AMD64 bit version keeping the Ethernet plugged in, if not the install will freeze. Once up go to 
[www.linuxfoundation/collaborate/workgroups/networking/alx](www.linuxfoundation/collaborate/workgroups/networking/alx)
and download the compat-wireless-2012-05-10-p.tar.bz2 tarball and svave it in your home directory, I put it in a folder named alx. Go there and extact it. Follow the instructions on the website ... 
./scripts/driver-select-alx then make and sudo make install. 
Then you reboot. When the reboot is over you still see the alt1c driver so we need to get rid of it. Do 
sudo rmmod alt1c, then 
sudo depmod alx  after that your wired connection comes back up, last do a 
sudo depmod -a and last but not least 
sudo update-initramfs -u

Reboot and it works a treat... It took me a while to figure this out, I hope it will help.

---

