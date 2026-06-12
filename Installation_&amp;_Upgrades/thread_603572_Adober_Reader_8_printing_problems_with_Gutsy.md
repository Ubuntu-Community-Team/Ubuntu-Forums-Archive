---
title: "Adober Reader 8 printing problems with Gutsy"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by jmagsho on 2007-11-05
I am having problems printing docs from Adobe Reader 8.   This all started after the upgrade from Feisty to Gutsy.

I am printing to an HP Photosmart 3210 network printer using CUPS with the latest HPLIP drivers.   All other applications print just fine, but when I try to print a doc from Adobe 8 it will spool to the print queue and then subsequently die.    The status flips to stopped after about 30 seconds and the doc will not print.

CUPS logs have not proven very useful thus far so I thought I would put it out there to see if anyone else is experiencing any weirdness with this.

I should mention that the docs I am trying to print are protected but will allow you to type data into the form (tried with evince but this functionality will not work and unfortunately it is a necessity for me to have it).

Any input would be appreciated.   I will post the logfile output later today.

Thanks in advance.

- JM

---

### Post by jmagsho on 2007-11-05
Here's a snip of the logfile:

D [05/Nov/2007:23:34:57 -0500] [Job 112] Loading attributes...
D [05/Nov/2007:23:34:57 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)
D [05/Nov/2007:23:34:57 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [05/Nov/2007:23:34:57 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:34:57 -0500] CUPS-Get-Printers
D [05/Nov/2007:23:34:57 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)
D [05/Nov/2007:23:34:57 -0500] cupsdCloseClient: 16
D [05/Nov/2007:23:35:14 -0500] cupsdAcceptClient: 16 from localhost:631 (IPv4)
D [05/Nov/2007:23:35:14 -0500] cupsdReadClient: 16 GET / HTTP/1.1
D [05/Nov/2007:23:35:14 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:14 -0500] cupsdReadClient: 16 GET /cups.css HTTP/1.1
D [05/Nov/2007:23:35:14 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:14 -0500] cupsdReadClient: 16 GET /favicon.ico HTTP/1.1
D [05/Nov/2007:23:35:14 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:14 -0500] cupsdReadClient: 16 GET /images/top-left.gif HTTP/1.1
D [05/Nov/2007:23:35:14 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:14 -0500] cupsdAcceptClient: 18 from localhost:631 (IPv4)
D [05/Nov/2007:23:35:14 -0500] cupsdReadClient: 18 GET /images/top-middle.gif HTTP/1.1
D [05/Nov/2007:23:35:14 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:14 -0500] cupsdReadClient: 16 GET /images/top-right.gif HTTP/1.1
D [05/Nov/2007:23:35:14 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:14 -0500] cupsdReadClient: 18 GET /images/tab-left.gif HTTP/1.1
D [05/Nov/2007:23:35:14 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:14 -0500] cupsdReadClient: 16 GET /images/tab-right.gif HTTP/1.1
D [05/Nov/2007:23:35:14 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 18 GET /images/button-help.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 16 GET /images/button-add-class.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 18 GET /images/button-add-printer.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 16 GET /images/button-manage-classes.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 18 GET /images/button-manage-jobs.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 16 GET /images/button-manage-printers.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 18 GET /images/button-manage-server.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 16 GET /images/happy.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 18 GET /images/bottom-left.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:15 -0500] cupsdReadClient: 16 GET /images/bottom-right.gif HTTP/1.1
D [05/Nov/2007:23:35:15 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:20 -0500] cupsdReadClient: 18 GET /admin/ HTTP/1.1
D [05/Nov/2007:23:35:20 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:20 -0500] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 9751
I [05/Nov/2007:23:35:20 -0500] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=9751)
D [05/Nov/2007:23:35:20 -0500] cupsdSendCommand: 18 file=19
D [05/Nov/2007:23:35:20 -0500] [CGI] admin.cgi started...
D [05/Nov/2007:23:35:20 -0500] cupsdAcceptClient: 20 from localhost (Domain)
D [05/Nov/2007:23:35:20 -0500] [CGI] http=0x80790d0
D [05/Nov/2007:23:35:20 -0500] [CGI] No form data, showing main menu...
D [05/Nov/2007:23:35:20 -0500] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [05/Nov/2007:23:35:20 -0500] cupsdReadClient: 20 POST / HTTP/1.1
D [05/Nov/2007:23:35:20 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:20 -0500] Get-Subscriptions ipp://localhost/
D [05/Nov/2007:23:35:20 -0500] Get-Subscriptions client-error-not-found: No subscriptions found.
D [05/Nov/2007:23:35:20 -0500] cupsdProcessIPPRequest: 20 status_code=406 (client-error-not-found)
D [05/Nov/2007:23:35:20 -0500] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [05/Nov/2007:23:35:21 -0500] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [05/Nov/2007:23:35:21 -0500] cupsdReadClient: 16 GET /images/button-find-new-printers.gif HTTP/1.1
D [05/Nov/2007:23:35:21 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:21 -0500] cupsdReadClient: 16 GET /images/button-edit-configuration-file.gif HTTP/1.1
D [05/Nov/2007:23:35:21 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:21 -0500] cupsdReadClient: 16 GET /images/button-view-access-log.gif HTTP/1.1
D [05/Nov/2007:23:35:21 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:21 -0500] cupsdReadClient: 16 GET /images/button-view-error-log.gif HTTP/1.1
D [05/Nov/2007:23:35:21 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:21 -0500] cupsdReadClient: 16 GET /images/button-view-page-log.gif HTTP/1.1
D [05/Nov/2007:23:35:21 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:22 -0500] [CGI] lang="en_US.UTF-8", locale="/en_US"...
D [05/Nov/2007:23:35:22 -0500] cupsdCloseClient: 20
D [05/Nov/2007:23:35:22 -0500] cupsdReadClient: 16 GET /images/button-change-settings.gif HTTP/1.1
D [05/Nov/2007:23:35:22 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:22 -0500] PID 9751 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [05/Nov/2007:23:35:22 -0500] cupsdReadClient: 18 GET /images/button-add-rss-subscription.gif HTTP/1.1
D [05/Nov/2007:23:35:22 -0500] cupsdAuthorize: No authentication data provided.
D [05/Nov/2007:23:35:24 -0500] cupsdReadClient: 16 GET /admin/log/error_log HTTP/1.1
D [05/Nov/2007:23:35:24 -0500] cupsdAuthorize: No authentication data provided.

---

### Post by jmagsho on 2007-11-09
As an FYI for anyone who might be interested, this has been logged as bug # 145772 in Launchpad. ([https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/145772](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/145772))

---

