---
title: "Getting started - installing packages"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by efAston on 2010-02-09
Hi,

I'm getting started with kubuntu 9.10 and I'm stumbling a bit with installing packages. I want to, for example, install kino, but I saw on a forum someone saying to use "apt-get install kino dvdrip", and when I do that it says 

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I tried typing "su", and it asked for a password. The only password I entered when installing kubuntu 9.10 (and I re-installed this morning) was the password for my "aston" login, so I entered that, and it said "su: Authentication failure".

I seem to go in circles every time I try to install something that's not in KPackageKit, any help is really appreciated.

Regards,
Aston

---

### Post by amityak on 2010-02-09
it seems like you have to figure out the password you gave to your username during installation. try 'root' .... are you on a live cd ?

---

### Post by abhishek.malhotra35 on 2010-02-09
sometimes, it happens that a lock file gets created but not deleted. I faced similar issue while working on aix. I simply deleted the lock file and it started working. This might solve your issue.

---

### Post by Bucky Ball on 2010-02-09
Why not just go System->Administration->Synaptic Package Manager and do a search for then install Kino?

---

### Post by efAston on 2010-02-09
False alarm, the installation was unsuccessful and I was actually running off a live CD without realising it. Thanks anyway!

---

### Post by abhishek.malhotra35 on 2010-02-09
> **Bucky Ball said:**
> Why not just go System->Administration->Synaptic Package Manager and do a search for then install Kino?

I think the problem is the lock that system uses so another process cannot use it. 
> : Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
Normally lock is created when you try to install something and when it installed, lock file is deleted. Somehow this lock file has not been deleted. It can be deleted manually.

---

