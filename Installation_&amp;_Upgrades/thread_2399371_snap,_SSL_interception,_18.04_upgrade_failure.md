---
title: "snap, SSL interception, 18.04 upgrade failure"
date: 2018-08-24
forum: Installation &amp; Upgrades
---

### Post by GovDude on 2018-08-24
I thought I'd try the upgrade from 16.04 to 18.04 today. Unfortunately I didn't get very far. I'm getting the following warning/error:

[B][FONT=courier new]Your system does not have a connection to the Snap Store...
Do you still want to continue with the upgrade? 

Continue [yN] 
[/FONT][/B]
After some Google searching I've come to suspect that this has to do with the fact that my workstation sits behind our corporate firewall which includes SSL interception. I did a "snap install hello-world" and received

[B][FONT=courier new]error: cannot install "hello-world": Post [https://api.snapcraft.io/v2/snaps/refresh:](https://api.snapcraft.io/v2/snaps/refresh:) x509:
       certificate signed by unknown authority
[/FONT][/B]
This would seem to validate my suspicion. Is there any way to get around this issue?

TIA

---

### Post by TheFu on 2018-08-24
I would test it inside a virtual machine.  See what happens.   

[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) has some background.

I'm not a fan of snaps for a few reasons.
Good question. Thanks.

---

### Post by GovDude on 2018-08-24
@TheFu gave me a new chain of things to follow and it turns out that [https://bugs.launchpad.net/snappy/+bug/1533899/comments/1](https://bugs.launchpad.net/snappy/+bug/1533899/comments/1) fixed my problem. Note that I had defined my proxies in both my login shell, via *export http[s]_proxy* **and** in /etc/environment and that didn't solve the problem. But setting the proxies in the file referenced in the link did fix it.

---

