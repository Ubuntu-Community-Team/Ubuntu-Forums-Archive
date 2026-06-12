---
title: "help with incredibly frustrating sound card driver installation problem"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by adamgram on 2008-11-24
I'm trying to set up Ubuntu on my Dell Dimension E521 desktop with a Creative SB-XFi sound card.  I downloaded the driver from the Creative website, extracted the .tar.gz file, went to the folder under root and typed 'make' followed by 'make install'.  Here is what my terminal looked like doing this:

-----

adam@adam-desktop:~$ cd Desktop
adam@adam-desktop:~/Desktop$ cd XFiDrv_Linux_Public_US_1.00/
adam@adam-desktop:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for adam:
make -C /lib/modules/2.6.24-16-generic/build M=/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.o
/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function 'ct_alsa_pcm_create':
/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of 'snd_pcm_new' discards qualifiers from pointer target type
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
  CC      /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/adam/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
adam@adam-desktop:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
make: *** [install] Segmentation fault
adam@adam-desktop:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 

-----

Next I rebooted my computer.  It got to the Ubuntu screen with the orange bar that goes across as it loads, but the bar got stuck half way.  After a couple minutes, the screen went blank and this was typed out on it:

-----

* reading files needed to boot....     [ok]
*preparing restricted drivers... [ok]
*setting the system clock... [ok]
*starting basic networking... [ok]
*starting kernely event manager... [ok]
*loading hardware drivers... [ok]
udevd-event[3033]:run_program: '/sbin/modprobe' abnormal exit

*setting the system clock
*loading kernel modules
*loading manual drivers... 

-----

Now every time I reboot in Ubuntu it goes straight to this screen.  I can do a clean reinstall to back out of this (there isn't anything on the computer to worry about erasing or anything like that).  But if anyone could tell me what any of this means or what I need to do to install the driver properly, I'd really appreciate it!  Thanks in advance!

---

### Post by alpage2 on 2008-11-24
A quick look at other threads suggests that this driver works under ubuntu 8.10, but not with 8.04. Which version are you using?

Alan

---

### Post by adamgram on 2008-11-24
I've tried it with both.  I started with 8.04, tried a bunch of stuff to get it to work, most of which involved reading how-to's on the web and just blindly doing whatever they said only to get an error message and backing out with things half-configured.  This was giving me a different problem than I'm facing now... it was an error message in the terminal after running 'make install'  Anyway, at the suggestion of someone else I upgraded to 8.10, and things didn't work any differntly... same error message in the terminal during make install.  So, I did a fresh reinstall back to 8.04 and that takes us to my original post.  Since you suggested it again, now I'm upgrading back to 8.10, but this time without whatever half-configured changes I made when I originally tried a bunch of random how-to's.  We'll see if this works!  Thanks!

---

