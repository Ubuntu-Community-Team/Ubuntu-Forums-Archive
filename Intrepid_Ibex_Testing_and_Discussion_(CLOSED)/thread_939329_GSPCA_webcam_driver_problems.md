---
title: "GSPCA webcam driver problems?"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Dremora on 2008-10-05
Pretty much just what it says.

Intrepid has problems with my Creative Webcam Instant.

Cheese can't detect it at all, and aMSN gets the resolution totally wrong and only shows about a quarter of the image it should.

Anyone else having this?

---

### Post by UbuWu on 2008-10-06
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267522](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267522)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270618](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270618)

---

### Post by loell on 2008-10-06
yep, we are in the transition phase, since spca5xx v2 is already in the kernel.

[http://www.nabble.com/-Bug-43308--libv4l,-NEW:-gspca-v2-requires-libv4l-and-the-use-of-LD_PRELOAD-to-get-an-image-from-a-logitech-webcam-td19220545.html]("http://www.nabble.com/-Bug-43308--libv4l,-NEW:-gspca-v2-requires-libv4l-and-the-use-of-LD_PRELOAD-to-get-an-image-from-a-logitech-webcam-td19220545.html")

concisely the workaround is

install libv4l, [https://launchpad.net/~stemp/+archive]("https://launchpad.net/~stemp/+archive")

preload it, then hopefully the webcam will work.

---

### Post by UbuWu on 2008-10-06
Loell, are you going to get libv4l in the official archives as well?

---

### Post by loell on 2008-10-06
> **UbuWu said:**
> Loell, are you going to get libv4l in the official archives as well?

libv4l didn't made it to intrepid :( , so we'll just gonna have to depend on a third party repo for now.

---

### Post by UbuWu on 2008-10-06
> **loell said:**
> libv4l didn't made it to intrepid :( , so we'll just gonna have to depend on a third party repo for now.

Well I think there is very good reason for a freeze exception for it and that will probably be granted. But there only needs to be somebody doing the packaging.

---

### Post by loell on 2008-10-06
> **UbuWu said:**
> Well I think there is very good reason for a freeze exception for it and that will probably be granted. But there only needs to be somebody doing the packaging.

yes, actually that's a good point, even though it only addresses gspca based webcams which is by the way majority of them, putting libv4l in the official repo is one less step of the workaround.

[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

---

### Post by AmyRose on 2008-10-07
> **loell said:**
> yep, we are in the transition phase, since spca5xx v2 is already in the kernel.

[http://www.nabble.com/-Bug-43308--libv4l,-NEW:-gspca-v2-requires-libv4l-and-the-use-of-LD_PRELOAD-to-get-an-image-from-a-logitech-webcam-td19220545.html]("http://www.nabble.com/-Bug-43308--libv4l,-NEW:-gspca-v2-requires-libv4l-and-the-use-of-LD_PRELOAD-to-get-an-image-from-a-logitech-webcam-td19220545.html")

concisely the workaround is

install libv4l, [https://launchpad.net/~stemp/+archive]("https://launchpad.net/~stemp/+archive")

preload it, then hopefully the webcam will work.
Thank you so much for the workaround! I was pulling my hair out trying to compile the driver from the [http://mxhaard.free.fr](http://mxhaard.free.fr), with no success. The driver included with Intrepid works like a charm now!

Had to read the directions to find out what lib to preload though.

---

### Post by loell on 2008-10-07
> **AmyRose said:**
> Thank you so much for the workaround! I was pulling my hair out trying to compile the driver from the [http://mxhaard.free.fr](http://mxhaard.free.fr), with no success. The driver included with Intrepid works like a charm now!

Had to read the directions to find out what lib to preload though.

O hai Amy :)

i'm glad it worked.. :D

yeah, i forgot to mention the preloading command, thanks ;)

> export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so 

---

