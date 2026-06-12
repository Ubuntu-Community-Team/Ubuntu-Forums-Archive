---
title: "Installation Problems Newbe"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by dborras on 2006-12-19
Can anyone help out?  
I&#8217;m a newbe to the Linux world and I&#8217;m try to load Ubuntu onto and older computer to use on a CNC mill.  I have downloaded the CD image of 6.10 i386 and checked its integrity.  I have striped down the computer I&#8217;m using to its basic components for ease of installation, it uses an AMD K6-2 / 400, with 256M of ram, an Nvida  GForce video card, Cdrom, and a Floppy drive all on and Asus motherboard..  The problem I&#8217;m having is that the installation starts fine with the Ubuntu logo and installing bar display, but after a short while the screen goes blank except for a blinking curser, but the cdrom is still running as if the application is still loading, but than everything goes blank and the computer locks up and stay that way.  I know that the compute is good because it was running Win 98 just fine.  Is there something I&#8217;m missing in the installation process?
:confused:

---

### Post by wpshooter on 2006-12-19
First did you run memtest to check the integrity of your memory ?

Did you check the CD integrity by running the verification function found on the initial Ubuntu boot screen menu or did you only check the sumcheck during burning ?

Do you currently have any other O/S on the computer ?

Are you trying to install from the DESKTOP (some times referred to as the live Ubuntu CD) ?

---

### Post by dborras on 2006-12-19
Thank you for the quick reply

I did memtest, sumcheck and CD integrity test and they all came out OK. Windows 98 is installed on the computer but I was going to reformat the HD if it gave me the option, and yes I was trying to install from the Ubuntu desktop, I thought I cover all of my bases and I even used a video card that was suggested for Linux.
 
I was looking through the forums and one posting said that sometime the system will go into sleep mode if there isn’t any mouse or keyboard activity.  They suggested moving the mouse once in a while to keep it from going into sleep mode, is that a possibility?

---

### Post by wpshooter on 2006-12-19
Get the **KILLDISK** program and **WIPE** your hard drive competely clean and then try installing it again from the DESKTOP CD, may want to try the safe video mode.

[http://www.killdisk.com/](http://www.killdisk.com/)

The amount of your memory may be a deficient to your installing with the DESKTOP version.

If that still does not work, then KILLDISK the drive again and then try installing from the ALTERNATE CD version.

No, I don't think the sleep mode is a problem here.  I think the program is set initially to go into sleep monitor after about 10 to 20 minutes of inactivity.  I don't think that is the source of your problems.

Good luck.

---

### Post by kevinatkins on 2006-12-19
Hi,

I think you might be a bit short on RAM to install from the Live CD, so I'd suggest trying the Alternate install CD, as mentioned by wpshooter. With your system specs, Ubuntu should run fine once you've got it installed - for reference, I've got it installed on an old K6 450Mhz laptop, with 192MB of RAM. I had to use the Alternate CD for that.

---

### Post by Sef on 2006-12-19
> The amount of your memory may be a deficient to your installing with the DESKTOP version.

dborras' computer has 256 mb ram, so it has enough to run Ubuntu, though the processor is on the low side.

 > try installing from the ALTERNATE CD version.

Agreed.  Often the alternate cd version will work were the Live CD version install fails.

---

### Post by dborras on 2006-12-19
Thank you for all of the help I will download the alt. CD and try again.  I have some extra sticks of memory that I can put in too.

---

