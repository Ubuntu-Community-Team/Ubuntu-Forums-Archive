---
title: "Brother HL2140 segmentation fault"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by glennr on 2010-02-18
I was using a Brother HL2140 on Kubuntu 8.04 amd64 and within the last week or two it stopped working.

In the cups error_log below (near the end) it shows that something is causing a seg fault. I keep this machine up to date and I suspect that a recent update broke it.

I haven't found anything useful from searching. Anyone know how to diagnose and/or fix this?

```

D [12/Feb/2010:10:59:51 +1300] Print-Job ipp://localhost/printers/HL2140
D [12/Feb/2010:10:59:51 +1300] print_job: auto-typing file...
D [12/Feb/2010:10:59:51 +1300] add_job: requesting-user-name="glenn"
I [12/Feb/2010:10:59:51 +1300] [Job 2368] Adding start banner page "none".
D [12/Feb/2010:10:59:51 +1300] Discarding unused job-created event...
I [12/Feb/2010:10:59:51 +1300] [Job 2368] Adding job file of type application/postscript.
I [12/Feb/2010:10:59:51 +1300] [Job 2368] Adding end banner page "none".
I [12/Feb/2010:10:59:51 +1300] [Job 2368] Queued on "HL2140" by "glenn".
D [12/Feb/2010:10:59:51 +1300] [Job 2368] hold_until = 0
D [12/Feb/2010:10:59:51 +1300] Discarding unused printer-state-changed event...
D [12/Feb/2010:10:59:51 +1300] [Job 2368] job-sheets=none,none
D [12/Feb/2010:10:59:51 +1300] [Job 2368] banner_page = 0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] argv[0]="HL2140"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] argv[1]="2368"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] argv[2]="glenn"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] argv[3]="(no subject)"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] argv[4]="1"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] argv[5]="media=A4 finishings=3 number-up=1 job-uuid=urn:uuid:b7156f7a-b3d2-39d5-6fb7-808fa97043a7"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] argv[6]="/var/spool/cups/d02368-001"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[9]="SERVER_ADMIN=root@cs"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[10]="SOFTWARE=CUPS/1.3.7"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[12]="TZ=Pacific/Auckland"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[13]="USER=root"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[16]="IPP_PORT=631"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[17]="CHARSET=utf-8"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[18]="LANG=en_NZ.UTF8"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[19]="PPD=/etc/cups/ppd/HL2140.ppd"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[20]="RIP_MAX_CACHE=8m"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[21]="CONTENT_TYPE=application/postscript"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[22]="DEVICE_URI=usb://Brother/HL-2140%20series"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[23]="PRINTER=HL2140"
D [12/Feb/2010:10:59:51 +1300] [Job 2368] envp[24]="FINAL_CONTENT_TYPE=printer/HL2140"
I [12/Feb/2010:10:59:51 +1300] [Job 2368] Started filter /usr/lib/cups/filter/pstops (PID 22336)
I [12/Feb/2010:10:59:51 +1300] [Job 2368] Started filter /usr/lib/cups/filter/brlpdwrapperHL2140 (PID 22337)
I [12/Feb/2010:10:59:51 +1300] [Job 2368] Started backend /usr/lib/cups/backend/usb (PID 22338)
D [12/Feb/2010:10:59:51 +1300] Discarding unused job-state-changed event...
D [12/Feb/2010:10:59:51 +1300] cupsdProcessIPPRequest: 34 status_code=0 (successful-ok)
D [12/Feb/2010:10:59:51 +1300] PID 22336 (/usr/lib/cups/filter/pstops) exited with no errors.
D [12/Feb/2010:10:59:51 +1300] cupsdAcceptClient: 36 from localhost (Domain)
D [12/Feb/2010:10:59:51 +1300] [Job 2368] Page = 595x842; 18,12 to 577,830
D [12/Feb/2010:10:59:51 +1300] [Job 2368] slow_collate=0, slow_duplex=0, slow_order=0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] Before copy_comments - %!PS-Adobe-3.0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %!PS-Adobe-3.0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%BoundingBox: 0 0 612 792
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%HiResBoundingBox: 0 0 612 792
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%Creator: Mozilla PostScript module (rv:1.8.1.23/2009081714)
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%DocumentData: Clean8Bit
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%DocumentPaperSizes: Letter
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%Orientation: Portrait
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%Pages: 1
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%PageOrder: Ascend
D [12/Feb/2010:10:59:51 +1300] [Job 2368] %%EndComments
D [12/Feb/2010:10:59:51 +1300] [Job 2368] Before copy_prolog - % MozillaCharsetName: iso-8859-1
D [12/Feb/2010:10:59:51 +1300] [Job 2368] Before copy_setup - %%BeginResource: font Nimbus_Roman_No9_L.Medium.0.0.Set0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] Before page loop - %%Page: 1 1
D [12/Feb/2010:10:59:51 +1300] [Job 2368] Copying page 1...
D [12/Feb/2010:10:59:51 +1300] [Job 2368] pagew = 559.0, pagel = 818.0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [12/Feb/2010:10:59:51 +1300] [Job 2368] PageLeft = 18.0, PageRight = 577.0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] PageTop = 830.0, PageBottom = 12.0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] PageWidth = 595.0, PageLength = 842.0
D [12/Feb/2010:10:59:51 +1300] [Job 2368] Wrote 1 pages...
D [12/Feb/2010:10:59:51 +1300] Discarding unused printer-state-changed event...
D [12/Feb/2010:10:59:51 +1300] [Job 2368] Printer using device file "/dev/usblp0"...
D [12/Feb/2010:10:59:51 +1300] [Job 2368] backendRunLoop(print_fd=0, device_fd=7, use_bc=0, side_cb=0x401f80)
D [12/Feb/2010:10:59:51 +1300] Discarding unused printer-state-changed event...
D [12/Feb/2010:10:59:52 +1300] [Job 2368] Segmentation fault
D [12/Feb/2010:10:59:52 +1300] PID 22338 (/usr/lib/cups/backend/usb) exited with no errors.
D [12/Feb/2010:10:59:52 +1300] PID 22337 (/usr/lib/cups/filter/brlpdwrapperHL2140) exited with no errors.
D [12/Feb/2010:10:59:52 +1300] [Job 2368] File 0 is complete.
I [12/Feb/2010:10:59:52 +1300] [Job 2368] Completed successfully.
D [12/Feb/2010:10:59:52 +1300] Discarding unused printer-state-changed event...
D [12/Feb/2010:10:59:52 +1300] Discarding unused job-completed event...
D [12/Feb/2010:10:59:53 +1300] [Job 2368] Unloading...

```

---

### Post by byStanderone on 2010-02-18
...hope a sudo apt-get autoclean fixes it.

---

### Post by glennr on 2010-02-18
> **byStanderone said:**
> ...hope a sudo apt-get autoclean fixes it.

It didn't, but thanks for the suggestion.

---

### Post by glennr on 2010-02-18
It works if I set up a "Raw" queue and print from Windows over the network, so that probably rules out an issue with the printer itself, the USB connection or CUPS.

---

### Post by glennr on 2010-02-18
I got a PPD file from openprinting.org and it now works.

Diff shows that it is very different from the Brother one, so I guess some package update changed something that causes it to no longer work.

---

### Post by byStanderone on 2010-02-18
...ok, enjoy your ubuntu.

---

