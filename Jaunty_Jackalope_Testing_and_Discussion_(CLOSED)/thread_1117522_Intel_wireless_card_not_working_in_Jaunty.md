---
title: "Intel wireless card not working in Jaunty"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mike565sd on 2009-04-06
I just did a clean install of the Jaunty beta, and my wireless card has stopped working.  Under Intrepid my wireless worked fine, but now Network Manager doesn't recognise any wireless devices.  When I run dmesg, this is the output:

[    9.188581] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    9.188585] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    9.188702] ipw2200 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.189788] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    9.189832] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[    9.431259] ipw2200: Unable to load ucode: -62
[    9.431274] ipw2200: Unable to load firmware: -62
[    9.431278] ipw2200: failed to register network device
[    9.436332] ipw2200 0000:02:03.0: PCI INT A disabled
[    9.436347] ipw2200: probe of 0000:02:03.0 failed with error -5

I have been searching for hours trying to fix this, but no luck.  I am relatively new to Linux but I consider myself to be pretty computer literate.  Any help would be appreciated and I apologize if this has been answered before. Thanks.

---

### Post by alex88 on 2009-04-06
You have to download the firmware from here:

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

remember to use the version for your drivers, then unpack the tarball and copy all files into /lib/firmware

---

### Post by mike565sd on 2009-04-06
Alex88,

Thanks for the reply. The FW was already in the /lib/firmware folder, but I went ahead and downloaded it from the website you provided and replaced the existing FW with the new one, but still no wireless.  dmesg gives the same results as before.

EDIT:

I just rebooted into my windows partition to verify that my card was still working (it was), and when I rebooted into Jaunty my wireless was working. Thanks again for the help, and hopefully I won't have any other problems.

---

### Post by alex88 on 2009-04-06
No problem, please add [SOLVED] into topic title.

---

