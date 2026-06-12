---
title: "Installing Ubuntu 6.06 Server: No Bootable CD support."
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by Corvis on 2007-01-02
Hi, I've been trying to get an old Compaq to boot from CD so i can install Ubuntu 6.06 Server.  Its a Pentium I and does not support booting from CD as far as i can tell.  I originally couldn't even get into the BIOS, apparently the Compaq needed some special floppy disks to load the BIOS.  Once i got in i did not see the option for CD-ROM.  I then tried Smart Boot Manager, but again once that loaded I didn't see the option for CD, only hard disk and floppy.  I hope I didn't carelessly over look something in the process, most of this is new to me.  I then acquire a floppy disk from where i work that is supposed to let me choose boot from CD.  I get home today and try it, it gets me to the command prompt and i can switch over to the CD.  


now I'm stuck.  I was wondering if someone here could tell me what file on the CD starts the Install process.  This way i can just use the command prompt to start th install. Or am I asking the wrong question?  

Any help is appreciated.

---

### Post by ingo on 2007-01-03
Hi,

it sounds like your start-up floppy got you into dos (was it a win98 start-up?). Unfortunately this will not do you any good, as dos cannot do a lot with what is on the cd. You really need to be able to boot from the cd itself as far as I am aware...

---

### Post by az on 2007-01-03
There is a tool called smart boot manager.  On the cd, there is an install folder.  The sbm binary is there - in windows, you can use rawrite to write it to a floppy.  Boot the floppy and then sbm will (should) allow you to boot from the cdrom, if it can see it.

Read the readme in that folder...

---

### Post by Corvis on 2007-01-10
Smart Boot manager didn't work for me, there was no CD-ROM option to pick to boot from.  So i went and got Bootable CD Loader as suggested in another post in these forums.  and again no luck. here is the error

> IDE/ATAPI CD-ROM Device Driver Version 1.11     18:37:57    04/25/95
CD-ROM drive #0 found on 170h port master device

Cannot boot from CD. press any key to boot from HDD or ESCape to reboot...

I talked to some one at work and he mentioned that Linux may not support some of the older Pentiums.  Turns out I have a Pentium MMX.  someone else mentioned that i might want to just try a new CD-ROM drive.

I'm thinking about trying to locate a newer "junker" to put Ubuntu Server on, unless someone has some suggestions.

yet again any help is much appreciated, and thank you ingo and azz for the input

---

### Post by K.Mandla on 2007-01-10
You might try this 

[http://www.ubuntuforums.org/showthread.php?t=316093](http://www.ubuntuforums.org/showthread.php?t=316093)

Or this

[http://instlux.sourceforge.net/](http://instlux.sourceforge.net/)

I haven't tried either of those, although I have heard good things about them.

---

### Post by ingo on 2007-01-13
if your problem is getting the laptop to boot from cd you might want to google make and model - you are bound to find something useful. It really is most unusual not to be able to boot from cd (unless your laptop is older than 10 years).

---

