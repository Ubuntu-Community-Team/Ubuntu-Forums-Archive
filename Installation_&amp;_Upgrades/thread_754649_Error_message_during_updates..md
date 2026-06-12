---
title: "Error message during updates."
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by Enigmacat on 2008-04-14
Aaaarrrrrrggggg!!!!! :mad:

Every time the install a program I get some kind of error message. Even for updates. Whats the deal!?! :confused:

1st error: 

  E: hl1650lpr: subprocess post-installation script returned error exit status 127

2nd error:

   dpkg: error processing hl1650lpr (--configure):
                    subprocess post-installation script returned error exit status 127
                    Errors were encountered while processing:
                    hl1650lpr

The 1st error came from the Add/Remove
The 2nd error came while working in the Terminal
I now that I am new to this, yes I'm a noob, but come on this is crazy. What can I do to correct this?

---

### Post by AdamG51172 on 2008-04-14
This shows a problem with part of a package for a printer driver.  Do you have a brother printer?  If not then you should be able to just uninstall this package by :
```
sudo apt-get remove brother-lpr-drivers-laser1
```
and go on your merry way.  If you _do_ have a Brother device, then I can only suggest searching the forums for your model to see what the community has to say.

---

### Post by riftheripper on 2008-04-14
Hi!

I get a similar error trying to run the update manager:

'E:Pakken hl1650lpr skal geninstalleres, men jeg kan ikke finde noget arkiv med den.'

which in English would be something like:

E:Package hl1650lpr must be reinstalled, but I cannot find any archive with it

Any suggestions?!!!

Riftheripper - newcomer:confused:

---

### Post by bapoumba on 2008-04-14
@ riftheripper: it means the repositories for that package are missing from your /etc/apt/sources.list
Where did you install it from? I canno find it in the regular ubuntu repos.

---

### Post by AdamG51172 on 2008-04-14
It's part of the package "brother-lpr-drivers-laser1" in the multiverse and is a printer driver for Brother model hl1650.

---

