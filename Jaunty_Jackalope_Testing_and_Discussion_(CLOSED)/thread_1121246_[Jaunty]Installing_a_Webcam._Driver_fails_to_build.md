---
title: "[Jaunty]Installing a Webcam. Driver fails to build."
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Ahrim on 2009-04-09
Hello first post here so pardon if I have misposted.

I'm trying to get this webcam to work, lsusb lists it as:

Bus 005 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 WebCam


Which if I'm not mistaken is supported by the GSPCA driver.
So I originally extracted that driver to /usr/src/ and ran make which led to this error:

make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

Disappointed I ran:

sudo apt-get install build-essential linux-headers-$(uname -r)

To make sure everything was in order, it was. Though it does say I no longer need libindicate0.

So I tried the module-assistant. Prepare, selected the drivers, update drivers, tried to build and...:

&#9474; Bad luck, the kernel headers for the target kernel version could   &#9618; 
     &#9474; not be found                                                       &#9618; 
     &#9474; and you did not specify other valid kernel headers to use.

And it recommends I prepare the headers which I did above.

So, can anyone help?

---

### Post by Ahrim on 2009-04-09
I don't believe this is the right forum to post this in. In case anyone was writing something here I won't delete this immediately. New one is under hardware

---

### Post by cariboo on 2009-04-10
I have a Logitech Quickcam messanger that used to use the gspca driver, but as of Intrepid the driver would no longer compile. The driver for your webcam may already be loaded. Open a terminal and type:

```
lsmod | grep spca
```

when I type the above command this is what I get:

```
smod | grep spca
gspca_zc3xx            59392  0 
gspca_main             34560  1 gspca_zc3xx
compat_ioctl32         18304  2 saa7134,gspca_main
videodev               45184  4 tuner,saa7134,gspca_main,compat_ioctl32
```

You should see something similar, the saa7134 is my tv tuner card so just ignore that.

Jim

---

### Post by Ahrim on 2009-04-10
Yes I get:

gspca_zc3xx            55552  0 
gspca_main             29952  1 gspca_zc3xx
videodev               41600  1 gspca_main


So this means that the driver needs to be updated for Jaunty then?

---

### Post by cariboo on 2009-04-10
No that is the driver that should be loaded when you boot Jaunty and connect your webcam. When running Jaunty try cheese, it is available in the repositories, It worked for me right out of the boax.

Jim

---

### Post by Ahrim on 2009-04-10
Ah thanks so much! I had just assumed it was a driver problem that the cam wouldn't work with skype or camorama.

---

