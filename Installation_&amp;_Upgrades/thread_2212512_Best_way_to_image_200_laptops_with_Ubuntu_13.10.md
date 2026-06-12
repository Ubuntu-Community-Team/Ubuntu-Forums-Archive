---
title: "Best way to image 200 laptops with Ubuntu 13.10"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by william26 on 2014-03-21
We have a test laptop setup exactly like we want. I thought it would be easy to create an image and push them to the other laptops.  I was completely wrong.  
What are the recommended ways of pushing an image to 200 plastic wrapped laptops loaded with windows 8.1?

Here's what I've tried so far:
1) Clonezilla - failed, graphical anomolies, dead end downloads, incomplete or incorrect instructions
2) DRBL - instructions apparently written for 8.10.  PPA's outdated and unavailable.  Folder structure completely changed from tutorials.  Pretty much a dead end.

Here's what I would like:
1) A server that pushes the image when a computer is connected and booted using PXE

Here's what I might have to do:
1) Create an 'image' on a USB and install ubuntu via USB sticks ( cannot create the USB image, right now ).

Here's what I really do not want to have to do:
1)  Load Ubuntu manually, configure system ( x200 )

Thank you for your genius!

---

### Post by ubfan1 on 2014-03-21
Have you checked out [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)  ?
Just a few questions for more complete info:
  1)Are you trying to set up dual boot with Windows?
  2)Are all the machines identical hardware (as far as you know)?  Of course, you really won't know that until you examine each one, because even the same model may get build with different hardware, depends on the vendor.

---

### Post by eric13 on 2014-03-21
Just a point of consideration: 13.10 is only supported until 2014-07, while the upcoming 14.04 LTS until 2019. It might be worth it to wait a few weeks before the rollout !

---

