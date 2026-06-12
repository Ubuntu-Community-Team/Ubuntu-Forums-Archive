---
title: "Lucid to Maverick using ssh; lost connection halfway through"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by sylae on 2010-12-11
Okay, so I was upgrading Ubuntu to 10.10 via ssh. I did the do-release-upgrade and it told me doing it via ssh was a bad idea and it'd open another sshd on port 1022. I said okay and went on with the upgrade. It downloaded fine and started upgrading. It looked like it was doing fine, so I went away for a bit. When I came back about an hour later, my ssh client said it had lost the connection. Stupid wireless adapter on the client machine had decided to turn off.

So I reopened my ssh client and reconnected. Connected fine, so I figured I'd just use apt-get to upgrade. It gave me the following:
```
$sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
This leads me to assume that somewhere in Ubuntu there was an sshd session sitting waiting for me to do some configuration thing for the upgrade to continue. Anywho, I have no idea how to get to this session. Is there some way to do that? Should I just restart the machine being upgraded? Is anything going to be broken?

---

### Post by papenpj on 2011-01-23
Did you ever get this figured out? I was trying to upgrade my server from 8.04 to 10.4 and got the timeout.  I can reconnect on the port I was using, and the one the upgrade created but I don't know how to the window I was using to finish the upgrade.


sudo do-release-upgrade

just tells me 

"Unable to get exclusive lock

This usually means that another package management application (like
apt-get or aptitude) already running. Please close that application
first."

---

