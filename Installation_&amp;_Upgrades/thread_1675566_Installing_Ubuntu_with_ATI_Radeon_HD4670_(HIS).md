---
title: "Installing Ubuntu with ATI Radeon HD4670 (HIS)"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by firewhizzle on 2011-01-25
This has been the absolute worst day ever as far as computer-related problems for me.

Here is how it went

**8:00 AM**
Boot up my Windows 7 box, download Ubuntu 10.10 i386 AND x64
Burn both to CD's, and x64 to USB key as backup

**9:00 AM**
Install from CD. Installation works fine, goes great, no problems.
Installation finishes, console appears telling me to remove media and press "Enter"
I remove the media, and press enter. Nothing happens - it just outputs some funny characters. A few minutes later it reboots.
After rebooting, the computer loads the starting console text for Ubuntu, says "Welcome to Ubuntu" in the console, then proceeds to go to a blank screen. The monitor is on, but just backlit black.

Also relevant, this shows up on the boot console log:
error: unexpectedly disconnected from boot status daemon
after the radeon_gem_ commands run

**5:24 PM**
Still trying different screens/combinations/keyboards/CDs&USBs, still getting the black screen of fail.

HELP!

_System specs_:
GFX: HIS Radeon HD 4670
CPU: AMD Athlon 64 3400+
RAM: 2ghz Kingston DDR2
HD: 120g westgate
CDROM: SONY something another
Monitors: 1280x1024(VGA) & 1920 x 1280(DVI&VGA) (tried both)

**Update**
I've found that I cannot boot into Live CD mode from CD or USB, it still does this:
error: unexpectedly disconnected from boot status daemon
after the radeon_gem_ commands run
Even when booting from live CD

Whats going on?

---

### Post by mörgæs on 2011-01-26
How does the machine behave in a live boot with 10.04, 32 bit?

---

### Post by sikander3786 on 2011-01-26
Welcome to the forums :-)

Here is what you need to do step by step.

Check the MD5SUM of your downloaded image to check it against any possible defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums don't match, download a new image and using a Torrent reduces the chances of damage.

If the image is ok, check your disc for any possible defects or burn a new disc at the _lowest_ possible speeds.

In order to gain access to the Main page options, you need to keep pressing any key as soon as the computer starts booting from the disc until you see the page which has an option to check the disc for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

For burning an ISO.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If you intend to install from a USB drive, I would recommend to use Unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

When you boot from the installation media (CD or USB), you might encounter a blank screen or a weird display problem and might need to enable the *nomodeset* parameter by pressing F6 at the Main Page. See here.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Keep us posted ;-)

---

### Post by othiena on 2011-03-09
it is not the CD as I have a CD from Ship-it and it is the same problem(currently running in safe graphics mode). From what I can tell it is a problem with the default ATI driver or the xorg.conf file. I had to use the on-board graphics card to install on my system. I tried installing ubuntu on several systems with my Radeon HD4670 card and I kept getting a blank screen.

---

### Post by mörgæs on 2011-03-09
With this card, Ubuntu 10.04 might be the best option.

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by stephanmir on 2011-03-26
I also purchased this video card and want to install it on my 10.10. 
 
We need a better response other than to back-track our ubuntu systems.
 
Someone else pls respond for a possible fix.

---

