---
title: "Likewise issues with 11.04 64-bit"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by greggc@bsmg.net on 2011-05-03
I am testing Ubuntu 11.04 64-bit with a Microsoft AD environment using Likewise-Open. I setup a clean install of the OS and installed Likewise open from the Ubuntu repository. I was able to add the workstation to the AD domain and log in, but, when I ran the command "lw-enum-users", I would get the following error;

Failed to enumerate users. Error code 40121 (LW_ERROR_DOMAIN_IS_OFFLINE)
The domain is offline

lw-get-status would show that the domain is online and operating fine. I ran through all the testing options on the Likewise website documentation and everything passed, except querying AD for groups or users. I removed the workstation from the domain and re-added it. Now I can't log into the domain, but everything else looks the same. Status and all tests are fine, but I am unable to query AD. Unable to get any resolution on this. Networking configuration and settings all have been confirmed to be configured correctly. Anyone have any ideas?

---

### Post by greggc@bsmg.net on 2011-05-03
I was able to get a little further with this. If I killed the lsassd daemon and restarted it. I was able to query AD for objects and log in as a domain account. However, after a reboot I would no longer be able to log in with a domain account nor query AD. It would seem the lsassd daemon may be starting before something else it may need running first?

---

### Post by archer007 on 2011-05-03
You have no idea how many hours you just saved me! Thank you. I was stuck in this weird state where lw-enum-users gave me errors but lw-get-status said it could see the domain. Going to restart and see if this sticks, will post more if I can.

---

