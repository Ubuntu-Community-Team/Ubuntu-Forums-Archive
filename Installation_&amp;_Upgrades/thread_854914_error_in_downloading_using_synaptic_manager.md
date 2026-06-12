---
title: "error in downloading using synaptic manager"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by arturieto on 2008-07-09
I got this error when using the synaptic pacakge manager :

"E: havp: subprocess post-installation script returned error exit status 1"

Even updates from repositories can not be installed.  I got this error after I removed antivirus, clamav, avast home edition linux and avg for linux.

I tried re-installing synaptic and tried also the havp but nothing happened.

please help.

---

### Post by iaculallad on 2008-07-09
What messages/error will it display when you issue the following commands on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Dunchillin on 2008-11-04
Hi guys.
I'm having the same problem.  Have followed the advice on both threads I found but no joy.
Following the advice in this thread I get:

Do you want to continue [Y/n]? y
Setting up havp (0.86-1build1) ...
There is already /var/lib/havp/havp.loop, maybe from an earlier or custom installation, not building loopback-device
Starting havp: Starting HAVP Version: 0.86
LibClamAV Error: cl_loaddbdir(): Can't get status of /var/lib/clamav/
One or more scanners failed to initialize!
Check errorlog for errors.
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)

I was trying to install GnuCash when I started getting the "no havp" messages.  Now it says I have a /havp/havp.loop but I don't have the foggiest idea what that means!

Help vastly appreciated :)

---

### Post by zvacet on 2008-11-05
```
sudo dpkg --configure -a
```

---

### Post by Dunchillin on 2008-11-05
sudo dpkg --configure -a
[sudo] password for john: 
Setting up havp (0.86-1build1) ...
There is already /var/lib/havp/havp.loop, maybe from an earlier or custom installation, not building loopback-device
Starting havp: Starting HAVP Version: 0.86
LibClamAV Error: cl_loaddbdir(): Can't get status of /var/lib/clamav/
One or more scanners failed to initialize!
Check errorlog for errors.
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp

---

### Post by Dunchillin on 2008-11-12
Any more ideas on this anyone? Please?!
Basically no updates or packages will install at all.  On looking I discover I have about 4 or 5 folders called 'havp' but they all seem to have different contents.
Every upgrade/package comes back with:
> subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
havp

---

