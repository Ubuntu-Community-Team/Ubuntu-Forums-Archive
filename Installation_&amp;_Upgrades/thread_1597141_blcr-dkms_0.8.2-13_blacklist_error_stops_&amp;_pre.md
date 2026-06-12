---
title: "blcr-dkms_0.8.2-13 blacklist error stops &amp; prevents upgrade"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by CyborgAlpha on 2010-10-15
Following the instructions, I get to a little after "setting software channels" and a **blcr-dkms_0.8.2-13** blacklist error pops-up and ends the installation. :confused:

---

### Post by tdgs on 2010-10-15
Same thing here.

---

### Post by bagvian on 2010-10-16
Dear All,
I seems that I also encounter the same kind of problems.

Following Ubuntu 10.10 relase, I have been trying to upgrade from 10.04 to 10.10 on my amd64 laptop. Everything starts as it should but when the system starts the following action :
“Setting new software channels”
A new message bax pops up saying :

Could not calculate the upgrade



An unresolvable problem occurred while calculating the upgrade:

Trying to install blacklisted version 'blcr-dkms_0.8.2-13'



 This can be caused by:

 * Upgrading to a pre-release version of Ubuntu

 * Running the current pre-release version of Ubuntu

 * Unofficial software packages not provided by Ubuntu



If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Finally, you can only press “Close” and this is how the upgrade ends up!
To be more precise, I am neither upgrading to a pre-release nor currently running a pre-release (my current install is a stable long term 10.04 release and updates are up to date.). I also believe that I only use official software packages.

 Many thanks for any help, Bagvian

---

### Post by UeB on 2010-10-16
I have the same problem.  Anybody any solution?

---

### Post by UeB on 2010-10-16
faund the corresponding bug report:
[https://bugs.launchpad.net/ubuntu/+source/blcr/+bug/555729](https://bugs.launchpad.net/ubuntu/+source/blcr/+bug/555729)
removing blcr-dkms helps

---

### Post by xdaedalus on 2010-10-31
I was having this same problem. The bug report helped, but I'm not a very experienced user, so I didn't understand most of it. 

What I found was that I had downloaded Euler, a program I was interested in but hadn't used much. Euler required blcr-dkms, which is why my package manager had downloaded it (I wanted to find out what depended on blcr-dkms, rather than just removing it and possibly messing something up later). I uninstalled Euler, and then used computer janitor to remove blcr, which wasn't needed anymore. 

This allowed me to upgrade to 10.10 without problems (well, at least without problems related to this).

Hope that helps somebody else--thanks for pointing us to the bug report page.

---

### Post by treerink on 2010-11-04
I had exactly the same problem. Solved it by:

-> System -> Administration -> Synaptic Package Manager :
-> type in the search: blcr-dkms
-> by right mouse click on the S-column select: Mark for Upgrade
-> close

-> then again: System -> Administration ->  Update Manager :
-> Upgrade

now it works

---

### Post by kakila on 2010-11-16
Hi all
I tried your solution but my blcr-dkms item in the synaptic does not allow me to mark for Upgrade, it is grey in the menu.

I have already tried re-installing

Any ideas?

---

### Post by cigtoxdoc on 2011-01-13
I just solved problem were blcr-dkms was blocking upgrade from 10.04 LTS to 10.10.  I went into Synaptic, searched for blcr-dkms.  Found that it was installed.  Told Synaptic to completely remove it.  Once removed, upgrade went just fine.

John

---

### Post by bala1987 on 2011-10-06
> **cigtoxdoc said:**
> I just solved problem were blcr-dkms was blocking upgrade from 10.04 LTS to 10.10.  I went into Synaptic, searched for blcr-dkms.  Found that it was installed.  Told Synaptic to completely remove it.  Once removed, upgrade went just fine.

John

Worked like a charm... thanks a lot;)

---

