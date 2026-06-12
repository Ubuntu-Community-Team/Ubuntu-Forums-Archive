---
title: "Bad graphics in Try mode"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by bernie2 on 2013-10-17
I have a nice PC at work, too nice; it has an Nvidia FX 5500 video card, which has been an issue lately.   Installs have always worked in past using the Nouveau driver.  Before departing the non-gnome3 versions of Ubuntu and Mint I used to be able to install.

I am really looking forwards to coming back to Ubuntu threw Gnome Ubuntu.

My problem is that when I boot from the 13.10 disk and use the Try option, I get freaked out graphics.  You can tell that X is running and that under the black and yellow flashing the desk is there, it does not look like over driving.   TTY is OK.  Nothing of note in the Xorg log file.

As per pined item at top of list: Mint 15 looked like it might work, but soon lost it. Lubuntu works fine, Fedora 18/19 install Nouveau and work.

The graphics are fine during the install, up to the point the I select the try button.  I tried this on my old test install laptop with an Nvidia card and had no problem.  It doesn’t look like the try button even does anything but remove the buttons.  So I don’t see why my desk changes when the button it pushed.

I am down loading Gnome-U 13.04 now and will try that, but I am looking for feedback on how to proceed.

I guess I could go ahead and install then, boot to single user, install Ndivia, fix booting, etc, etc.  

But I sure was looking forwards to getting away from all that and getting back to work.   One of the big draws of Ubuntu for me is that it usually updates and works and additional software installs work without user intervention.

How should I proceed?  Need more/better info?

Thanks!

---

### Post by Bashing-om on 2013-10-17
bernie2;  Hi !

Have your tried the "nomodeset" boot option, and when at the desk top -> Additional Drivers utility to install the recommended driver ?

Boot the liveDVD, soon as bios screen clears depress and hold the shift key -> language screen, escape key to accept the default; -> boot options screen -> f6 key; arrow down to the preset option "nomodeset", space or enter to accept and then the escape key to exit -> Enter key to continue the boot process.

[INDENT][INDENT]worth a try
[/INDENT][/INDENT]

---

### Post by bernie2 on 2013-10-18
That did the trick, Thanks!

I am the proud owner of a shiny new Ubuntu system, with all the non-main stream tweaks I need for work.

---

### Post by Bashing-om on 2013-10-18
bernie2; Outstanding !

Welcome to our world of open source. May your experiences be as good as mine.

Please mark this thread as solved - 1st post -> thread tools and;

[INDENT][INDENT]I will read you next time [/INDENT][/INDENT]

---

