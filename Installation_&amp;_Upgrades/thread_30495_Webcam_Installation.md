---
title: "Webcam Installation?"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by Goober on 2005-04-28
Hello,

I have a Webcame, and it worked on XP.  How, if at all, can i get it to work on Linux?

It is a Creative Webcam Live!, and just plugs into the USB port.

Thanks,

Goober

---

### Post by tUrtleAE86 on 2005-04-28
Well, I'm not sure if your webcam chipset is supported. You have to figure out what chipset your camera has.

And use the following links to determine if there is support for them. It worked for my Creative Webcam NX Ultra, by the way.  :) 

[http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html)
[http://spca50x.sourceforge.net/spca50x.php](http://spca50x.sourceforge.net/spca50x.php)

---

### Post by Goober on 2005-04-29
Hmm, I didn't find it on either of those 2 sites.

It is the [Creative Webcam Live!](http://www.creative.com/products/product.asp?category=218&subcategory=219&product=10412), and I cannot find any other markings to indicate which driver I need, which suggests to me that a driver has yet to come out.

I have found out the following informtion about it though, which could possibly be useful:

Vendor ID: 0X041e
Product ID: 0X4036
Bridge: Zc0301P
Sensor: Hv7131c
Driver: spca5xx
Stream: jpeg

---

### Post by heimo on 2005-04-29
Hopefully this helps.

In README file 
[http://mxhaard.free.fr/spca50x/Download/spca5xx-20050419.tar.gz]("http://mxhaard.free.fr/spca50x/Download/spca5xx-20050419.tar.gz")

```

What cameras are supported?
===========================

Currently, the following cameras are supported by this driver:

	   Vendor ID  Device ID  Support Summary
	    ---------  ---------  ---------------
  {USB_DEVICE (0x041e, 0x4036)},		/* Creative Live ! */

```

---

### Post by InnerFIRE on 2006-02-14
I need that file, i have a creative live webcam too. I checked that site listed above and its not there. Webpage is down... other suggestions?

---

### Post by Sigudian on 2006-06-21
sure... thanks for leting me know what driver i need !!!! =D> 

i googled it and found it here

[http://mxhaard.free.fr/download.html]("http://mxhaard.free.fr/download.html")

---

