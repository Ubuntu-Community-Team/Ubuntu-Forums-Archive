---
title: "New Printer grayed out"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nutmac on 2009-09-16
I am trying to add a networked printer (on Windows network). On 9.04, all I had to do is hit Ctrl+N in Printing admin tool (system-config-printer). On the latest 9.10, it seems I need to specify the CUPS server, which inevitably triggers "There was an error during the CUPS operation: 'client-error-not-found'" CUPS server error dialog box.

Anyone?

---

### Post by orlox on 2009-09-16
> **nutmac said:**
> I am trying to add a networked printer (on Windows network). On 9.04, all I had to do is hit Ctrl+N in Printing admin tool (system-config-printer). On the latest 9.10, it seems I need to specify the CUPS server, which inevitably triggers "There was an error during the CUPS operation: 'client-error-not-found'" CUPS server error dialog box.

Anyone?

I've had some problems with some karmic updates where my cups configuration file dissapeared, so cups didn't even start...Could you post the contents of your /etc/cups/cupsd.conf??

---

### Post by nutmac on 2009-09-16
LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
Listen localhost:631
Listen /var/run/cups/cups.sock
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  Order allow,deny
</Location>
<Location /admin>
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
Require user @OWNER @SYSTEM
Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
  AuthType Default
  Require user @SYSTEM
  Order deny,allow
    </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
      </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
      Require user @OWNER @SYSTEM
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>
RIPCache 2013406k

---

### Post by orlox on 2009-09-16
Seems your issue is different from what I had. In my case the file was actually empty. I would reccomend this to you:

[LIST]
[*]Use the web interface and see if it also fails. You can access it at [http://localhost:631/](http://localhost:631/)
[*]Try to reestart cups by running the command:
> 
sudo /etc/init.d/cups restart

and see if there's any problem in starting cups.
[/LIST]

---

### Post by nutmac on 2009-09-23
> **orlox said:**
> Seems your issue is different from what I had. In my case the file was actually empty. I would reccomend this to you:

[LIST]
[*]Use the web interface and see if it also fails. You can access it at [http://localhost:631/](http://localhost:631/)
[*]Try to reestart cups by running the command:

and see if there's any problem in starting cups.
[/LIST]

Thanks, that worked (along with apt-get upgrade).

---

