---
title: "Unable to print to PDF"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Roger Gundberg on 2008-10-14
I tried to print to PDF but no such option was offered. I went into Home/Roger but no directory is available. Synaptic Manager shows no broken packages. I went back to Sys/Admin/Printing and performed a debug routine. and got the following read-out. This is Ibex 8.10:
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest PDF (default)>,
 'cups_instance': None,
 'cups_queue': 'PDF',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'cups-pdf',
 'cups_printer_dict': {'device-uri': u'cups-pdf:/',
                       'printer-info': u'PDF',
                       'printer-is-shared': False,
                       'printer-location': u'',
                       'printer-make-and-model': u'Generic CUPS-PDF Printer',
                       'printer-state': 3,
                       'printer-state-message': u'No %%Pages: comment in header!',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 2289740,
                       'printer-uri-supported': u'ipp://localhost:631/printers/PDF'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'300dpi'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'file',
                      'device-id': u'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CLS:PRINTER;CMD:POSTSCRIPT;',
                      'device-info': u'CUPS-PDF',
                      'device-make-and-model': u'Virtual PDF Printer'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'No %%Pages: comment in header!',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'LogLevel': 'warning',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 3287L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(6, u'Job canceled.'), (7, u'Job canceled.')],
 'test_page_job_id': [6, 7],
 'test_page_job_status': [(True,
                           6,
                           'PDF',
                           'Test Page',
                           'Canceled',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 6,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 2,
                            'job-more-info': u'ipp://localhost:631/jobs/6',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'roger',
                            'job-preserved': False,
                            'job-printer-state-message': u'No %%Pages: comment in header!',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1224025988,
                            'job-printer-uri': u'ipp://roger-desktop:631/printers/PDF',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 7,

                            'job-state-reasons': u'job-canceled-by-user',
                            'job-uri': u'ipp://localhost:631/jobs/6',
                            'job-uuid': u'urn:uuid:622faa67-4b77-3ee5-7111-7f05451f7507',
                            'printer-uri': u'ipp://localhost/printers/PDF',
                            'time-at-completed': 1224025968,
                            'time-at-creation': 1224025967,
                            'time-at-processing': 1224025967}),
                          (True,
                           7,
                           'PDF',
                           'Test Page',
                           'Canceled',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 7,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 2,
                            'job-more-info': u'ipp://localhost:631/jobs/7',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'roger',
                            'job-preserved': False,
                            'job-printer-state-message': u'No %%Pages: comment in header!',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1224025988,
                            'job-printer-uri': u'ipp://roger-desktop:631/printers/PDF',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 7,
                            'job-state-reasons': u'job-canceled-by-user',
                            'job-uri': u'ipp://localhost:631/jobs/7',
                            'job-uuid': u'urn:uuid:9713ea27-3653-392a-60d4-e90c8d08729b',
                            'printer-uri': u'ipp://localhost/printers/PDF',
                            'time-at-completed': 1224025980,
                            'time-at-creation': 1224025978,
                            'time-at-processing': 1224025978})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [14/Oct/2008:17:12:36 -0600] cupsdCloseClient: 7',
               'D [14/Oct/2008:17:12:36 -0600] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [14/Oct/2008:17:12:36 -0600] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:36 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:36 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [14/Oct/2008:17:12:36 -0600] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:36 -0600] cupsdCloseClient: 7',
               'D [14/Oct/2008:17:12:36 -0600] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [14/Oct/2008:17:12:36 -0600] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:36 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:36 -0600] Create-Printer-Subscription /',
               'D [14/Oct/2008:17:12:36 -0600] cupsdCreateSubscription(con=0xb9782de0(7), uri="/")',
               'D [14/Oct/2008:17:12:36 -0600] pullmethod="ippget"',
               'D [14/Oct/2008:17:12:36 -0600] notify-lease-duration=86400',
               'D [14/Oct/2008:17:12:36 -0600] notify-time-interval=0',
               'D [14/Oct/2008:17:12:36 -0600] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [14/Oct/2008:17:12:36 -0600] Added subscription 11 for server',
               'I [14/Oct/2008:17:12:36 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:36 -0600] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:36 -0600] cupsdCloseClient: 7',
               'D [14/Oct/2008:17:12:37 -0600] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [14/Oct/2008:17:12:37 -0600] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:37 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:37 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:37 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:37 -0600] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:37 -0600] cupsdCloseClient: 7',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 7 POST /printers/PDF HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] Print-Job ipp://localhost/printers/PDF',
               'D [14/Oct/2008:17:12:47 -0600] add_job: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:47 -0600] Adding default job-sheets values "none,none"...',
               'I [14/Oct/2008:17:12:47 -0600] [Job 6] Adding start banner page "none".',
               'I [14/Oct/2008:17:12:47 -0600] Saving subscriptions.conf...',
               'I [14/Oct/2008:17:12:47 -0600] [Job 6] Adding end banner page "none".',
               'I [14/Oct/2008:17:12:47 -0600] [Job 6] File of type application/postscript queued by "roger".',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] hold_until=0',
               'I [14/Oct/2008:17:12:47 -0600] [Job 6] Queued on "PDF" by "roger".',
               'I [14/Oct/2008:17:12:47 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] job-sheets=none,none',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] banner_page = 0',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] argv[0]="PDF"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] argv[1]="6"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] argv[2]="roger"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] argv[3]="Test Page"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] argv[4]="1"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] argv[5]="job-uuid=urn:uuid:622faa67-4b77-3ee5-7111-7f05451f7507"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] argv[6]="/var/spool/cups/d00006-001"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[9]="SERVER_ADMIN=root@roger-desktop"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[12]="TZ=America/Shiprock"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[13]="USER=root"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[16]="IPP_PORT=631"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[17]="CHARSET=utf-8"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[18]="LANG=en_US.UTF8"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[19]="PPD=/etc/cups/ppd/PDF.ppd"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[20]="RIP_MAX_CACHE=8m"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[22]="DEVICE_URI=cups-pdf:/"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[23]="PRINTER=PDF"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] envp[24]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"',
               'I [14/Oct/2008:17:12:47 -0600] [Job 6] Started filter /usr/lib/cups/filter/pstopdf (PID 6269)',
               'I [14/Oct/2008:17:12:47 -0600] [Job 6] Started filter /usr/lib/cups/filter/pdftopdf (PID 6271)',
               'I [14/Oct/2008:17:12:47 -0600] [Job 6] Started filter /usr/lib/cups/filter/cpdftocps (PID 6274)',
               'I [14/Oct/2008:17:12:47 -0600] [Job 6] Started backend /usr/lib/cups/backend/cups-pdf (PID 6277)',
               'I [14/Oct/2008:17:12:47 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'E [14/Oct/2008:17:12:47 -0600] PID 6277 (/usr/lib/cups/backend/cups-pdf) stopped with status 5!',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] pstopdf argv[6] = 6 roger Test Page 1 job-uuid=urn:uuid:622faa67-4b77-3ee5-7111-7f05451f7507 /var/spool/cups/d00006-001',
               'D [14/Oct/2008:17:12:47 -0600] cupsdCloseClient: 7',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] pdftops - copying to temp print file "/tmp/48f5276f6d7c7"',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] Injecting PostScript: <</.HWMargins[0 0 0 0] /Margins[0 0]>>setpagedevice',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] Page = 612x792; 0,0 to 612,792',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] Before copy_comments - %!PS-Adobe-3.0',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] %!PS-Adobe-3.0',
               'E [14/Oct/2008:17:12:47 -0600] [Job 6] No %%BoundingBox: comment in header!',
               'I [14/Oct/2008:17:12:47 -0600] Saving subscriptions.conf...',
               'E [14/Oct/2008:17:12:47 -0600] [Job 6] No %%Pages: comment in header!',
               'I [14/Oct/2008:17:12:47 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] Before copy_prolog - <</.HWMargins[0 0 0 0] /Margins[0 0]>>setpagedevice',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] Before copy_setup - %%Page: 1 1',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] Before page loop - %%Page: 1 1',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] Copying page 1...',
               'I [14/Oct/2008:17:12:47 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] pagew = 612.0, pagel = 792.0',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] PageLeft = 0.0, PageRight = 612.0',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] PageTop = 792.0, PageBottom = 0.0',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] PageWidth = 612.0, PageLength = 792.0',
               'D [14/Oct/2008:17:12:47 -0600] [Job 6] Wrote 1 pages...',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:47 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] Get-Job-Attributes ipp://localhost/jobs/6',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:47 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Printers',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Classes',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Default',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Printers',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Classes',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Default',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Printers',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Classes',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:47 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:47 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:47 -0600] CUPS-Get-Default',
               'D [14/Oct/2008:17:12:47 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:48 -0600] cupsdCloseClient: 11',
               'D [14/Oct/2008:17:12:48 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:48 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:48 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:48 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:48 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:48 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:48 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:48 -0600] PID 6269 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [14/Oct/2008:17:12:48 -0600] PID 6271 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] Page = 612x792; 0,0 to 612,792',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] Before copy_comments - %!PS-Adobe-3.0',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] %!PS-Adobe-3.0',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] %%LanguageLevel: 2',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] %%DocumentSuppliedResources: (atend)',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] %%DocumentMedia: plain 612 792 0 () ()',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] %%BoundingBox: 0 0 612 792',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] %%Pages: 1',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] %%EndComments',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] Before copy_prolog - %%BeginDefaults',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] Before copy_setup - %%BeginSetup',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] Before page loop - %%Page: 1 1',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] Copying page 1...',
               'I [14/Oct/2008:17:12:48 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] pagew = 612.0, pagel = 792.0',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] PageLeft = 0.0, PageRight = 612.0',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] PageTop = 792.0, PageBottom = 0.0',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] PageWidth = 612.0, PageLength = 792.0',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] Wrote 1 pages...',
               'D [14/Oct/2008:17:12:48 -0600] PID 6274 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
               'D [14/Oct/2008:17:12:48 -0600] [Job 6] File 0 is complete.',
               'I [14/Oct/2008:17:12:48 -0600] [Job 6] Backend returned status 5 (cancel job)',
               'I [14/Oct/2008:17:12:48 -0600] Saving subscriptions.conf...',
               'I [14/Oct/2008:17:12:48 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:49 -0600] [Job 6] Unloading...',
               'D [14/Oct/2008:17:12:49 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:49 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [14/Oct/2008:17:12:49 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:49 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:49 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:49 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:49 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:49 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:49 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:49 -0600] CUPS-Get-Printers',
               'D [14/Oct/2008:17:12:49 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:49 -0600] CUPS-Get-Classes',
               'D [14/Oct/2008:17:12:49 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:49 -0600] CUPS-Get-Default',
               'D [14/Oct/2008:17:12:49 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:49 -0600] cupsdCloseClient: 11',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:49 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:49 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:49 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:49 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:49 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:58 -0600] cupsdReadClient: 8 POST /printers/PDF HTTP/1.1',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:58 -0600] Print-Job ipp://localhost/printers/PDF',
               'D [14/Oct/2008:17:12:58 -0600] add_job: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:58 -0600] Adding default job-sheets values "none,none"...',
               'I [14/Oct/2008:17:12:58 -0600] [Job 7] Adding start banner page "none".',
               'I [14/Oct/2008:17:12:58 -0600] Saving subscriptions.conf...',
               'I [14/Oct/2008:17:12:58 -0600] [Job 7] Adding end banner page "none".',
               'I [14/Oct/2008:17:12:58 -0600] [Job 7] File of type application/postscript queued by "roger".',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] hold_until=0',
               'I [14/Oct/2008:17:12:58 -0600] [Job 7] Queued on "PDF" by "roger".',
               'I [14/Oct/2008:17:12:58 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] job-sheets=none,none',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] banner_page = 0',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] argv[0]="PDF"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] argv[1]="7"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] argv[2]="roger"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] argv[3]="Test Page"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] argv[4]="1"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] argv[5]="job-uuid=urn:uuid:9713ea27-3653-392a-60d4-e90c8d08729b"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] argv[6]="/var/spool/cups/d00007-001"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[9]="SERVER_ADMIN=root@roger-desktop"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[12]="TZ=America/Shiprock"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[13]="USER=root"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[16]="IPP_PORT=631"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[17]="CHARSET=utf-8"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[18]="LANG=en_US.UTF8"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[19]="PPD=/etc/cups/ppd/PDF.ppd"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[20]="RIP_MAX_CACHE=8m"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[22]="DEVICE_URI=cups-pdf:/"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[23]="PRINTER=PDF"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] envp[24]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"',
               'I [14/Oct/2008:17:12:58 -0600] [Job 7] Started filter /usr/lib/cups/filter/pstopdf (PID 6314)',
               'I [14/Oct/2008:17:12:58 -0600] [Job 7] Started filter /usr/lib/cups/filter/pdftopdf (PID 6316)',
               'I [14/Oct/2008:17:12:58 -0600] [Job 7] Started filter /usr/lib/cups/filter/cpdftocps (PID 6319)',
               'I [14/Oct/2008:17:12:58 -0600] [Job 7] Started backend /usr/lib/cups/backend/cups-pdf (PID 6322)',
               'I [14/Oct/2008:17:12:58 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:58 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'E [14/Oct/2008:17:12:58 -0600] PID 6322 (/usr/lib/cups/backend/cups-pdf) stopped with status 5!',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] pstopdf argv[6] = 7 roger Test Page 1 job-uuid=urn:uuid:9713ea27-3653-392a-60d4-e90c8d08729b /var/spool/cups/d00007-001',
               'D [14/Oct/2008:17:12:58 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] pdftops - copying to temp print file "/tmp/48f5277aa11b5"',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] Injecting PostScript: <</.HWMargins[0 0 0 0] /Margins[0 0]>>setpagedevice',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] Page = 612x792; 0,0 to 612,792',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] Before copy_comments - %!PS-Adobe-3.0',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] %!PS-Adobe-3.0',
               'E [14/Oct/2008:17:12:58 -0600] [Job 7] No %%BoundingBox: comment in header!',
               'I [14/Oct/2008:17:12:58 -0600] Saving subscriptions.conf...',
               'E [14/Oct/2008:17:12:58 -0600] [Job 7] No %%Pages: comment in header!',
               'I [14/Oct/2008:17:12:58 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] Before copy_prolog - <</.HWMargins[0 0 0 0] /Margins[0 0]>>setpagedevice',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] Before copy_setup - %%Page: 1 1',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] Before page loop - %%Page: 1 1',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] Copying page 1...',
               'I [14/Oct/2008:17:12:58 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] pagew = 612.0, pagel = 792.0',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] PageLeft = 0.0, PageRight = 612.0',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] PageTop = 792.0, PageBottom = 0.0',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] PageWidth = 612.0, PageLength = 792.0',
               'D [14/Oct/2008:17:12:58 -0600] [Job 7] Wrote 1 pages...',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:58 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:58 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [14/Oct/2008:17:12:58 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:58 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:58 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:58 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:58 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:58 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:58 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:58 -0600] Get-Job-Attributes ipp://localhost/jobs/7',
               'D [14/Oct/2008:17:12:58 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [14/Oct/2008:17:12:58 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:58 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:58 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:58 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:58 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:58 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Printers',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Classes',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Default',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Printers',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Classes',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Default',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Printers',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Classes',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] CUPS-Get-Default',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdCloseClient: 11',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:12:59 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:12:59 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:12:59 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:12:59 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:12:59 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:12:59 -0600] PID 6314 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [14/Oct/2008:17:13:00 -0600] PID 6316 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] Page = 612x792; 0,0 to 612,792',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] Before copy_comments - %!PS-Adobe-3.0',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] %!PS-Adobe-3.0',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] %%LanguageLevel: 2',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] %%DocumentSuppliedResources: (atend)',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] %%DocumentMedia: plain 612 792 0 () ()',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] %%BoundingBox: 0 0 612 792',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] %%Pages: 1',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] %%EndComments',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] Before copy_prolog - %%BeginDefaults',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] Before copy_setup - %%BeginSetup',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] Before page loop - %%Page: 1 1',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] Copying page 1...',
               'I [14/Oct/2008:17:13:00 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] pagew = 612.0, pagel = 792.0',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] PageLeft = 0.0, PageRight = 612.0',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] PageTop = 792.0, PageBottom = 0.0',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] PageWidth = 612.0, PageLength = 792.0',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] Wrote 1 pages...',
               'D [14/Oct/2008:17:13:00 -0600] PID 6319 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
               'D [14/Oct/2008:17:13:00 -0600] [Job 7] File 0 is complete.',
               'I [14/Oct/2008:17:13:00 -0600] [Job 7] Backend returned status 5 (cancel job)',
               'I [14/Oct/2008:17:13:00 -0600] Saving subscriptions.conf...',
               'I [14/Oct/2008:17:13:00 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:00 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:13:00 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:13:00 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:00 -0600] CUPS-Get-Printers',
               'D [14/Oct/2008:17:13:00 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:00 -0600] CUPS-Get-Classes',
               'D [14/Oct/2008:17:13:00 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:00 -0600] CUPS-Get-Default',
               'D [14/Oct/2008:17:13:00 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:00 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [14/Oct/2008:17:13:00 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdCloseClient: 11',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:00 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:13:00 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:13:00 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdCloseClient: 11',
               'D [14/Oct/2008:17:13:00 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:00 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:00 -0600] Get-Notifications /',
               'D [14/Oct/2008:17:13:00 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'D [14/Oct/2008:17:13:00 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:00 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:13:01 -0600] [Job 7] Unloading...',
               'D [14/Oct/2008:17:13:08 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:13:08 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:08 -0600] Get-Job-Attributes ipp://localhost/jobs/6',
               'D [14/Oct/2008:17:13:08 -0600] [Job 6] Loading attributes...',
               'D [14/Oct/2008:17:13:08 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:08 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:08 -0600] Get-Job-Attributes ipp://localhost/jobs/7',
               'D [14/Oct/2008:17:13:08 -0600] [Job 7] Loading attributes...',
               'D [14/Oct/2008:17:13:08 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:08 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:13:08 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:13:08 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [14/Oct/2008:17:13:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [14/Oct/2008:17:13:08 -0600] Cancel-Subscription /',
               'D [14/Oct/2008:17:13:08 -0600] cupsdIsAuthorized: requesting-user-name="roger"',
               'I [14/Oct/2008:17:13:08 -0600] Saving subscriptions.conf...',
               'D [14/Oct/2008:17:13:08 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [14/Oct/2008:17:13:08 -0600] cupsdCloseClient: 8',
               'D [14/Oct/2008:17:13:08 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [14/Oct/2008:17:13:08 -0600] cupsdReadClient: 8 GET /admin/log/error_log HTTP/1.1',
               'D [14/Oct/2008:17:13:08 -0600] cupsdAuthorize: No authentication data provided.']}
```
What did I do Wrong?
Warmest Regards
Roger

---

### Post by ajmorris on 2008-10-14
hi there,
which application were you using to try to print to PDF?
 
 
 
AJ

---

### Post by overdrank on 2008-10-14
Moved to  Intrepid Ibex Testing and Discussion :)

---

### Post by FuturePilot on 2008-10-14
Is the cups-pdf package installed? It got removed on me when I upgraded for some reason.

---

### Post by Golgoth on 2008-10-15
same here: last week during upgrade, cups-pdf has been removed.

---

### Post by Piraja on 2008-10-17
Hey, does anyone here have any idea why the cups-pdf package was removed as "obsolete" in the Intrepid Beta upgrade, and not updated?

---

### Post by shane19174 on 2008-10-17
Hey, thanks for bringing up the cups-pdf issue. Mine had been uninstalled without my noticing it too. Reinstalling it solved a little problem for me. So just to repeat Piraja's question: why does the package get removed when upgrading? I assume (or rather hope) that it's because a newer package is on the way?

---

### Post by Piraja on 2008-10-17
I just found out that our question has been submitted to [Launchpad]("https://answers.launchpad.net/ubuntu/+source/cups-pdf/+question/48088") a couple of days ago. No response yet, so I think we just have to wait and see for a few days.

---

### Post by efinch on 2008-10-19
I reinstalled cups-pdf. Anyone know where the pdf files I print finish up? Thanks!

---

### Post by shane19174 on 2008-10-19
> I reinstalled cups-pdf. Anyone know where the pdf files I print finish up? Thanks! 

Usually in a subfolder of your home directory called simply "PDF".

---

### Post by Roger Gundberg on 2008-10-20
Worked like a charm! Thanks to everyone! You don't get this much help from Micro...something.

---

### Post by Piraja on 2008-10-20
Hey efinch, did you already find your files? I'm asking this because your question reminded me of myself searching for the output files. The reason I could not find them was that I had, for some reason, after installing cups-pdf messed up the ownership and permissions of the backends directory and the cups-pdf file therein. The following commands fixed the "[issue]("http://ubuntuforums.org/showthread.php?p=5963209")":

```
cd /usr/lib/cups/backend
sudo chown root:root cups-pdf
sudo chmod 700 cups-pdf
```

---

### Post by Lorenz on 2008-10-20
I actually thought that was a new feature, if you choose "print to file" you can tick PDF and it prints it as PDF to /home/PDF

works like a charm

---

### Post by nanog on 2008-10-20
and it gives you the choice of pdf or ps. choice is better...

---

### Post by dalonso on 2008-10-20
If I'm not wrong, PDF as well as PS printing is now integrated natively into Gtk-Print (gtk native print dialogs). 

So we do not need cups-pdf anymore.

The Gtk-Print support is far better, as for example, it lets you choose the output directory. No more obfuscated output directory as in cups-pdf.

I don't know however whats the situation in Kubuntu, though I seem to remember that KDE apps have already had native pdf printing for some time.

---

### Post by shane19174 on 2008-10-20
> **dalonso said:**
> If I'm not wrong, PDF as well as PS printing is now integrated natively into Gtk-Print (gtk native print dialogs). 

So we do not need cups-pdf anymore.

The Gtk-Print support is far better, as for example, it lets you choose the output directory. No more obfuscated output directory as in cups-pdf.

I don't know however whats the situation in Kubuntu, though I seem to remember that KDE apps have already had native pdf printing for some time.

Before I (re)installed cups-pdf, I was getting corrupted pdfs: the first page was fine, everything after that was garbled. This was the case in Thunderbird, Firefox, and OOo (the only three I tested). Of course it could be something particular to my system, but I'm certainly glad cups-pdf is still available.

---

### Post by efinch on 2008-10-23
> **Piraja said:**
> Hey efinch, did you already find your files? I'm asking this because your question reminded me of myself searching for the output files. The reason I could not find them was that I had, for some reason, after installing cups-pdf messed up the ownership and permissions of the backends directory and the cups-pdf file therein. The following commands fixed the "[issue]("http://ubuntuforums.org/showthread.php?p=5963209")":

```
cd /usr/lib/cups/backend
sudo chown root:root cups-pdf
sudo chmod 700 cups-pdf
```

Thanks, but I just couldn't get it to work that way, so I've just been going with the Print to File thing, which does seem fine.

---

### Post by maestrobwh1 on 2008-10-23
Cool: it actually makes sense to have it included.

---

### Post by ichigo on 2008-10-29
The same problme here! I've reinstalled cups-pdf after upgrading to intrepid and dtill can't find the output files, even though it looks like printing worked...
Piraja's code couldn't fix it either :(

I've seen the new print to file option but don't think it can substitute cups-pdf properly, because it doesn't have all the print options, cups-pdf has/had. (e.g. page ordering, when printing several pages on one)
Another reason for cups-pdf is that some programs (like acroread) don't use the standard print dialog and thus don't offer a print-to-pdf option...

---

