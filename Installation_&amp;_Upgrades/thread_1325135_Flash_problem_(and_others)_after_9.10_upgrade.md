---
title: "Flash problem (and others) after 9.10 upgrade"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Justin Pentecost on 2009-11-13
I upgraded from 9.04 to 9.10 via the update manager . 
Initially I had problem with the internet connection that was solved via this site .. 

Then I went to the BBC for my weekly dose of HUT 33.   The browser told me to "Install Adobe flash" which the Software centre told me was installed .. 

So I uninstalled it .. and tried to reinstall it .. 

first it stuck at 82% ..

Now all I get is a message that says "Waiting for other software managers to quit" .. 

Additional stuff .. 

I've restarted the computer several times .. 
Package manager will not start due to an error ..

Anyone else had this problem ?

---

### Post by HannuMR on 2009-11-13
This allready tried in terminal?

sudo apt-get install ubuntu-restricted-extras

And these?

sudo apt-get update
sudo apt-get remove swfdec-mozilla
sudo apt-get install flashplugin-installer

---

### Post by Justin Pentecost on 2009-11-13
Thanks .. That has mvoed things along .. 

I tried the first apt-get ... and then followed the instructions ..

justin@HOME:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for justin: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
justin@HOME:~$ sudo dpkg --configure -a
Setting up flashplugin-installer (10.0.32.18ubuntu1) ...
Downloading...
--2009-11-13 16:29:45--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.32.18.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.32.18.orig.tar.gz)
Resolving archive.canonical.com... 1.0.0.0
Connecting to archive.canonical.com|1.0.0.0|:80... 

This suggests that for whatever reason I have no DNS lookup .. I have DNS with Firefox and Thunderbird .. but my guess is that it does not work for APT-GET ...

anyone have anymore ideas ?

---

