---
title: "Ubuntu 11.10 installation from USB, black screen"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by subhadip_sky on 2011-10-14
Hi, I am successfully running Ubuntu 11.04 both on my HP 520 laptop and on my desktop computer. I downloaded the 11.10 desktop i386 cd image and created live USB using Unetbootin, live usb creator from pendrivelinux and the default start up disk creator in Ubuntu each but both my laptop and my desktop won't boot from the USB, I don't know why. After a few marching dots under "Ubuntu", my computer will be presented with a black screen and with the USB light not blinking, I can tell it's not reading from the USB either.

I can boot 11.04 both on my laptop and my desktop with the same USB and it also works with 10.04. Any help will be appreciated. Thank you.

---

### Post by sikander3786 on 2011-10-14
Try the classic old fix, 'nomodeset':

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

If that doesn't work, please let us know your hardware specs, importantly RAM and graphics card.

---

### Post by subhadip_sky on 2011-10-14
> **sikander3786 said:**
> Try the classic old fix, 'nomodeset':

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

If that doesn't work, please let us know your hardware specs, importantly RAM and graphics card.


Thank you for your kind reply. I tried that already, didn't work. Here's the specification for my desktop computer

CPU Intel P IV 1.6 GHz Core 2D
Motherboard Intel 945
HDD Seagate 80 Gb Sata
Memory DDR 512 mb + 1024 mb

---

### Post by sikander3786 on 2011-10-15
> **subhadip_sky said:**
> Thank you for your kind reply. I tried that already, didn't work. Here's the specification for my desktop computer

CPU Intel P IV 1.6 GHz Core 2D
Motherboard Intel 945
HDD Seagate 80 Gb Sata
Memory DDR 512 mb + 1024 mb
So, you most probably have got an Intel graphics chip as you didn't specify one individually.

Did you try other parameters like 'i915.modeset=1' or 'i915.modeset=0' as mentioned near the bottom of that post?

And if it still doesn't work, I would recommend to create a new USB, this time following this tutorial:

[http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create](http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create)

It would present you with the standard boot options/menus/pages that come with Ubuntu. Then try inserting some other boot parameters by pressing F6 at the boot options page as mentioned here:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

Any of the top 3 options in the F6 menu might work for you.

---

### Post by subhadip_sky on 2011-10-22
I am extremely sorry, it was my fault. There was something wrong with the installation file, I don't know I just downloaded it from Bit torrent. So I used the installation file my friend had downloaded from the official Ubuntu site and the installation went exceptionally smooth.

---

