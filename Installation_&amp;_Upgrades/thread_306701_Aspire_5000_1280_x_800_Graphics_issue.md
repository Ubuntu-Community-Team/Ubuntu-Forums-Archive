---
title: "Aspire 5000 1280 x 800 Graphics issue"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by James Maxwell on 2006-11-25
I am very new to this Linux malarkey so please bare with me.

I have an Aspire 5000 machine installed with Ubuntu. I have got past the installing simple applications stage and am now into the getting rid of small irritants stage. This leads me nicely into my question, my monitor will support 1280 x 800 screen resolution at 24-bit, how can i get my version of Ubuntu to recognize this? Please please please Jim can you fix it for me to have fully functional graphics? 

I have had a scan through the forums and have found a post that means nothing to me so I thought I would post the question here for the first attempt of me using this forum. The graphics processor as far as i can determine is an SisM760GX. If anyone can point me vaguely in the direction of someone who has written about this issue, is such a way that someone like me can read and understand it, so it does not look like complete twaddle, this would be grand.

James Maxwell

---

### Post by Cyraxzz on 2006-11-27
First, install the correct video card driver. The Aspire 5000 has a Nvidia card as a default right? I would recommend  [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38") to install the Nvidia drivers. There is a way for adding your desired screen resolution with the Nvidia driver, read the man pages for nvidia-xconfig for further info on that.  

There is another way to add screen resolutions, simply type in the following command in your terminal ```
dpkg-reconfigure xserver-xorg
``` at the end it will ask about resolutions.

I have always found it easier to edit the xorg.conf file myself. BACK IT UP FIRST!

---

### Post by James Maxwell on 2006-11-30
Thank you I will try this later when I get back to the offending PC seems nice and simple.

Thank you for your time

Regards

James

---

