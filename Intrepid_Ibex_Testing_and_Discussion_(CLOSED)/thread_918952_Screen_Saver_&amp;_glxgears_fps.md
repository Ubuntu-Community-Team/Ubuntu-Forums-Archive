---
title: "Screen Saver &amp; glxgears fps"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phidia on 2008-09-13
With latest updates running x86_64 ibex the screen saver starts (the monitor fades) and then it comes right back. I've noticed that it has worked in the past but it's been working off and on as the updates are applied.

I've also been keeping track of my fps output with glxgears and with each update (using the 173 nvidia driver installed through hardware drivers) it varies a great deal-sometimes good rates other times the fps drops to 50 or 60% of what it had been. This last series of updates has the fps in a downturn again.

I know that glxgears may not be that accurate but I'm not sure there should be wide swings with the same card. Is anyone seeing either of this behaviors and should I report it? Thanks

---

### Post by autocrosser on 2008-09-13
Yes--glxgears is just a advisory bit of info--and a toy to boot...I fire it up to get a general feel, but not much more.

There is a note on nVidia forums about performance with the newer drivers--you need to add a couple of things to your sessions>startup & your xorg.conf---link is:

[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

I can post the section in xorg.conf if you have any questions...

---

### Post by phidia on 2008-09-13
Thanks autocrosser and the link you provided appears to be specifically for The 177.67 NVIDIA BETA driver. 
I'm using the 173 driver as I noted in my post.

---

### Post by autocrosser on 2008-09-13
You might try the pixmap placement to see if there is any difference....and look thru nVidia forums for more information..

---

