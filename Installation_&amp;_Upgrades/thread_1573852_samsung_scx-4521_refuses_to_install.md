---
title: "samsung scx-4521 refuses to install"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by hodad on 2010-09-13
I've been trying for days to get this printer to be recognized by 10.04. I've tried seemingly every possible combination of methods from "HOWTO Install Samsung Unified Printer Driver" to no avail (though I have learned a good bit during the process). Presently, the (partial) output of the printer error log file is as follows:

************************************************** *****************

D [10/Sep/2010:13:42:29 -0600] [cups-deviced] Found device "usb://Samsung/SCX-4x21%20Series"...
D [10/Sep/2010:13:42:29 -0600] [cups-deviced] PID 1824 (usb) exited with no errors.
D [10/Sep/2010:13:42:29 -0600] [cups-deviced] PID 1838 (hpfax) exited with no errors.
D [10/Sep/2010:13:42:31 -0600] [cups-deviced] PID 1829 (snmp) exited with no errors.
I [10/Sep/2010:13:42:44 -0600] Saving job cache file "/var/cache/cups/job.cache"...
I [10/Sep/2010:13:42:44 -0600] Saving subscriptions.conf...
D [10/Sep/2010:13:42:44 -0600] cupsdSetBusyState: Active clients
D [10/Sep/2010:13:42:44 -0600] cupsdSetBusyState: Not busy
D [10/Sep/2010:13:42:44 -0600] PID 1822 (/usr/lib/cups/daemon/cups-deviced) exited with no errors.
D [10/Sep/2010:13:42:44 -0600] cupsdReadClient: 27 WAITING Closing on EOF
D [10/Sep/2010:13:42:44 -0600] cupsdCloseClient: 27
D [10/Sep/2010:13:42:44 -0600] cupsdAcceptClient: 22 from localhost (Domain)
D [10/Sep/2010:13:42:44 -0600] cupsdReadClient: 22 POST / HTTP/1.1
D [10/Sep/2010:13:42:44 -0600] cupsdSetBusyState: Active clients
D [10/Sep/2010:13:42:44 -0600] cupsdAuthorize: No authentication data provided.
D [10/Sep/2010:13:42:44 -0600] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [10/Sep/2010:13:42:44 -0600] Get-Printer-Attributes ipp://localhost/printers/scx4x21
D [10/Sep/2010:13:42:44 -0600] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/scx4x21) from localhost
D [10/Sep/2010:13:42:44 -0600] cupsdSetBusyState: Not busy
D [10/Sep/2010:13:42:47 -0600] cupsdAcceptClient: 27 from localhost (Domain)
D [10/Sep/2010:13:42:47 -0600] Report: clients=15
D [10/Sep/2010:13:42:47 -0600] Report: jobs=39
D [10/Sep/2010:13:42:47 -0600] Report: jobs-active=3
D [10/Sep/2010:13:42:47 -0600] Report: printers=2
D [10/Sep/2010:13:42:47 -0600] Report: printers-implicit=0
D [10/Sep/2010:13:42:47 -0600] Report: stringpool-string-count=959
D [10/Sep/2010:13:42:47 -0600] Report: stringpool-alloc-bytes=8400
D [10/Sep/2010:13:42:47 -0600] Report: stringpool-total-bytes=20560
D [10/Sep/2010:13:42:47 -0600] cupsdReadClient: 27 WAITING Closing on EOF
D [10/Sep/2010:13:42:47 -0600] cupsdCloseClient: 27
D [10/Sep/2010:13:42:47 -0600] cupsdReadClient: 24 POST / HTTP/1.1
D [10/Sep/2010:13:42:47 -0600] cupsdSetBusyState: Active clients
D [10/Sep/2010:13:42:47 -0600] cupsdAuthorize: Authorized as dave using PeerCred
D [10/Sep/2010:13:42:47 -0600] cupsdReadClient: 24 1.1 Get-Jobs 1
D [10/Sep/2010:13:42:47 -0600] Get-Jobs ipp://localhost/printers/
D [10/Sep/2010:13:42:47 -0600] [Job 44] Loading attributes...
D [10/Sep/2010:13:42:47 -0600] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [10/Sep/2010:13:42:47 -0600] cupsdSetBusyState: Not busy
D [10/Sep/2010:13:42:47 -0600] cupsdReadClient: 24 POST / HTTP/1.1
D [10/Sep/2010:13:42:47 -0600] cupsdSetBusyState: Active clients
D [10/Sep/2010:13:42:47 -0600] cupsdAuthorize: Authorized as dave using PeerCred
D [10/Sep/2010:13:42:47 -0600] cupsdReadClient: 24 1.1 Get-Jobs 1
D [10/Sep/2010:13:42:47 -0600] Get-Jobs ipp://localhost/printers/
D [10/Sep/2010:13:42:47 -0600] [Job 1] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 1] Unable to open job control file "/var/spool/cups/c00001" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 2] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 2] Unable to open job control file "/var/spool/cups/c00002" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 3] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 3] Unable to open job control file "/var/spool/cups/c00003" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 4] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 4] Unable to open job control file "/var/spool/cups/c00004" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 5] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 5] Unable to open job control file "/var/spool/cups/c00005" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 6] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 6] Unable to open job control file "/var/spool/cups/c00006" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 7] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 7] Unable to open job control file "/var/spool/cups/c00007" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 8] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 8] Unable to open job control file "/var/spool/cups/c00008" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 9] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 9] Unable to open job control file "/var/spool/cups/c00009" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 10] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 10] Unable to open job control file "/var/spool/cups/c00010" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 11] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 11] Unable to open job control file "/var/spool/cups/c00011" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 16] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 16] Unable to open job control file "/var/spool/cups/c00016" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 17] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 17] Unable to open job control file "/var/spool/cups/c00017" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 18] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 18] Unable to open job control file "/var/spool/cups/c00018" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 19] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 19] Unable to open job control file "/var/spool/cups/c00019" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 20] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 20] Unable to open job control file "/var/spool/cups/c00020" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 21] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 21] Unable to open job control file "/var/spool/cups/c00021" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 22] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 22] Unable to open job control file "/var/spool/cups/c00022" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 23] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 23] Unable to open job control file "/var/spool/cups/c00023" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 24] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 24] Unable to open job control file "/var/spool/cups/c00024" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 25] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 25] Unable to open job control file "/var/spool/cups/c00025" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 26] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 26] Unable to open job control file "/var/spool/cups/c00026" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 27] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 27] Unable to open job control file "/var/spool/cups/c00027" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 28] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 28] Unable to open job control file "/var/spool/cups/c00028" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 30] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 30] Unable to open job control file "/var/spool/cups/c00030" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 31] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 31] Unable to open job control file "/var/spool/cups/c00031" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 33] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 33] Unable to open job control file "/var/spool/cups/c00033" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] [Job 40] Loading attributes...
E [10/Sep/2010:13:42:47 -0600] [Job 40] Unable to open job control file "/var/spool/cups/c00040" - No such file or directory!
D [10/Sep/2010:13:42:47 -0600] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [10/Sep/2010:13:42:47 -0600] cupsdSetBusyState: Not busy
D [10/Sep/2010:13:42:47 -0600] cupsdAcceptClient: 27 from localhost (Domain)
D [10/Sep/2010:13:42:47 -0600] cupsdReadClient: 27 GET /admin/log/error_log HTTP/1.1
D [10/Sep/2010:13:42:47 -0600] cupsdSetBusyState: Active clients
D [10/Sep/2010:13:42:47 -0600] cupsdAuthorize: No authentication data provided.

************************************************** ***************

I've uninstalled and reiinstalled the Samsung Configurator numerous times.

Any help would be greatly appreciated.[http://ubuntuforums.org/images/icons/icon8.gif](http://ubuntuforums.org/images/icons/icon8.gif)

Thanks

---

### Post by yahs on 2010-09-13
I can't solve your various error messages but I have had success with the Unified Driver installation using a SCX4100 and SCX4500w
Something which has worked for me is to try a new installation of Ubuntu which you can do as follows.
Run a live Ubuntu session by booting from your Ubuntu 10.04 CD.
Attach your printer with a USB cable.
Once the desktop appears, download the unified Driver from Samsung, extract and change to the /cdroot/Linux directory.
Open a terminal and type sudo ./install.sh
The samsung GUI installer will appear. Just follow the prompts -  add yourself to lp group and disable parallel printing. When the installer gets to 95/96% the installation pauses while it sets up the Configurator on the Desktop, but then completes.
If you now open the Samsung Configurator you will hopefully see entries for a printer and a scanner.
If this works I would then close the live session and do a complete re-installation

---

### Post by hodad on 2010-09-15
Thanks for the idea -- that's an interesting and creative technique!  I'll keep it filed away...

Turns out that I managed to get the printer working by going thru the whole process outlined in the Samsung printer..." thread one more time.  I think I'm good to go now, but will try your method if something ever gets hosed in my setup and I wouldn't be surprised if that happens!).

):P

---

