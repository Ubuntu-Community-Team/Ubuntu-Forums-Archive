---
title: "Can't run installer with nVidia 6100"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by bruce_g on 2007-08-25
I ran feisty from the AMD-64 DVD, but could use only the 800x600 screen resolution.  The only other option was 640x480, and that didn't work.

I tried to run the installer, but it seems to have a minimum window height greater than 600 pixels.  This makes a custom installation impossible.

I tried installing the nVidia display driver by activating desktop effects, but it requires a reboot, and after a reboot, I have to install the driver again and reboot again...

Any suggestions?

-Bruce

---

### Post by meznaric on 2007-08-25
When you install the driver try only to reboot X rather than the entire system. Press CTRL+ALT+BAKCSPACE when you want to do that. 

Alternatively, you could use the non-graphic installer ...

---

### Post by bruce_g on 2007-08-25
meznaric,

Thanks for the reply.

Command line sys install?  Ughh. Isn't this going to be fun.

Any idea where I can find documentation?

-Bruce

---

### Post by Pumalite on 2007-08-25
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by bruce_g on 2007-08-25
Pumalite, 

Thanks.  I found a reference to the command line installer on the alternate install CD at the link you gave.  Not much there for instruction, but at least I know where to start.

Meznaric,

Thanks again.  I didn't know the ctrl-alt-bksp trick.  It let me partially install the nVidia driver, but I lost my mouse pointer.  I got through the install with the help of the Tab key, clues from tooltips, and some random clicking.  The partially installed nVidia driver confused the Ubuntu installer, and now X won't run.  It looks like I'll be trying the command line install after all.

-Bruce

---

