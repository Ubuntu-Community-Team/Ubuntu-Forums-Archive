---
title: "Printer not detected--non-network"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by Citizen Bleys on 2010-08-12
I'm running* Lucid on a desktop with a printer connected directly via USB.  I originally got an error message that just said "/usr/lib/cups/backend/hp failed", but in trying to fix it myself, I've made matters much, much worse.

The big mistake was to try reinstalling the printer from System/Administration/Printing.  I removed it, thereby losing the long and unmemorable URI that was originally there, and now I can't get it back.  lsusb shows no printers connected whatsoever.

The printer, for the record, is an HP Photosmart 7660, and yes HPLIP is installed.  Every forum post I've seen so far was either single-post threads marked "solved" with no solution posted or "Hey dude install HPLIP" followed by "Great it worked."  It didn't work for me.

```

hh@hh-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 004 Device 002: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0644:0200 TEAC Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 012: ID 04b8:0119 Seiko Epson Corp. Perfection 4490 Photo
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
hh@hh-desktop:~$ hp-info -i

HP Linux Imaging and Printing System (ver. 3.10.2)
Device Information Utility ver. 5.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No device selected/specified or that supports this functionality.

```

And my favorite part:
```

hh@hh-desktop:~$ hp-check -rt

HP Linux Imaging and Printing System (ver. 3.10.2)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux hh-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

(elided...)

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

(elided...)

---------------
| USER GROUPS |
---------------

hh adm dialout cdrom plugdev lpadmin admin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

No errors or warnings.

Done.
hh@hh-desktop:~$ 

```

Yes, the user account is a member of the group "lp".  The first time I ran hp-check it told me that, so I added the user and re-ran it.  Same complaint.

I'd like to manually add the URI, but to do that I'd have to know what the deuce it is.  I remember it started with hp:// and someone on launchpad solved it by "changing the URI to usb" (full text of the solution), but hp://WHAT? or usb://WHAT?  lsusb isn't helping.

hplip-gui just says "no devices found."

Of course, the basics -- yes, the printer is plugged in and turned on.  So is the computer.  Kernel is 2.6.32-24-generic.  It prints fine in Windows, but there are slines coming over who will want to use the computer and would most likely infect it with a mountain of viruses and spyware large enough to perturb the orbit of Jupiter, so booting into Windows is not an option until at least next Monday.

*read: setting up for someone else who actually prints in the 21st century

---

