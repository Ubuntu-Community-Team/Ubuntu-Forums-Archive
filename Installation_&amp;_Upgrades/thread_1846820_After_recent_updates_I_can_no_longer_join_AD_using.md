---
title: "After recent updates I can no longer join AD using Likewise"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by brandon.johnson on 2011-09-19
I noticed yesterday that I could not login to webmin with my AD account. I logged in using a local admin account. I left the domain using "sudo domainjoin-cli leave"and received a successful reply that it left. I uninstalled and reinstalled likewise-open and receive the following when I try to join the domain using "sudo domainjoin-cli join (FQDN) (DOMAIN ADMIN)" 


Error: No child processes [code 0x0001000a]                                                                                                                       An unexpected system error has occurred.  Please contact Likewise technical      support for assistance.

[FONT=Verdana]Any help would be much appreciated.

Thank you.[/FONT]

---

### Post by pytheas22 on 2011-09-19
I'm afraid I can't help troubleshoot that error, but you might try using Centrify instead of Likewise.  Likewise is [no longer in the AD business]("http://www.thevarguy.com/2011/08/11/the-new-likewise-shifts-its-focus-to-storage-services/").  Centrify provides free (though not open-source, unfortunately) tools that do the same thing as Likewise Open.

---

