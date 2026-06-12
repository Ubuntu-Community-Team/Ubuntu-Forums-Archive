---
title: "hibernate/suspend no working on DELL optiplex 755"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Ralph Boland on 2008-02-06
I just got dual monitors to work on my Dell optiplex 755 following the instruction on:

             [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

My graphics card is a:

             256MB ATI Radeon 2400 XT, dual Monitor DVI or VGA (TV out) full height.

Following instructions I installed the ATI Catalist 8.1 driver executing, among other
commands, the command:

                apt-get install xorg-driver-fglrx

The documention says that the new driver would also fix my problems with
suspend/hibernate not working.  (Originally hibernate worked but the screen was
drawn in very low resolution after restarting after a hibernate. I never tried suspend.)

Now, however, neither hibernate nor suspend work.  
With hibernate the computer only partially shuts down.  
The two screens show a blinking underline in the top right.
as if a tty waiting for input.  Any input typed is ignored though.
 I am forced to do a hard shutdown.
Suspend seems to suspend but I am unable to restart.
Typing of keys is ignored as is pressing the start button.
Again,  I am forced to do a hard shutdown.

Any ideas on how to fix this much appreciated.

Thanks

Ralph Boland

---

