---
title: "Ubuntu server 12.04 lts  Openssh"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by paul212 on 2015-06-11
I am running a SFTP Ubuntu server 12.04 lts.  What is the latest Openssh that I can install on this server?  My monthly security scans are failing because I am not on Openssh version 6.6 or higher.  I have done the apt-get update and it is only getting me to version 5.9.  how do I get to a higher version of Openssh?

---

### Post by papibe on 2015-06-11
Hi paul212. Welcome to the forums ):P

It is v5.9 + security patches. Not the latest in terms of features (which I think there's not many), but updated/patched with all important security patches.

You could look around for a ppa to upgrade. That way you could get the latest, however in terms of security updates, you would be at the mercy of the person packaging the ppa.

If you really need v6.6 (say because of a particular feature), I'd recommend upgrading to Trusty 14.04 which has v6.6.

Does that help? Let us know how it goes.
Regards.

---

### Post by Lars Noodén on 2015-06-11
You can read more about the individual patches on the Launcpad page for the package:

[https://launchpad.net/ubuntu/+source/openssh](https://launchpad.net/ubuntu/+source/openssh)

---

### Post by paul212 on 2015-06-11
Thank you for the information.   Looks like an upgrade to 14.04 lts.

---

### Post by Lars Noodén on 2015-06-12
> **paul212 said:**
> Thank you for the information.   Looks like an upgrade to 14.04 lts.

Not really, unless you really want to.  The Launchpad page shows that 5.9 for 12.04 has been kept up to date with security patches.  The scanner software needs some tuning instead.

---

