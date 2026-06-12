---
title: "Authenticating the Upgrade Failed 13.04 &gt; 13.10"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by ncweber on 2013-10-21
I am attempting to upgrade Ubuntu from 13.04 to 13.10 on my Acer Aspire One D255E-2659 netbook.  First, I used the Software Updater.  I get as far as the do-release-upgrade downloading two files.  Then, the window disappears and nothing further occurs.  So I decided to try the command line.

I typed ```
sudo do-release-upgrade
``` in Terminal and it returned the following:

```
Checking for a new Ubuntu release
Get:1 Upgrade tool signature                                                                                    
Get:2 Upgrade tool                                                                                              
Fetched 7,872 B in 0s (0 B/s)                                                                                   
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg' 
gpg exited 2
Debug information: 


gpg: no valid OpenPGP data found.
gpg: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.

```

Does anyone have an idea as to why this occurs?  My network connection is sound as I was able to run software updates before attempting to upgrade the distribution.  Is there a problem with the authentication on my system, or is it on the server end?

I am inclined to think that the problem is on my machine as I was able to smoothly upgrade my full sized laptop, another Acer, with no trouble at all.  Any assistance is greatly appreciated.

---

### Post by ncweber on 2013-10-25
UPDATE: As it turns out, the problem was the network I was on.  My full sized laptop was able to upgrade because I performed the upgrade at home where I have full control of the network.  I was attempting to upgrade my netbook at work.  I assumed I could upgrade because regular package updates work fine there, but apparently, the firewall is blocking the upgrade process.  I tried upgrading my netbook at home and everything worked fine.

So, be aware of the network you're on when upgrading.

---

