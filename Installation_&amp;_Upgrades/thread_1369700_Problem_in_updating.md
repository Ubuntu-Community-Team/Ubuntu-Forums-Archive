---
title: "Problem in updating"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by hbsq on 2010-01-01
Hi all

I couldn't update my system Ubuntu 9.04 for 10 days, I don't know what is the solution, I am a fresh user of Ubuntu. 

[img]http://farm3.static.flickr.com/2796/4218847251_5f6d466605_o.png[/img]

when I tried to update thru Terminal, I got the following msg.

> hbsqn@hbsqn-laptop:~$ sudo apt-get update
[sudo] password for hbsqn: 
Hit Ubuntu Security Notices | Ubuntu jaunty-security Release.gpg
Hit Index of / jaunty Release.gpg 
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release.gpg [197B] 
Hit Index of / jaunty-getdeb Release.gpg 
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release.gpg 
Get:2 Index of / jaunty Release.gpg [307B] 
Get:3 Google Pack stable Release.gpg [189B] 
Ign Index of / jaunty/main Translation-en_US 
Hit Index of / jaunty Release.gpg 
Hit The Opera .deb Repository stable Release.gpg 
Ign Google Pack stable/main Translation-en_US 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Translation-en_US 
Get:4 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release [3454B] 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release 
Hit [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Packages 
Get:5 Google Pack stable Release [2540B] 
Ign Index of / jaunty-getdeb/apps Translation-en_US 
Ign Index of / jaunty/main Translation-en_US 
Get:6 Google Pack stable/main Packages [867B] 
Hit Index of / jaunty-getdeb Release 
Ign Ubuntu Security Notices | Ubuntu jaunty-security/main Translation-en_US 
Get:7 Index of / jaunty Release [74.6kB] 
Ign Index of / jaunty Release 
Ign The Opera .deb Repository stable/non-free Translation-en_US 
Ign Index of / jaunty/main Translation-en_US 
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Translation-en_US 
Hit The Opera .deb Repository stable Release 
Hit Index of / jaunty-getdeb/apps Packages 
Hit Index of / jaunty Release 
Ign Ubuntu Security Notices | Ubuntu jaunty-security/restricted Translation-en_US 
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release 
Hit Index of / jaunty/main Packages 
Ign The Opera .deb Repository stable/non-free Packages 
Hit Index of / jaunty/main Sources 
Ign Index of / jaunty/restricted Translation-en_US 
Hit Index of / jaunty/main Packages 
Ign Ubuntu Security Notices | Ubuntu jaunty-security/universe Translation-en_US 
Hit The Opera .deb Repository stable/non-free Packages 
Ign Index of / jaunty/universe Translation-en_US 
Ign Ubuntu Security Notices | Ubuntu jaunty-security/multiverse Translation-en_US
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages 
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages 
Ign Index of / jaunty/multiverse Translation-en_US
Get:8 Index of / jaunty-updates Release.gpg [189B]
Hit Ubuntu Security Notices | Ubuntu jaunty-security Release
Ign Index of / jaunty-updates/main Translation-en_US
Hit Ubuntu Security Notices | Ubuntu jaunty-security/main Packages
Hit Ubuntu Security Notices | Ubuntu jaunty-security/restricted Packages
Ign Index of / jaunty-updates/restricted Translation-en_US
Ign Index of / jaunty-updates/universe Translation-en_US 
Ign Index of / jaunty-updates/multiverse Translation-en_US
Hit Ubuntu Security Notices | Ubuntu jaunty-security/main Sources
Hit Index of / jaunty Release 
Hit Ubuntu Security Notices | Ubuntu jaunty-security/restricted Sources 
Hit Ubuntu Security Notices | Ubuntu jaunty-security/universe Packages 
Get:9 Index of / jaunty-updates Release [57.9kB] 
Err Index of / jaunty-updates Release 

Hit Index of / jaunty/main Packages 
Hit Index of / jaunty/restricted Packages 
Hit Index of / jaunty/main Sources 
Hit Index of / jaunty/restricted Sources 
Hit Ubuntu Security Notices | Ubuntu jaunty-security/universe Sources 
Hit Ubuntu Security Notices | Ubuntu jaunty-security/multiverse Packages 
Hit Ubuntu Security Notices | Ubuntu jaunty-security/multiverse Sources 
Hit Index of / jaunty/universe Packages 
Hit Index of / jaunty/universe Sources 
Hit Index of / jaunty/multiverse Packages 
Hit Index of / jaunty/multiverse Sources 
Fetched 4292B in 8s (523B/s) 
Reading package lists... Done
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: Index of / jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0D3C959DB2035A6
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: Index of / jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://qa.archive.ubuntu.com/ubuntu/...pdates/Release](http://qa.archive.ubuntu.com/ubuntu/...pdates/Release) 

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by raymondh on 2010-01-01
In terminal ... (let's work on the pubkey error)...one at a time:

```
gpg --keyserver subkeys.pgp.net --recv DCF9F87B6DFBCBAE
```

```
gpg --export --armor DCF9F87B6DFBCBAE | sudo apt-key add -
```

```
sudo apt-get update
```

I inlcuded the first pubkey in the codes above.  Do that format for the next pubkey you see.  You can also use the last 8 digits of the key.

Post back errors.

---

### Post by warfacegod on 2010-01-01
I'm having a similar issue. I'm not getting any error messages, however, Update Manager hasn't shown me any new updates in well over a week.

It looks like part of you're problem is that you installed packages from ppa's and either didn't get or erased the keys for them. It also looks like you *might* be having issues with connectivity.

---

### Post by hbsq on 2010-01-01
Dear raymondh,

thanks a lot for your early reply, I already tried to do what you advised me to do for these two Pubkey DCF9F87B6DFBCBAE & D0D3C959DB2035A6

but after I run sudo apt-get update I got same problem.

---

### Post by mr clark25 on 2010-01-01
it sounds like the software source doesnt have what you need?

maybe you culd change the software source?

---

### Post by hbsq on 2010-01-01
> **mr clark25 said:**
> it sounds like the software source doesnt have what you need?

maybe you culd change the software source?

Mr. Clark, I am just a fresh user in Ubuntu, woudl u please explain to me what to do and how??:)

---

### Post by raymondh on 2010-01-01
I am using 9.04.

System > software sources > ubuntu software > Download from (and choose a different site) > close synaptic

Then run in terminal again

sudo apt-get update
sudo apt-get upgrade

PS. I normally ask my system to select OTHER and then 'selct best available source'.

Regards,

---

### Post by hbsq on 2010-01-02
unfortunately, I went to Software sources and tried to delete the third party software but it is shown up again every time I press Revert.

then I deleted the keys D0D3C959DB2035A6 & 40976EAF437D05B5 from Software window then Authentication.

---

### Post by hbsq on 2010-01-02
Reminder, thanks everybody

---

### Post by Shazaam on 2010-01-02
> **hbsq said:**
> unfortunately, I went to Software sources and tried to delete the third party software but it is shown up again every time I press Revert.

then I deleted the keys D0D3C959DB2035A6 & 40976EAF437D05B5 from Software window then Authentication.

Try it without pressing "Revert".
And yes, there have been no updates for about a week. Holidays and all probably so I wouldn't worry.

---

