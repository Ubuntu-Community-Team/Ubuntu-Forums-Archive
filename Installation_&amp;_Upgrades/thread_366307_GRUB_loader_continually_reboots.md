---
title: "GRUB loader continually reboots"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by ithyl on 2007-02-20
I was finally able to get Ubuntu server installed on my ancient K6/2-500 machine, but can't get past the GRUB loader.  I get to the part of the loader where it says:

GRUB Loading stage 1.5.

GRUB loading...

then if I don't ESC into the menu in time the loader simply reboots the machine.  Having never dealt with GRUB before I'm at a loss as to what options/commands I should try at the GRUB command line to try to get around this problem.  Any ideas?

---

### Post by confused57 on 2007-02-20
> **ithyl said:**
> I was finally able to get Ubuntu server installed on my ancient K6/2-500 machine, but can't get past the GRUB loader.  I get to the part of the loader where it says:

GRUB Loading stage 1.5.

GRUB loading...

then if I don't ESC into the menu in time the loader simply reboots the machine.  Having never dealt with GRUB before I'm at a loss as to what options/commands I should try at the GRUB command line to try to get around this problem.  Any ideas?

You'll need to use the alternate cd to install a server on older hardware:
[http://www.ubuntuforums.org/showthread.php?t=290903&page=2](http://www.ubuntuforums.org/showthread.php?t=290903&page=2)

---

### Post by ithyl on 2007-02-20
Thanks for the reply.  I'll try reinstalling using the alternate iso.

---

### Post by ithyl on 2007-02-21
Unfortunately, reinstalling didn't fix the problem.  I used the alternate install CD, installed using the "command line only" installation, but the symptoms are the same after trying to boot the system.

I get the messages:

GRUB Loading stage 1.5.

GRUB loading...

then the screen blanks out, I briefly see the message "Starting up...", and then the system reboots.

Any further ideas for what I can try to change/tweak?

---

### Post by confused57 on 2007-02-21
> **ithyl said:**
> Unfortunately, reinstalling didn't fix the problem.  I used the alternate install CD, installed using the "command line only" installation, but the symptoms are the same after trying to boot the system.

I get the messages:

GRUB Loading stage 1.5.

GRUB loading...

then the screen blanks out, I briefly see the message "Starting up...", and then the system reboots.

Any further ideas for what I can try to change/tweak?

If you used the Edgy alternate cd, you might try Dapper alternate...I haven't tried the Edgy alternate cd to install a server on my AMD k6-2, 500 Mhz pc, but the Dapper server install has worked OK...I know it's another download and don't know if it would help or not...if you did use the Dapper alternate, I don't really know what the problem might be.

---

