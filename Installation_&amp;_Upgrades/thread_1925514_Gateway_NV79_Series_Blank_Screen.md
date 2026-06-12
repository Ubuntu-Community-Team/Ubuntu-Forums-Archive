---
title: "Gateway NV79 Series Blank Screen"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by DWade on 2012-02-14
The Gateway laptop NV79 Series with Intel graphics and with the I5 processor, seems to have a problem with Ubuntu, or rather the newer Kernels, in that the graphics when you try to install Ubuntu, comes to a blank screen.  I am not sure of 10.10, I never tried it but I did 11.04 and 11.10..

I still have not heard of anyone re-instating the safe mode graphics into the installation CD / ISO.  I download it twice to check.

Is 12.04 going to be the same?

---

### Post by DWade on 2012-03-31
Again this is a Gateway NV7922u with I5 Processor and Intell HD Graphics

The Setup CD / ISO Needs to have a VGA Graphics mode.  Like the older CD / ISO had.

I also need to put here that the Partition Magic CD /ISO does the same thing, and the lower Video mode does not work on it's CD.

---

### Post by DWade on 2012-04-09
WELL.  I have the beta2 12.04 Desktop burned will boot up and see what it does.

If it goes to blank screen or unable to make modification will post back will all problems.

---

### Post by DWade on 2012-04-09
The problem is in the video selection at boot up.

It seems that with intel graphics, Ubuntu can not decide which graphics to use so it chooses the HDMI output instead of the LCD TFT screen of the Laptop.  

I booted up the desktop install CD.  it ran to the first part where it says Ubuntu then went blank or a black screen. The disk ran and booted up but nothing on the screen, just the same as with versions 11.04, 11.10 and now 12.04.  I do not know if that was case with 10.10 because I was planing on just using the LTS version.  

I had the same problem with Parted Magic on this laptop, so that means it has something to do with the video detection process and is linked to the kernel and not your settings, or your linux builds.  

Since, I now have LCD HDMI TV and I have a HDMI cord, I decided to try and just plug it and see what it displayed.  the Ubuntu screen showed, but was not in the right video mode.

I rebooted and watched the TV screen, as all funtions of the CD ran. When it got to the video detection part it now picked the correct video for the Laptop and reset the TV to about half size.

So, that means laptops like mine, the Gateway NV79 series with the built in intel HD video [or at least with I5 cpu] and maybe even some others, may need to use a HDMI TV for to first boot with installation CD.

I almost tried this eariler, but did not.  This laptop has VGA output and a HDMI output. Since I do not have access right now to a VGA monitor, I have no idea if it will work that way or not.

So all the post with blank screens or even the back light problem may be related to this.

---

