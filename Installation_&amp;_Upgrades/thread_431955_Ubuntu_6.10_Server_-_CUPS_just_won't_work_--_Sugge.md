---
title: "Ubuntu 6.10 Server - CUPS just won't work -- Suggestions?"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by samalex on 2007-05-03
Hi Everyone,

I installed an Ubuntu 6.10 Server, and now I'm trying to setup CUPS to print directly to network printers (HP Laserjet 5n's to be exact).  I installed CUPS and LPR:
apt-get install cupsys
apt-get install cupsys-client
apt-get install lpr

Then using Webmin I configured CUPS and added a printer.  After working with it for a better part of the afternoon and trying various things online, here's what I have for the cupsd.conf and printers.conf files:

```

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
  Allow 10.142.104.55
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

```

and 

```

<DefaultPrinter WebmasterPTR>
Info WebmasterPTR
DeviceURI socket://10.142.104.180:9100
State Idle
Accepting Yes
</Printer>

```

My PC is 10.142.104.55 and the printer is 10.142.104.104.  I can ping the printer just fine from the Linux server, and the printer is working as I can print to it from my WIndows XP workstation just fine, also printing directly to the printer via IP.

What am I missing?  When I try to send a printjob to the printer, whether through Webmin or do something like this 'ls | lpr -PWebmasterPTR' the job just sits in the queue and never goes to the printer.  

Am I missing something?  I'm not sure if this is a permissions issue, if I'm missing a service, or what.  

Thanks for any insight.  Most of the HOW-TOs I read show doing all this via GUI, but being this is installed from Ubuntu Server there is no GUI installed.  I've setup CUPS before, well rather taken defaults on other distros, and all has worked as it should.  I'm not sure what's happening in this case.

As for what we want to print, I dont' really need network printing (from workstations to this server), rather I'll be writing scripts locally on the LInux server to print to various network printers. 

Thanks for your time and help with this, and take care --

Sam
[email]samalex@gmail.com[/email]

---

### Post by samalex on 2007-05-03
Hello Everyone,

Well I'm closer to getting this working.  I finally got the CUPS web administrator to work, so now I can connect to my server on port 631 and configure CUPS.  From here I can setup my printer and print a test page with no issues, but though this is working, from command line I'm still having some issues.

I'm not sure what the difference is between lp and lpr, but I can send print jobs to the printer using lp, but not lpr.  Not that this is a big issue, but can someone explain the difference between this programs?  It seems most examples I see for printing in command line want to use lpr.

Here's what happens, if I do for example 'ls | lp' I get a printout of the files.  I have set my network printer in CUPS to default, so this is as expected.  However if I do 'ls | lpr' I get unknown printer.  My printer is called WebmasterPrinter, and if I do this instead 'ls | lpr -P WebmasterPrinter' it returns with no error.  Could lpr be looking at the wrong thing, or does lpr not work with CUPS?

Sorry for all the questions, but I'm really trying to figure this out. 

Thanks ...

Sam

---

