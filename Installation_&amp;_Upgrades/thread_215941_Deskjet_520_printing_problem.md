---
title: "Deskjet 520 printing problem"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by culmore on 2006-07-14
I cannot yet print with my old reliable deskjet 520. I have spect some time reading old posts from the forums on this and quite a few hours with no joy.

I have tried various BIOS setting for my parallel port EPP ECP Normel bi-directional with no success. I tried downloading the packages from

HP Linux Imaging and Printing (HPLIP) i.e.
[http://hplip.sourceforge.net/install...tup/index.html](http://hplip.sourceforge.net/install...tup/index.html)

made no difference.


Here is the contents /etc/cups/printers.conf
# Printer configuration file for CUPS v1.2.1
# Written by cupsd on 2006-07-14 21:53
<Printer DeskJet-520>
Info
Location
DeviceURI parallel:/dev/lp0
State Idle
StateTime 1152910394
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

Note my printer is NOT automatically recognised when I try and install it using System->Admin->Printing. So I manually select the driver HP driver for the deskjet 520, (I have also tried some generic drivers). I also manually select lp1, as ubuntu does not detect any printer.

Here is the contents of

/etc/pnm2ppa.conf

# Sample configuration file
#
# This file will be automatically read upon startup if it is placed in
# /etc/pnm2ppa.conf
#
# uncomment entries by removing "#" to activate them.
#
#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
#
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command line
# option e.g., "-v 720".

version 710
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000


Can I set the version here to something other than the values shown??? I tried 520 but no luck.

Is my printer now to old to be supported? Surely not.

Many thanks for any help you can be.

---

### Post by culmore on 2006-07-14
PS I have the same problemn printing from my t41 thinkpad when I connect it directly to the laptops parrallel port.

---

### Post by indulis on 2006-07-14
Try making up a file in a text editor, or "print to file" on another system that has the printer working, transfer it to Ubuntu.

Then
*cat mytestfile >/dev/lp0*

Then try the same to /dev/lp1

You are bypasssing the printer subsystem and sending it direct to the parallel port by doing this.

Also, watch out for the fact that some laptops have the printer ports in the wrong order (dim memory of this!).

Luck!

Indulis

---

### Post by culmore on 2006-07-15
> **indulis said:**
> Try making up a file in a text editor, or "print to file" on another system that has the printer working, transfer it to Ubuntu.

Then
*cat mytestfile >/dev/lp0*

Then try the same to /dev/lp1

You are bypasssing the printer subsystem and sending it direct to the parallel port by doing this.

Also, watch out for the fact that some laptops have the printer ports in the wrong order (dim memory of this!).

Luck!

Indulis


Thanks for your reply Indulis. I tried your tip, I had to change the permission on /dev/lp0 (with a "sudo chmod a+rw /dev/lp0") but I got the same problem. The printer makes quite a bit of noise, it seems like it is going to print but then does not feed the paper through. Interestingly if I try the command a SECOND time nothing happens. So the printer is hung up still trying to "print the first file". I have to reboot to get it to make the noise again.


I checked for error messages in the following logs

-rw-r-----  1 root  adm    7249 2006-07-15 08:53 auth.log
-rw-r-----  1 root  adm  140070 2006-07-15 08:52 messages
-rw-r-----  1 root  adm    1200 2006-07-15 08:52 syslog
-rw-r-----  1 root  adm   10857 2006-07-15 08:52 user.log


but could see nothing appropiate to my problem. cups was down when I did this test btw.

I refuse to buy a new printer. This one has been faithful to me for 10 years.:)

---

### Post by culmore on 2006-07-15
oh my I justed realised what the problem is. The paper was not loaded properly. :oops: Now do I feel totally stupid. Sorry for wasting your time.

problem solved!

---

