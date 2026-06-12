---
title: "Upgrading from 14.04 to 16.04, &quot;fetching is complete&quot; and nothing else happens"
date: 2019-05-17
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2019-05-17
Hi:

I'm doing the same as in another desktop PC, similar to the other one where I have the problem.

The "getting new packages" stage is not checked and below it says fetching is completed and it has been there for more than 20 minutes.

I can't do anything else, the icons in the menu don't respond when clicked. I notices that the Terminal option is disabled in the upgrade window (in another upgrade I could monitor what was going on).

Now I remember something about a message related to me not being the root user that appeared at the beginning of the process.

The only option is cancel, what should I do?

---

### Post by rva1945 on 2019-05-17
I went to terminal and tried do-release-upgrade, it says No new release found.
sudo apt-get-update does nothing, not even asks for the password.

---

### Post by rsteinmetz70112 on 2019-05-17
Were you able to fully update 14.04 before starting? It looks like you weren't. Those archives are due to be removed at any time but it looks like they're still there. 

Is it set to look for LTS releases? If it's set to look for the next release that would be 14.10 which should have been removed long ago.

---

### Post by rva1945 on 2019-05-17
Well I finally clicked on Cancel but to no avail, the system was frozen. Reset. Thankfully everything was working ok. So Terminal, sudo apt-get update, do-release-upgrade and after long time and a few questions, 16.04 was successfully installed.

---

