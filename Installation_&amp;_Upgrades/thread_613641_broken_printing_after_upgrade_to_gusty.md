---
title: "broken printing after upgrade to gusty"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by matt_30 on 2007-11-15
Before i upgraded to gusty i ran an epson stylus photo 915 and set it up so it could be used over my network

Since upgrading to gusty every time i go to print whether its to my Epsom or print to pdf it possesses and in the Kubuntu  system settings printer section all my print jobs state show possessing and then switch to held.

has anyone else had the same problem or know of a fix?

---

### Post by matt_30 on 2007-11-30
2 weeks later and after taking cups and the printing system apart and putting it back together again i still get all my printer jobs 'held'.

As far as i can tell cups recognises my printer (see code below) im out of idea this only started when i upgraded to gusty

any help would be much appreciated

matt.

```

matt@base-unit:~$ lsmod | grep usb
usb_storage            73024  0
libusual               18448  1 usb_storage
usblp                  15104  0
scsi_mod              147084  4 sg,sd_mod,usb_storage,libata
ide_core              116804  4 usb_storage,ide_cd,ide_disk,via82cxxx
usbcore               138632  7 usb_storage,libusual,usblp,quickcam,ehci_hcd,uhci_hcd

matt@base-unit:~$ tail -f /var/log/messages
Nov 30 11:44:11 base-unit kernel: [ 4893.104000] audit(1196423051.153:14):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=6893 profile="/usr/sbin/cupsd"
Nov 30 11:44:11 base-unit kernel: [ 4893.120000] audit(1196423051.153:15):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=6897 profile="/usr/sbin/cupsd"
Nov 30 11:44:48 base-unit kernel: [ 4929.960000] Inbound IN=eth0 OUT= MAC=00:0d:87:6f:fd:4a:00:0f:b5:17:15:0a:08:00 SRC=185.149.230.147 DST=192.168.0.3 LEN=401 TOS=0x00 PREC=0x00 TTL=48 ID=56527 PROTO=UDP SPT=30585 DPT=1026 LEN=381
Nov 30 11:44:58 base-unit kernel: [ 4940.216000] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.3 DST=192.168.0.255 LEN=261 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=241
Nov 30 11:44:58 base-unit kernel: [ 4940.216000] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.3 DST=192.168.0.255 LEN=238 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=218
Nov 30 11:47:15 base-unit kernel: [ 5076.860000] Inbound IN=eth0 OUT= MAC=00:0d:87:6f:fd:4a:00:0f:b5:17:15:0a:08:00 SRC=128.227.83.11 DST=192.168.0.3 LEN=105 TOS=0x00 PREC=0x00 TTL=109 ID=8778 PROTO=UDP SPT=17195 DPT=17195 LEN=85
Nov 30 11:47:26 base-unit kernel: [ 5087.672000] Inbound IN=eth0 OUT= MAC=00:0d:87:6f:fd:4a:00:0f:b5:17:15:0a:08:00 SRC=24.64.219.244 DST=192.168.0.3 LEN=512 TOS=0x00 PREC=0x00 TTL=65 ID=55056 PROTO=UDP SPT=21761 DPT=1026 LEN=492
Nov 30 11:47:26 base-unit kernel: [ 5087.672000] Inbound IN=eth0 OUT= MAC=00:0d:87:6f:fd:4a:00:0f:b5:17:15:0a:08:00 SRC=24.64.219.244 DST=192.168.0.3 LEN=512 TOS=0x00 PREC=0x00 TTL=65 ID=55057 PROTO=UDP SPT=21761 DPT=1027 LEN=492
Nov 30 11:47:26 base-unit kernel: [ 5087.672000] Inbound IN=eth0 OUT= MAC=00:0d:87:6f:fd:4a:00:0f:b5:17:15:0a:08:00 SRC=24.64.219.244 DST=192.168.0.3 LEN=512 TOS=0x00 PREC=0x00 TTL=65 ID=55058 PROTO=UDP SPT=21761 DPT=1028 LEN=492
Nov 30 11:48:27 base-unit kernel: [ 5148.840000] Inbound IN=eth0 OUT= MAC=00:0d:87:6f:fd:4a:00:0f:b5:17:15:0a:08:00 SRC=128.227.83.11 DST=192.168.0.3 LEN=105 TOS=0x00 PREC=0x00 TTL=109 ID=12995 PROTO=UDP SPT=17195 DPT=17195 LEN=85
Nov 30 11:49:59 base-unit kernel: [ 5241.540000] usb 2-2: USB disconnect, address 5
Nov 30 11:49:59 base-unit kernel: [ 5241.540000] usb 2-2.1: USB disconnect, address 6
Nov 30 11:49:59 base-unit kernel: [ 5241.540000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
Nov 30 11:49:59 base-unit kernel: [ 5241.540000] usb 2-2.2: USB disconnect, address 7
Nov 30 11:50:02 base-unit kernel: [ 5244.020000] usb 2-2: new full speed USB device using uhci_hcd and address 8
Nov 30 11:50:02 base-unit kernel: [ 5244.188000] usb 2-2: configuration #1 chosen from 1 choice
Nov 30 11:50:02 base-unit kernel: [ 5244.196000] hub 2-2:1.0: USB hub found
Nov 30 11:50:02 base-unit kernel: [ 5244.196000] hub 2-2:1.0: 2 ports detected
Nov 30 11:50:02 base-unit kernel: [ 5244.508000] usb 2-2.1: new full speed USB device using uhci_hcd and address 9
Nov 30 11:50:03 base-unit kernel: [ 5244.648000] usb 2-2.1: configuration #1 chosen from 1 choice
Nov 30 11:50:03 base-unit kernel: [ 5244.656000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 9 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
Nov 30 11:50:03 base-unit kernel: [ 5244.860000] usb 2-2.2: new full speed USB device using uhci_hcd and address 10
Nov 30 11:50:03 base-unit kernel: [ 5244.992000] usb 2-2.2: configuration #1 chosen from 1 choice
Nov 30 11:50:03 base-unit kernel: [ 5244.992000] scsi2 : SCSI emulation for USB Mass Storage devices
Nov 30 11:50:08 base-unit kernel: [ 5249.992000] scsi 2:0:0:0: Direct-Access     EPSON    SP 915 Storage   1.10 PQ: 0 ANSI: 2
Nov 30 11:50:08 base-unit kernel: [ 5250.000000] sd 2:0:0:0: [sda] Attached SCSI removable disk
Nov 30 11:50:08 base-unit kernel: [ 5250.000000] sd 2:0:0:0: Attached scsi generic sg0 type 0

matt@base-unit:~$ lpinfo -v
network socket
network beh
direct epson:/dev/usb/lp0
network http
network ipp
network lpd
file cups-pdf:/
direct scsi
network smb
matt@base-unit:~$      


```

---

### Post by matt_30 on 2007-11-30
/var/log/cups/error_log

<code>
matt@base-unit:/var/log/cups$ cat error_log
I [30/Nov/2007:09:41:02 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
N [30/Nov/2007:09:41:02 +0000] Group and SystemGroup cannot use the same groups!
I [30/Nov/2007:09:41:02 +0000] Resetting Group to "root"...
I [30/Nov/2007:09:41:02 +0000] Configured for up to 100 clients.
I [30/Nov/2007:09:41:02 +0000] Allowing up to 100 client connections per host.
I [30/Nov/2007:09:41:02 +0000] Using policy "default" as the default!
I [30/Nov/2007:09:41:02 +0000] Full reload is required.
I [30/Nov/2007:09:41:02 +0000] Saving job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:09:41:02 +0000] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
I [30/Nov/2007:09:41:02 +0000] Loading job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:09:41:02 +0000] Full reload complete.
I [30/Nov/2007:09:41:02 +0000] Listening to :::631 on fd 4...
I [30/Nov/2007:09:41:02 +0000] Listening to 0.0.0.0:631 on fd 5...
I [30/Nov/2007:09:41:02 +0000] Listening to /var/run/cups/cups.sock on fd 6...
E [30/Nov/2007:09:41:02 +0000] Unable to bind socket for address 192.168.0.255:631 - Cannot assign requested address.
I [30/Nov/2007:09:41:02 +0000] Resuming new connection processing...
E [30/Nov/2007:09:52:50 +0000] CUPS-Delete-Printer: Unauthorized
I [30/Nov/2007:09:52:51 +0000] Printer "PDF" deleted by "root".
I [30/Nov/2007:09:52:51 +0000] Saving printers.conf...
E [30/Nov/2007:10:02:51 +0000] CUPS-Delete-Printer: Unauthorized
I [30/Nov/2007:10:02:51 +0000] Printer "epson" deleted by "root".
I [30/Nov/2007:10:02:51 +0000] Saving printers.conf...
I [30/Nov/2007:10:06:16 +0000] Scheduler shutting down normally.
I [30/Nov/2007:10:06:16 +0000] Saving job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:06:26 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
N [30/Nov/2007:10:06:26 +0000] Group and SystemGroup cannot use the same groups!
I [30/Nov/2007:10:06:26 +0000] Resetting Group to "root"...
I [30/Nov/2007:10:06:26 +0000] Configured for up to 100 clients.
I [30/Nov/2007:10:06:26 +0000] Allowing up to 100 client connections per host.
I [30/Nov/2007:10:06:26 +0000] Using policy "default" as the default!
I [30/Nov/2007:10:06:26 +0000] Full reload is required.
I [30/Nov/2007:10:06:26 +0000] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
I [30/Nov/2007:10:06:26 +0000] Loading job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:06:26 +0000] Full reload complete.
I [30/Nov/2007:10:06:26 +0000] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [30/Nov/2007:10:06:26 +0000] Listening to :::631 on fd 3...
I [30/Nov/2007:10:06:26 +0000] Listening to 0.0.0.0:631 on fd 4...
I [30/Nov/2007:10:06:26 +0000] Listening to /var/run/cups/cups.sock on fd 5...
E [30/Nov/2007:10:06:26 +0000] Unable to bind socket for address 192.168.0.255:631 - Address already in use.
I [30/Nov/2007:10:06:26 +0000] Resuming new connection processing...
I [30/Nov/2007:10:06:27 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
N [30/Nov/2007:10:06:27 +0000] Group and SystemGroup cannot use the same groups!
I [30/Nov/2007:10:06:27 +0000] Resetting Group to "root"...
I [30/Nov/2007:10:06:27 +0000] Configured for up to 100 clients.
I [30/Nov/2007:10:06:27 +0000] Allowing up to 100 client connections per host.
I [30/Nov/2007:10:06:27 +0000] Using policy "default" as the default!
I [30/Nov/2007:10:06:27 +0000] Full reload is required.
I [30/Nov/2007:10:06:27 +0000] Saving job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:06:27 +0000] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
I [30/Nov/2007:10:06:27 +0000] Loading job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:06:27 +0000] Full reload complete.
I [30/Nov/2007:10:06:27 +0000] Listening to :::631 on fd 3...
I [30/Nov/2007:10:06:27 +0000] Listening to 0.0.0.0:631 on fd 4...
I [30/Nov/2007:10:06:27 +0000] Listening to /var/run/cups/cups.sock on fd 5...
E [30/Nov/2007:10:06:27 +0000] Unable to bind socket for address 192.168.0.255:631 - Address already in use.
I [30/Nov/2007:10:06:27 +0000] Resuming new connection processing...
I [30/Nov/2007:10:06:49 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
N [30/Nov/2007:10:06:49 +0000] Group and SystemGroup cannot use the same groups!
I [30/Nov/2007:10:06:49 +0000] Resetting Group to "root"...
I [30/Nov/2007:10:06:49 +0000] Configured for up to 100 clients.
I [30/Nov/2007:10:06:49 +0000] Allowing up to 100 client connections per host.
I [30/Nov/2007:10:06:49 +0000] Using policy "default" as the default!
I [30/Nov/2007:10:06:49 +0000] Full reload is required.
I [30/Nov/2007:10:06:49 +0000] Saving job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:06:49 +0000] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
I [30/Nov/2007:10:06:50 +0000] Loading job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:06:50 +0000] Full reload complete.
I [30/Nov/2007:10:06:50 +0000] Listening to :::631 on fd 3...
I [30/Nov/2007:10:06:50 +0000] Listening to 0.0.0.0:631 on fd 4...
I [30/Nov/2007:10:06:50 +0000] Listening to /var/run/cups/cups.sock on fd 5...
E [30/Nov/2007:10:06:50 +0000] Unable to bind socket for address 192.168.0.255:631 - Address already in use.
I [30/Nov/2007:10:06:50 +0000] Resuming new connection processing...
E [30/Nov/2007:10:06:53 +0000] CUPS-Add-Modify-Printer: Unauthorized
I [30/Nov/2007:10:06:53 +0000] Setting PDF printer-is-accepting-jobs to 1 (was 0.)
I [30/Nov/2007:10:06:53 +0000] Setting PDF printer-state to 3 (was 5.)
I [30/Nov/2007:10:06:53 +0000] Saving printers.conf...
I [30/Nov/2007:10:06:53 +0000] New printer "PDF" added by "root".
I [30/Nov/2007:10:06:53 +0000] Setting PDF device-uri to "cups-pdf:/" (was "file:/dev/null".)
I [30/Nov/2007:10:06:53 +0000] Saving printers.conf...
I [30/Nov/2007:10:06:53 +0000] Printer "PDF" modified by "root".
I [30/Nov/2007:10:06:53 +0000] Saving printers.conf...
I [30/Nov/2007:10:06:53 +0000] Printer "PDF" modified by "root".
I [30/Nov/2007:10:06:53 +0000] Setting PDF printer-is-shared to 0 (was 1.)
I [30/Nov/2007:10:06:53 +0000] Saving printers.conf...
I [30/Nov/2007:10:06:53 +0000] Printer "PDF" modified by "root".
I [30/Nov/2007:10:18:39 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=9137)
I [30/Nov/2007:10:18:40 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=9153)
I [30/Nov/2007:10:19:05 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=9184)
I [30/Nov/2007:10:19:06 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=9200)
I [30/Nov/2007:10:21:30 +0000] Scheduler shutting down normally.
I [30/Nov/2007:10:21:30 +0000] Saving job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:21:30 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
N [30/Nov/2007:10:21:30 +0000] Group and SystemGroup cannot use the same groups!
I [30/Nov/2007:10:21:30 +0000] Resetting Group to "root"...
I [30/Nov/2007:10:21:30 +0000] Configured for up to 100 clients.
I [30/Nov/2007:10:21:30 +0000] Allowing up to 100 client connections per host.
I [30/Nov/2007:10:21:30 +0000] Using policy "default" as the default!
I [30/Nov/2007:10:21:30 +0000] Full reload is required.
I [30/Nov/2007:10:21:30 +0000] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
I [30/Nov/2007:10:21:30 +0000] Loading job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:21:30 +0000] Full reload complete.
I [30/Nov/2007:10:21:30 +0000] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [30/Nov/2007:10:21:30 +0000] Listening to :::631 on fd 3...
I [30/Nov/2007:10:21:30 +0000] Listening to 0.0.0.0:631 on fd 4...
I [30/Nov/2007:10:21:30 +0000] Listening to /var/run/cups/cups.sock on fd 5...
E [30/Nov/2007:10:21:30 +0000] Unable to bind socket for address 192.168.0.255:631 - Address already in use.
I [30/Nov/2007:10:21:30 +0000] Resuming new connection processing...
I [30/Nov/2007:10:21:43 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=9527)
I [30/Nov/2007:10:21:44 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=9543)
I [30/Nov/2007:10:22:16 +0000] Scheduler shutting down normally.
I [30/Nov/2007:10:22:16 +0000] Saving job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:23:08 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
N [30/Nov/2007:10:23:08 +0000] Group and SystemGroup cannot use the same groups!
I [30/Nov/2007:10:23:08 +0000] Resetting Group to "root"...
I [30/Nov/2007:10:23:08 +0000] Configured for up to 100 clients.
I [30/Nov/2007:10:23:08 +0000] Allowing up to 100 client connections per host.
I [30/Nov/2007:10:23:08 +0000] Using policy "default" as the default!
I [30/Nov/2007:10:23:08 +0000] Full reload is required.
I [30/Nov/2007:10:23:08 +0000] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
I [30/Nov/2007:10:23:08 +0000] Loading job cache file "/var/cache/cups/job.cache"...
I [30/Nov/2007:10:23:08 +0000] Full reload complete.
I [30/Nov/2007:10:23:08 +0000] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [30/Nov/2007:10:23:08 +0000] Listening to :::631 on fd 3...
I [30/Nov/2007:10:23:08 +0000] Listening to 0.0.0.0:631 on fd 4...
I [30/Nov/2007:10:23:08 +0000] Listening to /var/run/cups/cups.sock on fd 5...
E [30/Nov/2007:10:23:08 +0000] Unable to bind socket for address 192.168.0.255:631 - Cannot assign requested address.
I [30/Nov/2007:10:23:08 +0000] Resuming new connection processing...
I [30/Nov/2007:11:38:14 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6517)
I [30/Nov/2007:11:38:16 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6558)
I [30/Nov/2007:11:38:41 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6589)
I [30/Nov/2007:11:38:42 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6605)
I [30/Nov/2007:11:41:29 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6769)
I [30/Nov/2007:11:43:45 +0000] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6879)
I [30/Nov/2007:11:44:10 +0000] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6886)
I [30/Nov/2007:11:44:10 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6887)
I [30/Nov/2007:11:44:17 +0000] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6903)
I [30/Nov/2007:11:44:17 +0000] Started "/usr/lib/cups/daemon/cups-driverd" (pid=6904)
E [30/Nov/2007:11:44:20 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [30/Nov/2007:11:44:20 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
I [30/Nov/2007:11:45:13 +0000] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6912)
E [30/Nov/2007:11:45:13 +0000] CUPS-Add-Modify-Printer: Unauthorized
I [30/Nov/2007:11:45:18 +0000] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6913)
E [30/Nov/2007:11:45:18 +0000] CUPS-Add-Modify-Printer: Unauthorized
I [30/Nov/2007:11:45:18 +0000] Setting epson device-uri to "epson:/dev/usb/lp0" (was "file:/dev/null".)
I [30/Nov/2007:11:45:18 +0000] Setting epson printer-is-accepting-jobs to 1 (was 0.)
I [30/Nov/2007:11:45:18 +0000] Setting epson printer-state to 3 (was 5.)
I [30/Nov/2007:11:45:18 +0000] Saving printers.conf...
I [30/Nov/2007:11:45:18 +0000] New printer "epson" added by "matt".
I [30/Nov/2007:11:45:23 +0000] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6915)
I [30/Nov/2007:11:45:41 +0000] [Job 137] Adding start banner page "none".
I [30/Nov/2007:11:45:41 +0000] [Job 137] Adding job file of type application/postscript.
I [30/Nov/2007:11:45:41 +0000] [Job 137] Adding end banner page "none".
I [30/Nov/2007:11:45:41 +0000] [Job 137] Queued on "epson" by "matt".
I [30/Nov/2007:11:45:41 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstops (PID 6916)
I [30/Nov/2007:11:45:41 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstoraster (PID 6917)
I [30/Nov/2007:11:45:41 +0000] [Job 137] Started filter /usr/lib/cups/filter/rastertogutenprint.5.0 (PID 6918)
I [30/Nov/2007:11:45:41 +0000] [Job 137] Started backend /usr/lib/cups/backend/epson (PID 6919)
E [30/Nov/2007:11:45:42 +0000] [Job 137] Unable to open parallel port device file: Permission denied
E [30/Nov/2007:11:45:42 +0000] PID 6919 (/usr/lib/cups/backend/epson) stopped with status 1!
I [30/Nov/2007:11:45:42 +0000] Hint: Try setting the LogLevel to "debug" to find out more.
I [30/Nov/2007:11:46:05 +0000] [Job 137] Backend returned status 1 (failed)
I [30/Nov/2007:11:50:41 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=7040)
I [30/Nov/2007:11:51:08 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstops (PID 7058)
I [30/Nov/2007:11:51:08 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstoraster (PID 7059)
I [30/Nov/2007:11:51:08 +0000] [Job 137] Started filter /usr/lib/cups/filter/rastertogutenprint.5.0 (PID 7061)
I [30/Nov/2007:11:51:08 +0000] [Job 137] Started backend /usr/lib/cups/backend/epson (PID 7062)
E [30/Nov/2007:11:51:08 +0000] [Job 137] Unable to open parallel port device file: Permission denied
E [30/Nov/2007:11:51:08 +0000] PID 7062 (/usr/lib/cups/backend/epson) stopped with status 1!
I [30/Nov/2007:11:51:08 +0000] Hint: Try setting the LogLevel to "debug" to find out more.
I [30/Nov/2007:11:51:32 +0000] [Job 137] Backend returned status 1 (failed)
I [30/Nov/2007:11:56:42 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstops (PID 7066)
I [30/Nov/2007:11:56:42 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstoraster (PID 7067)
I [30/Nov/2007:11:56:42 +0000] [Job 137] Started filter /usr/lib/cups/filter/rastertogutenprint.5.0 (PID 7069)
I [30/Nov/2007:11:56:42 +0000] [Job 137] Started backend /usr/lib/cups/backend/epson (PID 7070)
E [30/Nov/2007:11:56:42 +0000] [Job 137] Unable to open parallel port device file: Permission denied
E [30/Nov/2007:11:56:42 +0000] PID 7070 (/usr/lib/cups/backend/epson) stopped with status 1!
I [30/Nov/2007:11:56:42 +0000] Hint: Try setting the LogLevel to "debug" to find out more.
I [30/Nov/2007:11:57:03 +0000] [Job 137] Backend returned status 1 (failed)
I [30/Nov/2007:12:01:48 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstops (PID 7122)
I [30/Nov/2007:12:01:48 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstoraster (PID 7123)
I [30/Nov/2007:12:01:48 +0000] [Job 137] Started filter /usr/lib/cups/filter/rastertogutenprint.5.0 (PID 7125)
I [30/Nov/2007:12:01:48 +0000] [Job 137] Started backend /usr/lib/cups/backend/epson (PID 7126)
I [30/Nov/2007:12:01:48 +0000] [Job 137] Released by "matt".
E [30/Nov/2007:12:01:48 +0000] [Job 137] Unable to open parallel port device file: Permission denied
E [30/Nov/2007:12:01:48 +0000] PID 7126 (/usr/lib/cups/backend/epson) stopped with status 1!
I [30/Nov/2007:12:01:48 +0000] Hint: Try setting the LogLevel to "debug" to find out more.
I [30/Nov/2007:12:02:09 +0000] [Job 137] Backend returned status 1 (failed)
I [30/Nov/2007:12:07:13 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstops (PID 7366)
I [30/Nov/2007:12:07:13 +0000] [Job 137] Started filter /usr/lib/cups/filter/pstoraster (PID 7367)
I [30/Nov/2007:12:07:13 +0000] [Job 137] Started filter /usr/lib/cups/filter/rastertogutenprint.5.0 (PID 7369)
I [30/Nov/2007:12:07:13 +0000] [Job 137] Started backend /usr/lib/cups/backend/epson (PID 7370)
E [30/Nov/2007:12:07:13 +0000] PID 7370 (/usr/lib/cups/backend/epson) stopped with status 1!
I [30/Nov/2007:12:07:13 +0000] Hint: Try setting the LogLevel to "debug" to find out more.
E [30/Nov/2007:12:07:13 +0000] [Job 137] Unable to open parallel port device file: Permission denied
I [30/Nov/2007:12:07:36 +0000] [Job 137] Backend returned status 1 (failed)
E [30/Nov/2007:12:07:36 +0000] [Job 137] Canceling job since it could not be sent after 5 tries.

</code>

---

### Post by jkzubu on 2007-12-01
edit

---

### Post by matt_30 on 2007-12-01
my problem is if i try to print from any graphical application (open office, Firefox, general kde, etc.) all print jobs possess then changed to the 'held' state.

ive looked through the logs and the conf files and reinstalled cups but no success.

this all happened after upgrading from fawn to gusty

---

### Post by Col-1023 on 2007-12-19
I'm having a strange problem with my brother mfc-210c.

I have it connected via usb to my ubuntu box, and no matter what I do, whether its print a test page, some text, or a photo, it just says job processing, then completed, but nothing prints.

I have a windows box hooked up to a router and I can use it to print (via samba) of my brother with no problem.

---

### Post by foxy123 on 2007-12-23
got the same problem with Epson Stylus DX3800. There is a bug reported: [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/130871](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/130871)

---

### Post by john_3000 on 2007-12-26
This probably isn't the right thread to post this in but no matter where it goes it can still be googled so wtf.

When I upgraded to 7.10 I lost the ability to print .pdf files within Acrobat via Cups and Samba on a remote windows machine's printer.  Evince worked (printed) so I knew it was just a matter of getting the command right in  

     (acrobat)/print/(select printer in drop-down menu)/properties. 

I googled up a storm without success.  What finally worked for me was

               /usr/bin/lpr -P smb://guest:@192.168.1.20/Printer2

where 192.168.1.20 is the remote windows machine. Note the colon in front of the @.

---

