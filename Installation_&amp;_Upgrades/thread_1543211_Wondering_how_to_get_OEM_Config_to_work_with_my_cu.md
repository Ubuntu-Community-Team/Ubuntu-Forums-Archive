---
title: "Wondering how to get OEM Config to work with my custom distro"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by AZorin on 2010-07-31
Hello!
I'm not sure how to get the OEM install mode working with my Ubuntu remaster. I'm using Remastersys to make the remastered Ubuntu 10.04 and I don't know how to make sure OEMs can use it. I have tried running sudo oem-config-prepare after installing the remaster (with oem-config, oem-config-gtk, oem-config-remaster and oem-config-debconf installed from Synaptic) in a new account called "oem" with the password also "oem". It tells me that I have to restart to show the system setup. So I did that, but it would not start into it. I pressed the Escape key at Plymouth to view the bootup in verbose mode and it told me this:
```
Traceback (most recent call last):
File "/usr/bin/ubiquity-dm", line 476, in <module>
  dm = DM(vt, display, username)
File "/usr/bin/ubiquity-dm", line 78, in __init__
  self.uid, self.gid = pwd.getpwnam(self.username)[2:4]
KeyError: 'getpwnam(): name not found: live'
```
multiple times and that I could make a new account from the boot prompt. I attempted to do this but it was choppy and my key presses didn't appear to do anything until I pressed Enter when it displayed only some of the key presses so setting up an account from the boot prompt was futile. 
I really need this to work as soon as possible!

Best regards,
AZorin

---

### Post by TwistedLincoln on 2010-09-26
I know this is an old thread, but just in case anyone else runs into the same problem:

The solution is to specify the live cd's username as "oem" in Remastersys when you create the ISO.  I have no idea why this matters, but apparently it does.

---

