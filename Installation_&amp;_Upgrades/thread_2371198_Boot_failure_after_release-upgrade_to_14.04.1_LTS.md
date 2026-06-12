---
title: "Boot failure after release-upgrade to 14.04.1 LTS"
date: 2017-09-12
forum: Installation &amp; Upgrades
---

### Post by ed7564 on 2017-09-12
Hello

I'm trying to upgrade an old Ubuntu 12.04.5 LTS to 14.04.1, it's a virtual VMware machine. 
The upgrade process goes very well, no errors or such are encountered as far as I've seen. 

Finally I get the prompt to reboot the system in order to finish the release upgrade.
Selecting 'yes' (reboot) subsequent startups fail. In the boot screen I can only see an error message saying "Error: File not found" flash by, printed 2-3 times.

How can this boot failure be solved?

---

### Post by mörgæs on 2017-09-13
Hi, welcome to the fora.
Before you proceed: Is downloading a fresh 16.04.3 and running it as a virtual machine an option?

---

### Post by ed7564 on 2017-10-04
> **mörgæs said:**
> Hi, welcome to the fora.
Before you proceed: Is downloading a fresh 16.04.3 and running it as a virtual machine an option?

Unfortunately the alternative of setting up a completely new installation would be undesirable. This machine is a server where some work/configuration has been performed and I am not completely informed about it.

Simply performing a dist-upgrade would be a better alternative, and it almost work - except for the boot issue.

---

### Post by mörgæs on 2017-10-06
Sorry, can't help you here. I'm not experienced enough in virtual machines.

---

### Post by ed7564 on 2017-10-10
> **mörgæs said:**
> Sorry, can't help you here. I'm not experienced enough in virtual machines.

It should not matter that much that it is a virtual machine. The booting process should not be different in any important aspect.

What can you tell me about the boot system, in general?

---

### Post by mörgæs on 2017-10-10
What I can tell you might not help your situation.

I use first and foremost old hardware from the days before Restricted Boot. Have almost never boot problems. 
I have little patience with old software. A fresh install of the latest stable version keeps the doctor away.
The only tool I have used for solving boot problems is Boot Repair. Recommended.

---

