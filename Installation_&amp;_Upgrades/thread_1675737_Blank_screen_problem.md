---
title: "Blank screen problem"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by TipsyDever on 2011-01-26
I just made an desktop installation CD (from the .iso) that can also be used to try it out without installing.  

It boots and works fine as far as giving me the screen where I can choose to either run it or install it ... but when I try to run it I end up on a blank screen (except for the mouse pointer, which i can move around).

I don't think it's a graphics card/driver issue, as the previous page looked normal, and it's a 7 year old HP/compaq laptop so nothing obscure or cutting edge ... plus i can see the mouse.  The graphics card is an "ATI Radeon IGP 320M"

Could this just be a problem with trying it out, which might go away if I choose to install it, or could there be some hardware issue?

BTW  I also ran the option to check the files on the CD, which said it was fine.

---

### Post by sikander3786 on 2011-01-26
Welcome to the forums :-)

This is a 7 year old Laptop so I wonder, how much RAM is there inside it? If it is less than 512MB, you might need to look for a light-weight Ubuntu variant such as Lubuntu.

[http://lubuntu.org](http://lubuntu.org)

You might also want to try the nomodeset parameter from F6 options at the Main page. See here for details.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by TipsyDever on 2011-01-26
Thanks ... I have 768Mb Ram so that's not it.

In fact, The nomodeset thing seems to work ... except (in try-out mode) firefox just shows a blank window (though I can right-click and view source).  Do some apps not work with the nomodeset thing?  Do I need to install an updated driver or something?

---

### Post by sikander3786 on 2011-01-26
nomodeset shouldn't cause a problem to Firefox at all. After the installation completes, you can install the graphics drivers from System > Administration > Hardware Drivers. Firefox issue _should_ resolve itself after installation completes and you boot from the Hard disk.

You'll need to punch in nomodeset at the Grub menu after you reboot your system after completion of install. See the above linked page for more details.

---

