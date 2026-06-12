---
title: "synaptic cant connect"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by John Melbourne on 2007-07-18
I've never used linux, so as a trial I've installed Ubuntu 5.10 on a very old machine. (I've tried to load the later versions but without success - possibly due to very old graphics hardware). I've got 5.10 up and running and got firefox to run by disabling IPv6. 

I know the repositories are no longer available in the normal place and so have edited the entries in synaptic to point to old-releases.unbuntu.com/unbuntu  and so on

Synaptic, however returns the message 
 "... . Could not connect to old-releases.unbuntu.com: 80 (1.0.0.0) "   when attempting to check  old-releases.unbuntu.com/unbuntu/dists/breezy/Release.gpg .

Firefox has no problem getting to (and reading) the file.  Is there some synaptic setting I need to change?

---

### Post by wpshooter on 2007-07-18
My suggestion would be that you download, burn and install a slightly newer version of Ubuntu - say 6.06.1 Dapper Gnome.

---

### Post by Basie on 2007-07-18
Does the latest Ubuntu version 7 include the latest Debian 4.0 packages?
 Or is that a totally separate Entity?  I think I have Dapper Gnome right now.

---

### Post by John Melbourne on 2007-07-20
On the basis that the problem was with synaptic not being able to route to the DNS I had a thought.

In synaptic  used settings-preferences-network Manual Proxy and set the HTTP proxy to 91.189.89.3 (the IP address of old-releases.ubuntu.com).

RESULT fast connect and some 200MB of update.

CONCLUSION Synaptic not correctly polling the DNS , possibly it is using IPv6 similar to Firefox.  Is there a Synaptic internal option variable which can be set to change this?

---

