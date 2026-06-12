---
title: "Howto install USB webcam?"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yumi on 2009-09-17
I own an older USB webcam which is not automatically recognised by Karmic.

Howto manually install it?

Is the tutorial using wacom [http://ubuntuforums.org/showthread.php?t=1038949&highlight=setup+usb+camera]("http://ubuntuforums.org/showthread.php?t=1038949&highlight=setup+usb+camera") relevant for Karmic?

Michael

---

### Post by jesterthejedi on 2009-09-18
I have this cam. It took me a long time, 6 months to get the right driver up and working. This is assuming the gspca/sonix will work on this cam. 

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file - located on the left bar
extract and change directory
in terminal type these commands no quotes:
"make distclean"
"make clean"
"make menuconfig" - choose the gspca/sonix, exclude others
"make"
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue mess.
Camorama, Kopete, and Skype require:
"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype(or alt)"

---

### Post by Yumi on 2009-10-15
Thanks for the detailed procedure. I tried to follow it, but make menuconfig results in the error 
> *** Install ncurses (ncurses-devel) and try again.

Unfortunatly ncurses-devel is not in the Kharmic repositories. I just wait until the final release and will try again.

Michael

---

### Post by FuturePilot on 2009-10-15
> **Yumi said:**
> Thanks for the detailed procedure. I tried to follow it, but make menuconfig results in the error 


Unfortunatly ncurses-devel is not in the Kharmic repositories. I just wait until the final release and will try again.

Michael

I believe you want the package "libncurses5-dev"

---

### Post by Yumi on 2009-10-15
Sounded good to me and I installed libncurses5-dev . Still complains that it wants ncurses-devel as you see below.

> michael@michael-desktop:~/Desktop/driver$ make menuconfig
make -C /home/michael/Desktop/driver/v4l menuconfig
make[1]: Entering directory `/home/michael/Desktop/driver/v4l'
make -C /lib/modules/2.6.31-14-generic/build -f /home/michael/Desktop/driver/v4l/Makefile.kernel config-targets=1 mixed-targets=0 dot-config=0 SRCDIR=/lib/modules/2.6.31-14-generic/build v4l-mconf
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
make -f /lib/modules/2.6.31-14-generic/build/scripts/Makefile.build obj=scripts/kconfig hostprogs-y=mconf scripts/kconfig/mconf
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** **Install ncurses (ncurses-devel)** and try again.
 *** 
make[3]: *** [scripts/kconfig/dochecklxdialog] Error 1
make[2]: *** [v4l-mconf] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [/lib/modules/2.6.31-14-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/michael/Desktop/driver/v4l'
make: *** [menuconfig] Error 2


Michael

---

### Post by emarkay on 2009-10-21
Any more info??

---

### Post by Starks on 2009-10-21
That driver is already in the 2.6.31 kernel.

If it doesn't work in Karmic, it probably won't work period.

---

### Post by Yumi on 2009-10-25
Well, it is working without installing or setting up anything. I just use Cheese and the picture appears on the monitor. Cheese finds the camera automatically which is plugged into a USB port.

Well done Karmic.

Michael

---

