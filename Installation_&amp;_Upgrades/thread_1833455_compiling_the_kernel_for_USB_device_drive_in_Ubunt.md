---
title: "compiling the kernel for USB device drive in Ubuntu 11.04"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by balaqemu on 2011-08-26
I have tried to connecet a new USB device (ez430) to ubuntu11.04 which will create virtual serail port /dev/ttyACM0 . using this I can access the data .
 
I could see the virtual port has been up after I connected the device , but I cant write/read anything from the port . [COLOR=red]it gives input/output error[/COLOR] .
 
I tried to contact USB device vendor for this problem, they said I need to rebuild the kernal with some settings:
following is the suggestion gave by USB vendor:
[COLOR=darkgreen]**My guess is that it's a kernel configuration issue. The steps for compiling the kernel can be found here: [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)**[/COLOR]
[COLOR=darkgreen]**In the kernel config (step 2), make sure these are enabled:**[/COLOR]
[FONT=Monaco][SIZE=1][COLOR=darkgreen][B]Device Drivers --->
[*] USB support[/B][/COLOR][/SIZE][/FONT]
**[SIZE=1][FONT=Monaco][COLOR=darkgreen]<M> USB Modem (CDC ACM) support[/COLOR][/FONT][/SIZE]**
**[SIZE=1][FONT=Monaco][COLOR=darkgreen]<M> USB Serial Converter support --->[/COLOR][/FONT][/SIZE]**
**[SIZE=1][FONT=Monaco][COLOR=darkgreen]<M> USB TI 3410/5052 Serial Driver[/COLOR][/FONT][/SIZE]**

I dont want to rebuild the kernal , is there any other way to put this to the existing kernal with out buliding the kernal again ..?
if so , pls help with that .

---

