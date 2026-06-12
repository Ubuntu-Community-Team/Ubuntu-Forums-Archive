---
title: "Install Error: Out of Disk Space"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by stacey_hawkins on 2006-11-24
[FONT="Verdana"]Hey folks, 

I have an older Compaq Presario Notebook that I picked up for $50.  It is my intention to install Ubuntu 6.10 on it.  I burned the iso to disk using imgburn as outlined in the instructions page and am now trying to install.  I am receiving the following two errors:

[I]GDM could not write a new authorization entry to disk.  Possibly out of disk space.  Error:  No space left on disk.

Could not start the X server (your graphical environment) due to some internal error.  Please contact your system administrator or check your syslog to diagnose.  In the meantime, this display will be disabled.  Please restart GDM when the problem is corrected.[/I]

I have tried to use the 'safe graphics' option from the boot menu with the same result.  

I would consider myself technically inclined, however, I am a Linux Newb.  I am not going to partition the hd or anything, so if there is a way around this that involves whiping windows first, I am down.

Compaq Presario Notebook 1200
Pentium III
797 MHz
124 MB of Ram
Currently has WIN XP w/ SP2 installed

Thanks Everyone, Stacey :mrgreen:[/FONT]

---

### Post by ThrobbingBrain66 on 2006-11-24
it sounds to me like youre using the live cd.  the live cd should only be used with more than 192mb of memory.  i would suggest downloading the alternate install cd which is all text based.  this may take care of your problem

---

### Post by stacey_hawkins on 2006-11-24
Thank you, I am downloading now.  Stace

---

### Post by wpshooter on 2006-11-24
Stacey:

It may actually be a lack of memory problem BUT in case it is a lack of hard drive space problem you can cure that by WIPING the drive with this program.  Also, make sure you always check the integrity of the Ubuntu CD by running the verification check found on the initial Ubuntu boot screen menu.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by stacey_hawkins on 2006-11-24
The alternate install disk worked without incident!  I will keep killdisk in mind for future endeavors.  Thank you!  Stacey

---

