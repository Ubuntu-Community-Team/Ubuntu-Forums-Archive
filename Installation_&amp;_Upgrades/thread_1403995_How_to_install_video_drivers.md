---
title: "How to install video drivers?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by joek71 on 2010-02-10
Hi guys

I am having a problem with video drivers if you look at my pictures you will see distortion can you please help me out.

Thanks

---

### Post by Cheezespread on 2010-02-10
have you completed the installation or is this distortion coming along while you install ?

If its after you have installed it , you could check the **hardware drivers** within System -> Administration. Whats the GPU in your machine. A bit more info on the machine would be great for any one trying to help you.

---

### Post by joek71 on 2010-02-10
Thank you for your help but when the distorted window comes up after i install it and it says updating and checking partion and it just stays there and i cant do anything else, i cant load video drivers or anything i left like that for 1 hour and nothing changes i was looking at my hard drive light and it was not blinking so that means no drive activity.

---

### Post by Mark Phelps on 2010-02-11
This is EXACTLY why the LiveCD option is provided in Ubuntu.

Instead of trying to force an install, boot to the CD and choose the LiveCD mode.  That will give you a good feel for how well Ubuntu detects your hardware and installs the proper drivers.

If you can get to a desktop in LiveCD mode, open a terminal and type "lspci | grep VGA".  That will list the PCI hardware devices on your machine and will attempt to find the video card/chip.

Post back here with the results of that.

---

