---
title: "Cups web interface - not authorised on add printer"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by Windowsxpnomore on 2014-09-21
There is only one user called rodney on the system
These are my steps.
Format hd with gpart.
Installed 14.04.01 from cd (this is the SERVER addition)
installed webmin
updated all the packages.
installed cups
installed samba
connected the canon printer (type of printer does not matter yet).
Got the cups web interface runnings:
this is my cupd.conf currently.

```
#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn
DefaultEncryption Never

SystemGroup lpadmin

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Only listen for connections from the local machine.
Port 631
Listen /var/run/cups/cups.sock
Listen 192.168.0.2:631

# Show shared printers on the local network.
Browsing On
BrowseLocalProtocols dnssd

# Default authentication type, when authentication is required...
DefaultAuthType none

# Web interface setting...
WebInterface Yes

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow all
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow all
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user valid-user
  Order allow,deny
  Allow All
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#
```


on the server 
getent group lpadmin returns:
lpadmin:x:110:rodney

adduser rodney lpadmin returns:
The user 'rodney' is already a member of 'lpadmin'

The problem I have is on CUP web interface If I goto Add Printer I get UnAuthorised.
likewise the same if I try and save the config cupsd.conf
I restart cups each time - even rebooting the server 
I have googled and tried out many things (hence the conf above many include things not required) - but I cannot get it to work.

many thanks

---

### Post by ajgreeny on 2014-09-21
I assume you as user are able to use sudo for other commands?

If so, you should get a dialog box pop up asking for your user password, as for other root permission requiring activities.

---

### Post by Windowsxpnomore on 2014-09-21
No there is no web prompt for username or password.

---

### Post by Windowsxpnomore on 2014-09-22
as an update to this If I change this 
DefaultAuthType none
to
DefaultAuthType Basic
it will prompt for a password.
however with only 1 user defined and no way to sudo there I am still stuck

---

### Post by ajgreeny on 2014-09-22
Have you in some way or other set your system to work with no password at all?  I do not mean just autologin, but perhaps without password set, if that is even possible?

---

