---
title: "Install help please"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by GNUoob on 2010-09-14
Hi all, thanks for reading this

Situation:
I have an older laptop that boots from floppy or HD but not cdrom as it is dead.

Goal:
I would like to install 10.4 netbook on it via the command line after getting some basic shell loaded.

Hardware:
p3 1.1
512ram
DEAD cdrom
80 gig hdrive (replacement of original)
*** Does not boot via usb stick ***

Attempts:
I have removed the hdrive and via a usb cable attachment have put it on another machine. Then on that other machine started NBR (Netbook Remix) and told it to install to the usb drive using advanced methods and having the boot loader reside on other drive as well.

Results of attempts: the machine boots but gets then presents me with a video error as the screen suddenly fades to an all white screen as if it is being possessed. Its the video configuration but alas i am lost about how to correct this.

Restatement of Goal: I want 10.4 on this older machine through either through some sort of off machine install or floppy shell where i can then import/install the iso from a usb stick.

Thank you

---

### Post by sikander3786 on 2010-09-14
There is a simpler way of achieving what you want. You can use unetbootin for creating live usb and later on use it to install on your machine. See here.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Lateralis on 2010-09-14
The OP says he cannot boot from USB.  Does the Unetbootin require the machine to support booting from USB devices?  I've never used Unetbootin before so this is a genuine question. ;) 

@ OP

You could always try loading up Ubuntu without initialising X or the GDM - you can enter a multi-user mode with networking but without the graphical user interface.  Whether this will work or not I have no clue; it depends on what you mean by "it boots... but gives me a white screen".  

To do this you need to edit the kernel options in the grub menu.  If you are only booting Ubuntu (and I'm guessing you are) you will need to press and hold the shift key immediately after the BIOS has finished posting to screen.  The Grub menu should then appear.  Select one of the listed kernel entries and hit 'e'.  On the next page, highlight the *kernel* line and hit 'e' again.  At the end of the line append *3*.  You should, hopefully, boot into a fully functional shell without a graphical interface.  From the shell we can probably fix the problem, but I have to confess that at this moment in time I'm not sure.  I daresay someone else will be able to help. ;)

---

### Post by snowpine on 2010-09-14
Your machine is not a "netbook". Have you tried Xubuntu (Ubuntu for older hardware)?

---

### Post by GNUoob on 2010-09-15
> **sikander3786 said:**
> There is a simpler way of achieving what you want. You can use unetbootin for creating live usb and later on use it to install on your machine. See here.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Looked at page

The program either does...
1) creates a bootable usb stick OS
N/A no USB boot option
2) creates a mini linux version on the existing hardrive of same target machine, not other machine drive. This requires a workable winX version.
N/A in my situation

:/ thanks anyway

---

### Post by GNUoob on 2010-09-15
> **snowpine said:**
> Your machine is not a "netbook". Have you tried Xubuntu (Ubuntu for older hardware)?

I will try Xubuntu after i attempt..
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

...
Execute installation

The command-line version of Ubuntu is a sparse system, without any graphical elements. It's a text-only version of what lies underneath all the advanced graphical elements. It's also the starting point for a minimal installation.

To install a base system, boot from any Alternate CD and choose "Install a command-line system." It is exactly the same command-line system on Kubuntu/Xubuntu/Ubuntu Alternate CDs.

---

### Post by sikander3786 on 2010-09-16
There is a workaround for booting off a USB Drive even if the Bios doesn't support.

[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

