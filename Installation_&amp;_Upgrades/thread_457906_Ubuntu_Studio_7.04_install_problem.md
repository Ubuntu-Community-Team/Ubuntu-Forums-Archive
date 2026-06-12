---
title: "Ubuntu Studio 7.04 install problem"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by kryptonite307 on 2007-05-29
Hi,

I'm attempting to install Ubuntu 7.04 on a Dell Dimension 2400 and post the keyboard configuration step, it get's a "Failed to copy file from CD-ROM"  error message.  I've burnt several copies of the ISO with no luck...  Every other Distro works just fine ????

Anyone experience the same or have a workaround ?

Cheers,
Krypto

---

### Post by blacksadness on 2007-05-29
check the integrity of the iso, it could be that the download broke, download the .md5 file from the mirror where you downloaded the iso and do an md5 check (md5sum -c filename.iso)
hope it helps

---

### Post by btesec on 2007-05-29
> **kryptonite307 said:**
> Hi,

I'm attempting to install Ubuntu 7.04 on a Dell Dimension 2400 and post the keyboard configuration step, it get's a "Failed to copy file from CD-ROM"  error message.  I've burnt several copies of the ISO with no luck...  Every other Distro works just fine ????

Anyone experience the same or have a workaround ?

Cheers,
Krypto


Hello

I had the same experience.  when I got to the Software selection screen  I did not select any of the options (Audio, Graphics, Plugins, Video) and was able to complete the installation successfully.  However the problem I find out is that the DVD Drive is not able to read the dvd when I try to install the software after I load Ubuntu studio.  I tried to read a normal CD instead of DVD and it reads the files on the CD.  The error i get when clicking on the CD/DVD icon is "unable to mount the selected volume" and under more details it says "mount: special device /dev/scd0 not exist".

I am guessing it may be some software/driver that needs config since the drive can only read the normal CD-R the Version is HL-DT-ST RW/DVD GCC-44808 can anyone help.  

Can anyone help

****One thing I can say is that the bare Ubuntu Studio runs better and faster that vista on a DAEWOO PC P IV 2 GHZ 256 RAM it installed all the hardware.

thanks

---

