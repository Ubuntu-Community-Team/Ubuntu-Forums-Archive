---
title: "Can't install hp laserjet 1300 on dapper Live CD"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by polybius on 2007-03-27
Am trying to install hp laserjet 1300 on dapper 6.06.1 Live CD.  I'm doing this to see if hardware works before real installation of the OS.

I'm doing this on two different machines, one a Dell Dimension XPS 500 Pentium III with 256MB ram, the other another Dell of about the same vintage.  Both machines have hp laserjet 1300 attached via parallel cable (not USB).  Printers work on both machines with different versions of Linux (one uses Redhat 9.0, the other Suse 9.1), so I know the hardware and connections are ok.

I have the identical problem on both machines.  When I try to install the printer with the printer tool (3 step process), I double click New Printer, it sees the printer and correctly identifies it as hp laserjet 1300, it then wants me to identify the printer (step 2) which I do, load recommended driver, and then I finish up.  But no printer icon appears in the list of printers.

In /var/log/cups/access_log I see the following:

"POST /admin/HTTP/1.1" 401 473 CUPS-Add-Modify-Printer sucessful-ok
"POST /admin/HTTP/1.1" 401 473 CUPS-Add-Modify-Printer server-error-internal-error

in /var/log/cups/error_log I see:

CUPS-Add-Modify-Printer: Unauthorized

I haven't been able to find any reference to this problem in the forums.  

Any help would be greatly appreciated!

Thanks, Polybius

---

### Post by polybius on 2007-03-27
Correction:  the second message in /var/log/cups/access_log should read:

"POST /admin/HTTP/1.1" 200 473 CUPS-Add-Modify-Printer server-error-internal-error

---

