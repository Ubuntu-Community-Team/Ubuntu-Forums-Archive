---
title: "Atheros AR242x wireless cards"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2008-08-19
Does anyone know if these cards work out of the box in intrepid. It seems to find the card and attempt to connect to the wireless network but just sits for a while saying "requesting address" and then disconnects. 

I could have sworn it worked in an earlier alpha. 

George

---

### Post by gmclachl on 2008-08-20
> **gmclachl said:**
> Does anyone know if these cards work out of the box in intrepid. It seems to find the card and attempt to connect to the wireless network but just sits for a while saying "requesting address" and then disconnects. 

I could have sworn it worked in an earlier alpha. 

George

I guess I will need to grab the madwifi snapshot and compile the drivers, something I was really hoping to avoid.

George

---

### Post by gmclachl on 2008-08-20
Well I guess I am **** out of luck. 

It appears that ath5k is now used in 2.6.26-5 which apparently doesn't work with the ar242x. 

Also the madwifi drivers won't compile against 2.6.26-5 so I guess there will be no wireless for me. 

George

---

### Post by hexion on 2008-08-20
Try with the drivers here:
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

> make
sudo make uninstall
sudo make install

then blacklist ath5k by adding this to /etc/modprobe.d/blacklist
> blacklist ath5k

then reboot

---

### Post by gmclachl on 2008-08-20
I tried the snapshot and got the error
 cc1: warnings being treated as errors

I grabbed it from svn and it compiled. However doing a "make install" seems to put the modules in the wrong kernel directory 

I am running 2.6.26-5 and it installs the modules in 

/lib/modules/2.6.26.2

not 

/lib/modules/2.6.26-5

although 
 
/lib/linux-restricted-modules/2.6.26-5-generic 

seems to have the modules already

George

---

### Post by gmclachl on 2008-08-22
For anyone else with the same issue. The ath9k drivers work well with this card. This can/is also built into the 2.6.27 kernel.So although there will be no support for it Intrepid* hopefully it will be in 9.04 

*Assuming it's not patched back.

George

---

### Post by stereo_steve on 2008-08-22
looks like we are getting .27 though!

---

### Post by svlad cjelli on 2008-08-27
So guys...

do i understand right that:

-the integrated ath5-driver will never support wireless for our cards?
(madwifi will after installation)

-the new ath5k will support various atheros-chipsets, but not ours?
(and we have continue installing the madwifi-snapshots)?

-it is unsure when the ath5k-driver will be integrated in the Linux-Kernel, respectively in which Version (2.6.26/2.6.27 or higher)?

-the brand-new ath9k-driver will solve our Problems?

-it is unsure when the ath9k driver will be integrated in the Linux-Kernel and we dont know in which version?



Sorry for my  stupidness and for my english :-)

---

### Post by hexion on 2008-08-27
I have the same card (in a hp compaq presario A900 laptop) and it works perfectly with 2.6.27 following these steps:

1) Install the kernel 2.6.27 (image and headers) for hardy or intrepid:
Intrepid: [http://kernel.ubuntu.com/pub/next/2.6.27-rc3/intrepid/](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/intrepid/)
Hardy: [http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/)

2) Reboot to use the new kernel (use "**uname -a**" to check)

3) Grab this driver:
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)

4) Install the driver (follow the steps exactly)
- Uncompress it.> 
- make
- sudo make uninstall
- sudo make install5) Blacklist ath5k.
Add this line (without quotes) to the end of the file **/etc/modprobe.d/blacklist**
> blacklist ath5k
6) Create the directory with the firmware for the new kernel:
> cd /lib/firmware
lsidentify the directory for the most recent kernel (in example, the folder "2.6.24-21-generic" in my system)
> sudo cp -R 2.6.24-21-generic `uname -r`7) Reboot and enjoy. If you can't see networks, pulse the wireless button to activate the radar


Hope it helps

---

### Post by gmclachl on 2008-08-27
This card works out of the box with ath9k, which needs to be enabled in the kernel. So I didn't need to install madwifi, it may be possible that the intrepid build does not have this module included. 

George

---

### Post by siddhuwarrier on 2008-10-26
I dont know how to enable it from the kernel. I treid a modprobe (a modinfo found ath9k), but though it turned up on lsmod, the connection didn't work. I had to reinstall the madwifi drivers from source (that and a reboot worked for me).

Ubuntu 8.10 - kernel 2.6.27-7

---

