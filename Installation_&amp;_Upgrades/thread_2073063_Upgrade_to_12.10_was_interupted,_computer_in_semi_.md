---
title: "Upgrade to 12.10 was interupted, computer in semi workable condition"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by qedprigmosynois on 2012-10-18
Hi, I was doing an upgrade today on my 12.04 to 12.10 and for some reason during the upgrade, the power in my laptop went out. When I went to turn it on, the laptop ended up in a powerhogging, i think error prone mode, but I can still run 12.10 on it.  Now I've tried to get someone to help me before and he had me use dpkg, apt-get upgrade, apt-get update and everything went smoothly. But I still get popups saying tehre are system errors, everything is really slow and I keep getting this when i go to the debug client [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925760](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925760))  I think the installation wasn't cleaned up and some packages werent install. Anyone know how I can fix this?

---

### Post by cybrsaylr on 2012-10-18
Seems like your install got messed up.
I would simply reinstall and start over again.

---

### Post by qedprigmosynois on 2012-10-18
well so far, i think everything is working ok. I just did some automated uninstalls, other dpkg and configures and the result is that my computer  has improved power performance (fans are whirring like crazy) and works. What I do notice as problems is that it takes forever to get to the login screen and then to the desktop and I get "system program problems" which the client tells me to send a report for but does not tell me what is wrong. So mostly the install probably worked.

---

### Post by williejones on 2012-10-18
You should install Synaptics Package Manager.  It has an option to fix broken packages. To install:

```
sudo apt-get install synaptic
```

To run click the Dash (the top button and type synaptic)

---

### Post by williejones on 2012-10-18
Forgot to mention to fix broken packages in Synaptic Package Manager, select Edit (on top) then, fix broken packages.

---

### Post by qedprigmosynois on 2012-10-19
oh i love you, this pretty much fixed everything. There were no broken packages but there were indeed recommended packages that werent installed. After install with synaptic, working like the ole' ubuntu. Thanks :D

---

