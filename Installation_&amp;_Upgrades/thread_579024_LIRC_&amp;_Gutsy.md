---
title: "LIRC &amp; Gutsy"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by bmilleker on 2007-10-17
I am using gutsy and cant get LIRC working. I have a USB-UIRT. I would like to know if support is broken in Gutsy? What modules need to be loaded to use this device?

---

### Post by bmilleker on 2007-10-18
:guitar:

---

### Post by srt4play on 2007-10-25
Have you made any progress?  I also can't get my usb-uirt to work with gutsy (mythbuntu).

---

### Post by bmilleker on 2007-10-25
I followed the advice on this forum: [http://www.gossamer-threads.com/lists/mythtv/users/293531?do=post_view_threaded#293531](http://www.gossamer-threads.com/lists/mythtv/users/293531?do=post_view_threaded#293531)

Just an fyi.... when i rebuilt my kernel I had to manually get alsa working, and my wifi drivers... but I do have LIRC working now so it wasn;t a huge deal.

---

### Post by srt4play on 2007-10-25
Instead of recompiling a kernel couldn't you just install an earlier kernel package from packages.ubuntu.com? 

I'll try again tomorrow, thanks for the info.

---

### Post by bmilleker on 2007-10-25
I am not sure. I used a 2.6.20 kernel, but I couldn't find the right source for it so no new nvidia drivers.

---

### Post by srt4play on 2007-10-26
I copied the ftdi_sio source and header into the kernel source tree and then did a 

```
sudo make modules
```

hoping to build just the modules and avoid a time-consuming total kernel build.

Once that was done I copied the new ftdi_sio.ko file to replace the old one, and it works great.  If anyone knows how to build just a single module instead of all of them that would be great to know for the future.

Thanks again for sharing your solution.

---

### Post by chaumurky on 2007-11-11
From which source version are you building - I get a bunch of make errors from Edgy's (2.6.17). Dropping the .ko (Feisty or Edgy) in doesn't work either (complains about symbols etc when trying to load). I can't believe I got this delivered today and I can't use it - not just out of the box but at all. :mad: I've totally wasted my money.

EDIT: I've rolled back the kernel, restricted modules and nvidia-glx-new and it's working - still getting a checksum error but it's not apparently fatal. I's forced me to hack a couple of other bit's to get my HTPC back to normal. This is not a long term solution...

---

### Post by bmilleker on 2007-11-11
> **chaumurky said:**
> I can't believe I got this delivered today and I can't use it - not just out of the box but at all. :mad: I've totally wasted my money.

Research products before you go out and buy them. I have a microsoft receiver, and my usb-uirt working perfectly. There is no reason why yours shouldn't.

I used files from 2.6.20.

What are the errors you receive?

---

### Post by chaumurky on 2007-11-13
You must mean that I have to research the effect of future kernels to devices that are currently working by recent accounts. Your reference is to 'products',  not just to the usbuirt I posted about so are you judging me as a person who does this all the time? I hope your research into my nature went beyond this one post or you are as bad as me aren't you.? Perhaps it was just arrogance but I'm not interested enough to research any further. Anyway, my research indicated that owners running Feisty had no problems with this device so I decided to order it. At the time I was running Feisty and made my decision based on that. I upgraded to Gusty in the meantime and the rest is researchable history.

The error is as follows and is fatal on kernels above 2.6.20:

[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]uirt2_raw: checksum error 
uirt2_raw: UIRT version 0905 ok 
uirt2_raw: could not set DTR 
caught signal
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
Like I said though, in my previous post, rolling the kernel back is a temporary solution and I have nothing further to add.

---

### Post by srt4play on 2007-11-15
I used ftdi_sio.c and ftdi_sio.h from 2.6.20.  

Copy them into the 2.6.22 source tree in their appropriate places and 'sudo make modules' and you should be good.

---

### Post by chaumurky on 2007-11-18
Hmm, I'll give it another go but I could have sworn i got into make troubles when i tried it. guess there's no harm in trying it again.

EDIT: I wonder what I did wrong last time - this time ftdi_sio.ko built fine. Perhaps it was because i was booted to the 2.6.20 kernel. Anyway it seems 2.6.24 will fix this problem but until then, thanks srt4play for your help. :)

EDIT: Spoke too soon. Can't load the module:
```
 Nov 19 19:13:36 ATTICUS kernel: [   36.486839] ftdi_sio: no version for "struct_module" found: kernel tainted.
Nov 19 19:13:36 ATTICUS kernel: [   36.487193] ftdi_sio: disagrees about version of symbol usb_alloc_urb
Nov 19 19:13:36 ATTICUS kernel: [   36.487196] ftdi_sio: Unknown symbol usb_alloc_urb
Nov 19 19:13:36 ATTICUS kernel: [   36.487276] ftdi_sio: disagrees about version of symbol usb_free_urb
Nov 19 19:13:36 ATTICUS kernel: [   36.487279] ftdi_sio: Unknown symbol usb_free_urb
Nov 19 19:13:36 ATTICUS kernel: [   36.487364] ftdi_sio: disagrees about version of symbol usb_serial_port_softint
Nov 19 19:13:36 ATTICUS kernel: [   36.487367] ftdi_sio: Unknown symbol usb_serial_port_softint
Nov 19 19:13:36 ATTICUS kernel: [   36.487439] ftdi_sio: disagrees about version of symbol usb_register_driver
Nov 19 19:13:36 ATTICUS kernel: [   36.487442] ftdi_sio: Unknown symbol usb_register_driver
Nov 19 19:13:36 ATTICUS kernel: [   36.487545] ftdi_sio: disagrees about version of symbol usb_serial_disconnect
Nov 19 19:13:36 ATTICUS kernel: [   36.487548] ftdi_sio: Unknown symbol usb_serial_disconnect
Nov 19 19:13:36 ATTICUS kernel: [   36.487595] ftdi_sio: disagrees about version of symbol usb_submit_urb
Nov 19 19:13:36 ATTICUS kernel: [   36.487598] ftdi_sio: Unknown symbol usb_submit_urb
Nov 19 19:13:36 ATTICUS kernel: [   36.487726] ftdi_sio: disagrees about version of symbol usb_control_msg
Nov 19 19:13:36 ATTICUS kernel: [   36.487729] ftdi_sio: Unknown symbol usb_control_msg
Nov 19 19:13:36 ATTICUS kernel: [   36.487813] ftdi_sio: disagrees about version of symbol usb_deregister
Nov 19 19:13:36 ATTICUS kernel: [   36.487816] ftdi_sio: Unknown symbol usb_deregister
Nov 19 19:13:36 ATTICUS kernel: [   36.487927] ftdi_sio: disagrees about version of symbol usb_kill_urb
Nov 19 19:13:36 ATTICUS kernel: [   36.487930] ftdi_sio: Unknown symbol usb_kill_urb
Nov 19 19:13:36 ATTICUS kernel: [   36.488009] ftdi_sio: Unknown symbol malloc_sizes
Nov 19 19:13:36 ATTICUS kernel: [   36.488067] ftdi_sio: disagrees about version of symbol usb_serial_probe
Nov 19 19:13:36 ATTICUS kernel: [   36.488070] ftdi_sio: Unknown symbol usb_serial_probe
Nov 19 19:13:36 ATTICUS kernel: [   36.488128] ftdi_sio: disagrees about version of symbol usb_serial_register
Nov 19 19:13:36 ATTICUS kernel: [   36.488131] ftdi_sio: Unknown symbol usb_serial_register
Nov 19 19:13:36 ATTICUS kernel: [   36.488164] ftdi_sio: disagrees about version of symbol usb_serial_deregister
Nov 19 19:13:36 ATTICUS kernel: [   36.488167] ftdi_sio: Unknown symbol usb_serial_deregister
```
:confused:

---

