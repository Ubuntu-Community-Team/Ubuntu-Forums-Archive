---
title: "The new kernel?"
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ELD on 2008-07-15
With the new kernel now out will it be in inrepid? The webcam drivers will be a welcome addition!

---

### Post by loell on 2008-07-15
yes the kernel will be on intrepid, though  UVC webcam drivers on the kernel? i was under the impression that ubuntu has UVC module(s) by default?

---

### Post by ELD on 2008-07-15
This is specific new changes in the newest kernel, read up on it here:
[http://kernelnewbies.org/Linux_2_6_26](http://kernelnewbies.org/Linux_2_6_26)

Quote:
> 
1.3. Improved webcam support

2.6.26 includes a driver that supports video input devices compliant with the USB Video Class specification. This means lots of currently manufactured webcams, and probably most of the future ones (commit)


---

### Post by loell on 2008-07-15
base on [http://kernelnewbies.org/Linux_2_6_26]("http://kernelnewbies.org/Linux_2_6_26")

the specific should be here

[http://linux-uvc.berlios.de/#devices]("http://linux-uvc.berlios.de/#devices")

so i was asking if anybody could confirm that if  UVC comes with ubuntu by default, cause if it did, maybe users may not really see the improvements on webcam support.

---

### Post by ELD on 2008-07-15
> **loell said:**
> 
[http://linux-uvc.berlios.de/#devices]("http://linux-uvc.berlios.de/#devices")


Will devices with a green tick in that page work out-of-box in ubuntu?

---

### Post by loell on 2008-07-15
yes, it will work out of the box in intrepid for sure. :)

add those with an already compatibe webcams 
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")

---

### Post by GTvulse on 2008-07-15
> **loell said:**
> base on [http://kernelnewbies.org/Linux_2_6_26](http://kernelnewbies.org/Linux_2_6_26)

the specific should be here

[http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices)

so i was asking if anybody could confirm that if  UVC comes with ubuntu by default, cause if it did, maybe users may not really see the improvements on webcam support.

Yes, the UVC modules have been included in the ubuntu-modules packages at least for a year now.

---

### Post by loell on 2008-07-15
in that case users will see little or no change with webcam support in ubuntu.

---

