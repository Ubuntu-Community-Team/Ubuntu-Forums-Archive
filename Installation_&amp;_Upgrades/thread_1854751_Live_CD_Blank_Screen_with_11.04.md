---
title: "Live CD Blank Screen with 11.04"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by DWade on 2011-10-05
I placed Ubuntu 11.04 on a usb drive and tried it for Live mode.

When you select try Ubuntu it starts out then shifts to a blank screen. The light flash, the sounds come up as though it has loaded but..  Blank screen

This is a Gateway NV7922u Laptop 
Ubuntu 10.04 works fine on the usb if you choose F4.  How that worked I don't know but it does.

The USB Universal-USB-Installer-1.8.6.4, does not allow for mode changes or advanced options.  The menu says it does but it will not.

I burned a CD and booted up same thing as the USB, next book I got it to go to grub menu and choosed advanced set up F6, noacpi, and it then booted with the screen working.

---

### Post by Rubi1200 on 2011-10-05
What graphics card do you have installed on the machine in question?

---

### Post by DWade on 2011-10-13
What does Gateway NV7922u mean???

I am sorry whatever it comes with!

I haven't looked it up lately I believe the standard intel HD graphic for laptop I5 core processor. 

But the problems is.  The installation CD's or ISO no longer have safe graphics mode on them..  That what I was pointing out.

Also the USB program does not copy over mode changes or changes that can be done in the boot menu.

And I will bet the new 11.10 does the same thing.  wana bet?

---

### Post by foresthill on 2011-10-14
See this thread:

[http://ubuntuforums.org/showthread.php?t=1741556](http://ubuntuforums.org/showthread.php?t=1741556)

---

### Post by DWade on 2011-11-19
Didn't really help.

The problem is the monitor not working in a good mode here's how!!!

but after checking out the alternate CD, I found it used this switch VGA=788 in the boot line.

Pressing the ESC key constantly while booting either 11.04 or 11.10 get you to main grub menu. 

Select F6, then ESC to get out of menu, a boot options line appears,  and then using arrow key move the courser back next to ubuntu.seed and insert  vga=788 with a space after so it looks like this – /ubuntu.seed vga=788 boot=casper …  then hit enter.  you'll boot up in to try ubuntu unless you used an arrow key before the F  key.

There used to be a selection in the F4 menu for Vga safe if there was monitor problems, but that's been removed, and it need to be put back into the menu.  The new amd and in my case intel HD don't always work with the standard or default of the CD choosing. oh and this is now 18months old. 

This [http://support.gateway.com/s/notebook/2009/gateway/nv/NV79/NV79sp2.shtml]("http://support.gateway.com/s/notebook/2009/gateway/nv/NV79/NV79sp2.shtml") is the laptop support page.  It's the I5 Processor an this Intel® Graphics Media Accelerator HD7 (Intel® GMA HD), 128 MB of dedicated system memory, Microsoft® DirectX® 10..

So if anybody else has the blank screen problem or slash no backlite use this. I am using 11.10 now as I write this.

I will address the giant phone program later.

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

