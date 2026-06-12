---
title: "Video Drivers/Permissions  problem"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by bmwman on 2008-06-17
Hello, I'm trying to get my old pcmcia tv tuner to work. I installed the latest drivers from [http://linuxtv.org/cvs.php](http://linuxtv.org/cvs.php) and I think the card works fine. I can see it when I run 'lspci' and the modules seemed to be loaded as well 'lsmod':

saa7134               144724  0 
joydev                 13120  0 
videodev               35072  1 saa7134
v4l1_compat            15748  1 videodev
compat_ioctl32          2304  1 saa7134
v4l2_common            12672  1 saa7134
videobuf_dma_sg        14980  1 saa7134
videobuf_core          19716  2 saa7134,videobuf_dma_sg
ir_kbd_i2c             11152  1 saa7134
ir_common              41348  2 saa7134,ir_kbd_i2c
irtty_sir               9728  0 
tveeprom               13444  1 saa7134
sir_dev                17412  1 irtty_sir
i2c_core               24832  4 saa7134,v4l2_common,ir_kbd_i2c,tveeprom
pcmcia                 40876  0 

Then I try to run tvtime and i get permission denied:


bmw-man@bmw-man-laptop:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/bmw-man/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/bmw-man/.tvtime/tvtime.xml: Permission denied.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

If I run with "sudo" i get this:

bmw-man@bmw-man-laptop:~$ sudo tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/bmw-man/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

Sounds like I have multiple problems, one is the permissions and also the video card drivers. I'm using a laptop IBM T43 and it has ATIx300 128MB video card.

Any ideas how to fix this?
Thanks

---

### Post by bmwman on 2008-06-17
Little update: I just installed the latest drivers from ATI and still getting the same problem.

---

### Post by bmwman on 2008-06-18
Nobody?

---

