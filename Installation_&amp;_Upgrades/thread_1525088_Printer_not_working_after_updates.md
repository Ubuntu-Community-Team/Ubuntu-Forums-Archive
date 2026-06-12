---
title: "Printer not working after updates"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by cm8000000 on 2010-07-06
Hi there, I'm running Ubuntu 10.04, and after installing the recommended updates yesterday, my printer, which was working perfectly, no longer works. I tried reinstalling it by downloading the appropriate driver, but it still won't work. Here is the error log:

D [06/Jul/2010:07:55:26 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:26 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:55:26 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:26 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:26 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [06/Jul/2010:07:55:26 -0400] Get-Jobs ipp://localhost/printers/
D [06/Jul/2010:07:55:26 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Jul/2010:07:55:26 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:26 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:55:26 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:26 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:26 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [06/Jul/2010:07:55:26 -0400] Get-Jobs ipp://localhost/printers/
D [06/Jul/2010:07:55:26 -0400] [Job 132] Loading attributes...
D [06/Jul/2010:07:55:26 -0400] [Job 134] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 135] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 136] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 137] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 138] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 139] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 140] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 141] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 142] Loading attributes...
E [06/Jul/2010:07:55:27 -0400] [Job 142] Unable to queue job for destination "PSC_750"!
D [06/Jul/2010:07:55:27 -0400] [Job 143] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] [Job 144] Loading attributes...
E [06/Jul/2010:07:55:27 -0400] [Job 144] Unable to queue job for destination "PSC_750"!
D [06/Jul/2010:07:55:27 -0400] [Job 145] Loading attributes...
E [06/Jul/2010:07:55:27 -0400] [Job 145] Unable to queue job for destination "PSC_750"!
D [06/Jul/2010:07:55:27 -0400] [Job 146] Loading attributes...
D [06/Jul/2010:07:55:27 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Jul/2010:07:55:27 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:27 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:55:27 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:27 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:27 -0400] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [06/Jul/2010:07:55:27 -0400] Create-Printer-Subscription /
D [06/Jul/2010:07:55:27 -0400] cupsdCreateSubscription(con=0x2273fa90(12), uri="/")
D [06/Jul/2010:07:55:27 -0400] pullmethod="ippget"
D [06/Jul/2010:07:55:27 -0400] notify-lease-duration=86400
D [06/Jul/2010:07:55:27 -0400] notify-time-interval=0
D [06/Jul/2010:07:55:27 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [06/Jul/2010:07:55:27 -0400] Added subscription 66 for server
D [06/Jul/2010:07:55:27 -0400] cupsdMarkDirty(-----S)
D [06/Jul/2010:07:55:27 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [06/Jul/2010:07:55:27 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:28 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:55:28 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:28 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [06/Jul/2010:07:55:28 -0400] Get-Notifications /
D [06/Jul/2010:07:55:28 -0400] cupsdIsAuthorized: requesting-user-name="christine"
D [06/Jul/2010:07:55:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Jul/2010:07:55:28 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 14 POST /printers/HP-PSC-750 HTTP/1.1
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 14 1.1 Print-Job 1
D [06/Jul/2010:07:55:30 -0400] Print-Job ipp://localhost/printers/HP-PSC-750
D [06/Jul/2010:07:55:30 -0400] [Job ???] Auto-typing file...
I [06/Jul/2010:07:55:30 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [06/Jul/2010:07:55:30 -0400] cupsdMarkDirty(----J-)
D [06/Jul/2010:07:55:30 -0400] add_job: requesting-user-name="christine"
D [06/Jul/2010:07:55:30 -0400] Adding default job-sheets values "none,none"...
I [06/Jul/2010:07:55:30 -0400] [Job 149] Adding start banner page "none".
D [06/Jul/2010:07:55:30 -0400] cupsdMarkDirty(-----S)
D [06/Jul/2010:07:55:30 -0400] cupsdMarkDirty(----J-)
I [06/Jul/2010:07:55:30 -0400] [Job 149] Adding end banner page "none".
I [06/Jul/2010:07:55:30 -0400] [Job 149] File of type application/vnd.cups-banner queued by "christine".
D [06/Jul/2010:07:55:30 -0400] [Job 149] hold_until=0
I [06/Jul/2010:07:55:30 -0400] [Job 149] Queued on "HP-PSC-750" by "christine".
D [06/Jul/2010:07:55:30 -0400] cupsdMarkDirty(----J-)
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdMarkDirty(-----S)
D [06/Jul/2010:07:55:30 -0400] [Job 149] job-sheets=none,none
D [06/Jul/2010:07:55:30 -0400] [Job 149] argv[0]="HP-PSC-750"
D [06/Jul/2010:07:55:30 -0400] [Job 149] argv[1]="149"
D [06/Jul/2010:07:55:30 -0400] [Job 149] argv[2]="christine"
D [06/Jul/2010:07:55:30 -0400] [Job 149] argv[3]="Test Page"
D [06/Jul/2010:07:55:30 -0400] [Job 149] argv[4]="1"
D [06/Jul/2010:07:55:30 -0400] [Job 149] argv[5]="job-uuid=urn:uuid:fcbe43d1-74e1-3848-546b-44ff47740427 job-originating-host-name=localhost"
D [06/Jul/2010:07:55:30 -0400] [Job 149] argv[6]="/var/spool/cups/d00149-001"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[8]="HOME=/var/spool/cups/tmp"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[10]="SERVER_ADMIN=root@christine-desktop"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[11]="SOFTWARE=CUPS/1.4.3"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[13]="TZ=America/Toronto"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[14]="USER=root"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[17]="IPP_PORT=631"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[18]="CHARSET=utf-8"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[19]="LANG=en_CA.UTF-8"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[20]="PPD=/etc/cups/ppd/HP-PSC-750.ppd"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[21]="RIP_MAX_CACHE=834802k"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[23]="DEVICE_URI=hp:/usb/PSC_750?serial=MY27KD12C1WB"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[24]="PRINTER_INFO=HP PSC 750"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[25]="PRINTER_LOCATION=christine-desktop"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[26]="PRINTER=HP-PSC-750"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[27]="CUPS_FILETYPE=document"
D [06/Jul/2010:07:55:30 -0400] [Job 149] envp[28]="FINAL_CONTENT_TYPE=printer/HP-PSC-750"
I [06/Jul/2010:07:55:30 -0400] [Job 149] Started filter /usr/lib/cups/filter/bannertops (PID 1898)
I [06/Jul/2010:07:55:30 -0400] [Job 149] Started filter /usr/lib/cups/filter/pstopdf (PID 1899)
I [06/Jul/2010:07:55:30 -0400] [Job 149] Started filter /usr/lib/cups/filter/pdftopdf (PID 1900)
E [06/Jul/2010:07:55:30 -0400] Unable to execute /usr/lib/cups/filter/foomatic-rip-hplip: No such file or directory
E [06/Jul/2010:07:55:30 -0400] [Job 149] Unable to start filter "foomatic-rip-hplip" - Success.
D [06/Jul/2010:07:55:30 -0400] cupsdMarkDirty(-----S)
E [06/Jul/2010:07:55:30 -0400] [Job 149] Stopping job because the scheduler could not execute a filter.
D [06/Jul/2010:07:55:30 -0400] cupsdMarkDirty(----J-)
D [06/Jul/2010:07:55:30 -0400] cupsdMarkDirty(-----S)
D [06/Jul/2010:07:55:30 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-PSC-750) from localhost
D [06/Jul/2010:07:55:30 -0400] PID 1898 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15.
D [06/Jul/2010:07:55:30 -0400] PID 1899 (/usr/lib/cups/filter/pstopdf) was terminated normally with signal 15.
D [06/Jul/2010:07:55:30 -0400] PID 1900 (/usr/lib/cups/filter/pdftopdf) was terminated normally with signal 15.
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 15 1.1 Get-Notifications 1
D [06/Jul/2010:07:55:30 -0400] Get-Notifications /
D [06/Jul/2010:07:55:30 -0400] cupsdIsAuthorized: requesting-user-name="christine"
D [06/Jul/2010:07:55:30 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [06/Jul/2010:07:55:30 -0400] Get-Job-Attributes ipp://localhost/jobs/149
D [06/Jul/2010:07:55:30 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/149) from localhost
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [06/Jul/2010:07:55:30 -0400] Get-Printer-Attributes ipp://christine-desktop:631/printers/HP-PSC-750
D [06/Jul/2010:07:55:30 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://christine-desktop:631/printers/HP-PSC-750) from localhost
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [06/Jul/2010:07:55:30 -0400] Get-Job-Attributes ipp://localhost/jobs/149
D [06/Jul/2010:07:55:30 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/149) from localhost
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [06/Jul/2010:07:55:30 -0400] Get-Notifications /
D [06/Jul/2010:07:55:30 -0400] cupsdIsAuthorized: requesting-user-name="christine"
D [06/Jul/2010:07:55:30 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [06/Jul/2010:07:55:30 -0400] cupsdCloseClient: 16
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [06/Jul/2010:07:55:30 -0400] Get-Printer-Attributes ipp://christine-desktop:631/printers/HP-PSC-750
D [06/Jul/2010:07:55:30 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://christine-desktop:631/printers/HP-PSC-750) from localhost
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:30 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [06/Jul/2010:07:55:30 -0400] Get-Job-Attributes ipp://localhost/jobs/149
D [06/Jul/2010:07:55:30 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/149) from localhost
D [06/Jul/2010:07:55:30 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:31 -0400] [Job 149] Unloading...
D [06/Jul/2010:07:55:36 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:36 -0400] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [06/Jul/2010:07:55:36 -0400] Get-Job-Attributes ipp://localhost/jobs/149
D [06/Jul/2010:07:55:36 -0400] [Job 149] Loading attributes...
D [06/Jul/2010:07:55:36 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/149) from localhost
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:36 -0400] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [06/Jul/2010:07:55:36 -0400] Cancel-Subscription /
D [06/Jul/2010:07:55:36 -0400] cupsdIsAuthorized: requesting-user-name="christine"
D [06/Jul/2010:07:55:36 -0400] cupsdMarkDirty(-----S)
D [06/Jul/2010:07:55:36 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [06/Jul/2010:07:55:36 -0400] cupsdReadClient: 16 GET /admin/log/error_log HTTP/1.1
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdReadClient: 16 PUT /admin/conf/cupsd.conf HTTP/1.1
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:55:36 -0400] cupsdIsAuthorized: username=""
D [06/Jul/2010:07:55:36 -0400] cupsdSendHeader: 16 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [06/Jul/2010:07:55:36 -0400] cupsdCloseClient: 16
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [06/Jul/2010:07:55:36 -0400] cupsdReadClient: 16 PUT /admin/conf/cupsd.conf HTTP/1.1
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdAuthorize: Authorized as christine using PeerCred
D [06/Jul/2010:07:55:36 -0400] cupsdIsAuthorized: username="christine"
I [06/Jul/2010:07:55:36 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:55:36 -0400] cupsdCloseClient: 12
D [06/Jul/2010:07:55:36 -0400] cupsdCloseClient: 14
D [06/Jul/2010:07:55:36 -0400] cupsdCloseClient: 15
D [06/Jul/2010:07:55:36 -0400] cupsdCloseClient: 17
D [06/Jul/2010:07:55:36 -0400] cupsdCloseClient: 16
D [06/Jul/2010:07:55:36 -0400] cupsdDeregisterPrinter(p=0x226de678(HP-PSC-750), removeit=1)
I [06/Jul/2010:07:55:36 -0400] Saving printers.conf...
I [06/Jul/2010:07:55:36 -0400] Generating printcap /var/run/cups/printcap...
I [06/Jul/2010:07:55:36 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [06/Jul/2010:07:55:36 -0400] Saving subscriptions.conf...
D [06/Jul/2010:07:55:36 -0400] cupsdSetBusyState: Not busy
I [06/Jul/2010:07:55:36 -0400] cupsdDefaultRIPCacheSize: 834802k
E [06/Jul/2010:07:55:36 -0400] Filter "/usr/lib/cups/filter/foomatic-rip-hplip" for printer "HP-PSC-750" not available: No such file or directory
E [06/Jul/2010:07:55:36 -0400] Filter "/usr/lib/cups/filter/foomatic-rip-hplip" for printer "HP-PSC-750" not available: No such file or directory
E [06/Jul/2010:07:57:07 -0400] Filter "/usr/lib/cups/filter/foomatic-rip-hplip" for printer "HP-PSC-750" not available: No such file or directory
E [06/Jul/2010:07:57:07 -0400] Filter "/usr/lib/cups/filter/foomatic-rip-hplip" for printer "HP-PSC-750" not available: No such file or directory
I [06/Jul/2010:07:57:12 -0400] Listening to 0.0.0.0:631 (IPv4)
I [06/Jul/2010:07:57:12 -0400] Listening to :::631 (IPv6)
I [06/Jul/2010:07:57:12 -0400] Listening to /var/run/cups/cups.sock (Domain)
I [06/Jul/2010:07:57:12 -0400] Remote access is enabled.
D [06/Jul/2010:07:57:12 -0400] Added auto ServerAlias christine-desktop
I [06/Jul/2010:07:57:12 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [06/Jul/2010:07:57:12 -0400] Using default TempDir of /var/spool/cups/tmp...
I [06/Jul/2010:07:57:12 -0400] Configured for up to 100 clients.
I [06/Jul/2010:07:57:12 -0400] Allowing up to 100 client connections per host.
I [06/Jul/2010:07:57:12 -0400] Using policy "default" as the default!
D [06/Jul/2010:07:57:12 -0400] cupsdMarkDirty(P-----)
D [06/Jul/2010:07:57:12 -0400] cupsdSetBusyState: Dirty files
D [06/Jul/2010:07:57:12 -0400] load_ppd: Loading /var/cache/cups/HP-PSC-750.ipp...
D [06/Jul/2010:07:57:12 -0400] cupsdMarkDirty(P-----)
E [06/Jul/2010:07:57:12 -0400] Filter "/usr/lib/cups/filter/foomatic-rip-hplip" for printer "HP-PSC-750" not available: No such file or directory
E [06/Jul/2010:07:57:12 -0400] Filter "/usr/lib/cups/filter/foomatic-rip-hplip" for printer "HP-PSC-750" not available: No such file or directory
D [06/Jul/2010:07:57:12 -0400] cupsdRegisterPrinter(p=0x226de678(HP-PSC-750))
D [06/Jul/2010:07:57:12 -0400] cupsdMarkDirty(---p--)
I [06/Jul/2010:07:57:12 -0400] Partial reload complete.
I [06/Jul/2010:07:57:12 -0400] Listening to 0.0.0.0:631 on fd 5...
I [06/Jul/2010:07:57:12 -0400] Listening to :::631 on fd 7...
I [06/Jul/2010:07:57:12 -0400] Listening to /var/run/cups/cups.sock on fd 8...
I [06/Jul/2010:07:57:12 -0400] Resuming new connection processing...
D [06/Jul/2010:07:57:12 -0400] cupsdRegisterPrinter(p=0x226de678(HP-PSC-750))
D [06/Jul/2010:07:57:12 -0400] Discarding unused server-restarted event...
D [06/Jul/2010:07:57:13 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [06/Jul/2010:07:57:13 -0400] Report: clients=1
D [06/Jul/2010:07:57:13 -0400] Report: jobs=17
D [06/Jul/2010:07:57:13 -0400] Report: jobs-active=1
D [06/Jul/2010:07:57:13 -0400] Report: printers=1
D [06/Jul/2010:07:57:13 -0400] Report: printers-implicit=0
D [06/Jul/2010:07:57:13 -0400] Report: stringpool-string-count=3166
D [06/Jul/2010:07:57:13 -0400] Report: stringpool-alloc-bytes=9272
D [06/Jul/2010:07:57:13 -0400] Report: stringpool-total-bytes=69304
I [06/Jul/2010:07:57:43 -0400] Saving printers.conf...
I [06/Jul/2010:07:57:43 -0400] Generating printcap /var/run/cups/printcap...
D [06/Jul/2010:07:57:43 -0400] cupsdSetBusyState: Not busy
D [06/Jul/2010:07:57:53 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:57:53 -0400] cupsdSetBusyState: Active clients
D [06/Jul/2010:07:57:53 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:57:53 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [06/Jul/2010:07:57:53 -0400] Get-Jobs ipp://localhost/printers/
D [06/Jul/2010:07:57:53 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Jul/2010:07:57:53 -0400] cupsdSetBusyState: Not busy
D [06/Jul/2010:07:57:53 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Jul/2010:07:57:53 -0400] cupsdSetBusyState: Active clients
D [06/Jul/2010:07:57:53 -0400] cupsdAuthorize: No authentication data provided.
D [06/Jul/2010:07:57:53 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [06/Jul/2010:07:57:53 -0400] Get-Jobs ipp://localhost/printers/
D [06/Jul/2010:07:57:53 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Jul/2010:07:57:53 -0400] cupsdSetBusyState: Not busy
D [06/Jul/2010:07:57:53 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [06/Jul/2010:07:57:53 -0400] cupsdReadClient: 12 WAITING Closing on EOF
D [06/Jul/2010:07:57:53 -0400] cupsdCloseClient: 12
D [06/Jul/2010:07:57:53 -0400] cupsdReadClient: 13 GET /admin/log/error_log HTTP/1.1
D [06/Jul/2010:07:57:53 -0400] cupsdSetBusyState: Active clients
D [06/Jul/2010:07:57:53 -0400] cupsdAuthorize: No authentication data provided.

Any suggestions? I'd be really grateful for any help. Thanks!

---

### Post by Jgonick on 2010-07-06
I'm having the same issue.  On three computers after the update, the network printer will not work.  It won't even stay enabled.  I'm still using Karmic.  It is an update issue.  The problem started right after the update on all three computers.  The printer is a Brother MFC-7840W

---

### Post by WinRiddance on 2010-07-06
Try using an old Windows fix ... worked for me recently but with a different printer.

First remove any and all references to your printers if there are any to remove.
Then disconnect both power cord and parallel or usb cables.
Followed by cold booting (not restart) the machine and logging in again.
Finally hook up your power cable, USB, and power up the printer ... **wait for it** ...

With a little luck you'll get a "printer found" message after a while.
But even if that won't work, try using the Ubuntu default generic drivers.
That's what I had to do for our Oki color laser printer too. Doesn't give me all of the frills but it's working fine.

---

### Post by Mike Hof on 2010-07-06
i had the same problem.

i tried "sudo service cups start" and my printer(hp f4480) started working again.

i haven't done a reboot yet to see if it will still work or if i will have to enter the command each time i start my computer.

---

### Post by blacka on 2010-07-08
> **Mike Hof said:**
> i had the same problem.

i tried "sudo service cups start" and my printer(hp f4480) started working again.

i haven't done a reboot yet to see if it will still work or if i will have to enter the command each time i start my computer.

Worked perfectly. I have an HP Photosmart C4795 that stopped working last week after some updates. I was unable to complete the setup through hplip it kept asking for the ppd location. After running that command in terminal the setup was a breeze. Thank you.

---

### Post by cm8000000 on 2010-07-14
Thank you WinRiddance! That got the printer part of it working, but the scanner is a whole other problem. It's good to be able to print though!

---

