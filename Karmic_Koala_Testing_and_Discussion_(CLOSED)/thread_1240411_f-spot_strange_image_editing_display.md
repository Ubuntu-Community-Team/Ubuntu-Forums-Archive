---
title: "f-spot strange image editing display"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keithpeter on 2009-08-14
Hello All

Under Jaunty I used f-spot to gather the images from the SD card from my digital camera. Worked fine except sometimes failed to save to the right place when I just popped my SD card in.

Under Karmic (updated today), f-spot recognises my SD card fine and imports 100s of images no problem, thumbnails shown the right size and so on. When clicking on an image to edit it within f-spot, I get the display shown in the screen grab - the large edit image is broken into three slabs, and the bottom two slabs are transposed. This happens both with and without fancy desktop effects and persists after re-boot.  

I'm using an Asus with nvidia integrated graphics, restricted drivers, and this behaviour represents a change from Jaunty. Anyone else seeing similar? No bugs filed against f-spot and nothing in this forum.

---

### Post by keithpeter on 2009-08-15
The issue arises with 8Mb images only loaded from my Fujifilm snapshot camera. The 3264 by 2448 images display oddly in 'edit' view, the 4Mb 2304 by 1728 images display normally as do large jpg files downloaded from the Web.

If I load an image on the SD card into GIMP and save a copy it diplays OK in f-spot.

Anyone else seeing anything like this in Karmic's f-spot? The Jaunty version was fine with images from the same camera.

---

### Post by Jay_Bee on 2009-08-15
I see this sometimes but only when I'm adjusting the zoom level.

---

### Post by keithpeter on 2009-08-16
Hello

Thanks, I get the effect all the time after a brief flash of the correct image when clicking the 'edit' button.

It only seems to affect 8 megapixel images from the digital camera. 4 megapixel images are fine, and large images from the Web are fine. I've filed a bug as it is a change from Jaunty where f-spot worked ok most of the time.

---

