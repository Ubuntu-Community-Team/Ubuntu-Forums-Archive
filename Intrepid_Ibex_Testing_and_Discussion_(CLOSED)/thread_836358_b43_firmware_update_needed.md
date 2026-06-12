---
title: "b43 firmware update needed?"
date: 2008-06-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scradock on 2008-06-21
I am testing Intrepid, and have noticed in the last couple of days that there are messages during boot about DMA errors with my b43-phy0 start-up.
```
Jun 21 01:53:49 sc-laptop kernel: [   43.456011] Registered led device: b43-phy0::tx
Jun 21 01:53:49 sc-laptop kernel: [   43.457603] Registered led device: b43-phy0::rx
Jun 21 01:53:49 sc-laptop kernel: [   43.458040] Registered led device: b43-phy0::radio
Jun 21 01:53:49 sc-laptop kernel: [   43.458221] b43-phy0 ERROR: Fatal DMA error: 0x00001000, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Jun 21 01:53:49 sc-laptop kernel: [   43.458997] b43-phy0: Controller RESET (DMA error) ...
Jun 21 01:53:49 sc-laptop kernel: [   43.459095] b43-phy0 ERROR: Fatal DMA error: 0x00001000, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Jun 21 01:53:49 sc-laptop kernel: [   43.459841] b43-phy0: Controller RESET (DMA error) ...
```

In the kernellog there are also warnings that I should update my b43 firmware from linux-wireless.com. However, trying to begin the process with a wget leads to a failure, permission denied.

Has anyone else noticed this? 

Do I need to deal with it?
How do I deal with it? 
Isn't Jockey supposed to deal with this sort of thing?

---

### Post by CrazyGuy123 on 2008-06-21
I use the firmware available here:

[http://omattos.com/broadcom/](http://omattos.com/broadcom/)

And I don't see those errors.  I guess it's either firmware version dependant or motherboard chipset dependant.

---

### Post by scradock on 2008-06-21
> **CrazyGuy123 said:**
> I use the firmware available here:

[http://omattos.com/broadcom/](http://omattos.com/broadcom/)

And I don't see those errors.  I guess it's either firmware version dependant or motherboard chipset dependant.
Thanks for the suggestion.

I did in fact try using the linuxwireless files; the command-line instructions never did work, but I got around them by downloading the files manually and using the fwcutter that resulted to open up wl_apsta.o.

That got rid of the error messages, but left the broadcom 4306 unable to complete the connection through Network manager. NM listed the wireless networks correctly, but failed repeatedly to connect to them.

So I went back to the old firmware files, which connected correctly. Interestingly, the file list and *.fw file sizes are identical, though I don't know if the content is different, as they are binaries.

Does anyone know what is going on here? The error messages in kern.log say that the version 3 firmware should be replaced by version 4 before July 2008.....

---

### Post by Gina on 2008-06-21
I have bcm4306 (rev3) chipset on the card in this laptop and it works perfectly with the default firmware installed both in Hardy and Intrepid.  This is 32 bit though and I see yours is 64.  My 64bit desktop has a Ralink 2500 which works OOTB - I haven't got a Broadcom wireless to try on it.

---

### Post by scradock on 2008-06-22
Does anyone else get this warning?


```
Jun 22 01:31:36 sc-laptop kernel: [   66.092010] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
Jun 22 01:31:36 sc-laptop kernel: [   66.092010] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
Jun 22 01:31:36 sc-laptop kernel: [   66.092010] b43-phy0 warning: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
Jun 22 01:31:37 sc-laptop kernel: [   67.524010] Registered led device: b43-phy0::tx
Jun 22 01:31:37 sc-laptop kernel: [   67.524010] Registered led device: b43-phy0::rx
Jun 22 01:31:37 sc-laptop kernel: [   67.524010] Registered led device: b43-phy0::radio
Jun 22 01:31:37 sc-laptop kernel: [   67.524010] b43-phy0: Controller restarted
```

As you can see, the card does eventually get restarted, but it sometimes takes several tries, delaying start-up.

---

