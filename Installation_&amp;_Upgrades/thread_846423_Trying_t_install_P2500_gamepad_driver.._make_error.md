---
title: "Trying t install P2500 gamepad driver.. make errors"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by billdotson on 2008-07-01
here is the output:

> make -C /lib/modules/2.6.24-16-generic/build M=/home/bill/Desktop/SP2500 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/bill/Desktop/SP2500/saitek_p2500.o
/home/bill/Desktop/SP2500/saitek_p2500.c:38:26: error: linux/config.h: No such file or directory
/home/bill/Desktop/SP2500/saitek_p2500.c:122: error: implicit declaration of function ‘NBITS’
/home/bill/Desktop/SP2500/saitek_p2500.c:122: error: variably modified ‘flags’ at file scope
/home/bill/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_input_event’:
/home/bill/Desktop/SP2500/saitek_p2500.c:241: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/bill/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_upload_effect’:
/home/bill/Desktop/SP2500/saitek_p2500.c:291: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/bill/Desktop/SP2500/saitek_p2500.c:395: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/bill/Desktop/SP2500/saitek_p2500.c:396: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/bill/Desktop/SP2500/saitek_p2500.c:397: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/bill/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_close’:
/home/bill/Desktop/SP2500/saitek_p2500.c:467: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/bill/Desktop/SP2500/saitek_p2500.c:471: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/bill/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_flush’:
/home/bill/Desktop/SP2500/saitek_p2500.c:485: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/bill/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_process_packet’:
/home/bill/Desktop/SP2500/saitek_p2500.c:509: error: implicit declaration of function ‘input_regs’
/home/bill/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_probe’:
/home/bill/Desktop/SP2500/saitek_p2500.c:660: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/bill/Desktop/SP2500/saitek_p2500.c:667: error: incompatible types in assignment
/home/bill/Desktop/SP2500/saitek_p2500.c:677: error: ‘struct input_dev’ has no member named ‘upload_effect’
/home/bill/Desktop/SP2500/saitek_p2500.c:682: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/bill/Desktop/SP2500/saitek_p2500.c: At top level:
/home/bill/Desktop/SP2500/saitek_p2500.c:754: error: unknown field ‘owner’ specified in initializer
/home/bill/Desktop/SP2500/saitek_p2500.c:754: warning: initialization from incompatible pointer type
make[2]: *** [/home/bill/Desktop/SP2500/saitek_p2500.o] Error 1
make[1]: *** [_module_/home/bill/Desktop/SP2500] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2


I would decipher this myself but I have no idea what any of that means.  Thanks.

---

### Post by billdotson on 2008-07-01
I think the gamepad is already working in Ubuntu Hardy out of the box, at least with Gens.  hmm.

---

### Post by billdotson on 2008-07-01
but Gens won't open now, it just pops up for a second and then goes away, strange.

Edit: right now, about 20 minutes later I found a similar post on this forum that said the .gens folder in home/YourUserName needs to be deleted manually.  That fixes the Gens thing (all except for the fullscreen which could be OpenGL), and the gamepad is working fine as far as I can tell, I just don't know why it wouldn't make.

---

### Post by starcannon on 2008-07-01
I've got the same gamepad here, Saitek p2500, jscalibrate likes it, but in Mame the buttons work but the digital pad and Analog Sticks don't...

---

### Post by starcannon on 2008-07-02
I got the Saitek P2500 working:

```
sudo apt-get install xserver-xorg-input-joystick
```

Then if the joystick is plugged in, unplug it, and plug it back in.

Enjoy Mame and possibly other gaming goodness.

Enjoy,

~starcannon

---

