---
title: "ubuntu remote printing via cups"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by srstaff on 2006-11-22
Dapper LAMP server with HP PSC 950 multifunction printer connected via USB... WINS server 192.168.1.150 hostname is ubuntu

cupsd.conf:

# Show general information in error_log.
LogLevel info
SystemGroup shadow
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
#BrowseAddress @LOCAL
BrowseAddress 192.168.1.255
DefaultAuthType Basic

<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
  Allow From 192.168.1.101
  Allow From 192.168.1.103
</Location>

<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
  Allow From 192.168.1.101
  Allow From 192.168.1.103
</Location>

<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /printers>
  AuthType None
  Order Deny,Allow
  Deny From None
  Allow From All
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  # Only the owner or an administrator can cancel a job...
  <Limit Cancel-Job>
    Order deny,allow
    Require user @OWNER @SYSTEM
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

# Allow remote access
Port 631
#Listen /var/run/cups/cups.sock



Remote pc with Xubuntu Desktop network address is 192.168.1.103

client.conf:

ServerName 192.168.1.150

I added a printer on the client machine via the CUPS admin page using the URL http:\\192.168.1.150\printer\HP_PSC_900_Series_USB_1 and using the PPD that I got from linuxprinting.org for this HP printer

Says it adds printer successfully, but when I print a test page, I get:

-12345X@PJL ENTER LANGUAGE=PCL3
17H10M12Ao0M1-2Hu300D10L148D14E16Dp0Xg26WXX,,,,,,r1Ab2Mp0Yb10V

It has taken me awhile to even get to the point I could add the printer to the remote machine and get ANYTHING across the network to the printer, but now I'm at a loss as to why a testpage comes out as jibberish.  Does anyone have any ideas which part of this tenuous chain of moving parts might be awry?

Regards,
srstaff

---

### Post by srstaff on 2006-11-23
Perhaps it is also worth noting that I am able to print just fine from a remote windows xp home machine.... just not the remote xubuntu machine.

Please advise

srstaff

---

### Post by srstaff on 2006-11-23
I'm thinking since i have connectivity to the printer server on dapper, that it must be either an issue of the protocol? (whether the remote printer URL uses ipp:, http:, lpd: or suchlike) or perhaps something to do with the drivers (.ppd file?)??

I never was able to get the remote printer to show on client box cups admin page as a network printer found... perhaps if i can figure out how to adjust my settings so it shows up there, it will be able to auto-add with correct configs?

Surely someone has an idea... i have googled and read forums for 2 days now and tried numerous things, but based on my knowledge level its a bit like trying to solve a rubic's cube in the dark...

thx again,

srstaff

---

### Post by markertd on 2006-11-25
srstaff,

there is currently a bug in cupsys version 1.2.2-0ubuntu0.6.06.
This bug leads to your printer output

[INDENT]-12345X@PJL ENTER LANGUAGE=PCL3
17H10M12Ao0M1-2Hu300D10L148D14E16Dp0Xg26WXX,,,,,,r1Ab2Mp0Yb10V[/INDENT]

You can try to follow the hints from thread

[http://ubuntuforums.org/showthread.php?t=232996](http://ubuntuforums.org/showthread.php?t=232996)

Dirk

---

