---
title: "Upgrade from 8.04 to 9.10"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by Privsman on 2010-06-28
Regarding this error message:
**“Unable to get exclusive lock – This means that another package handler (like apt-get or aptitude) is already running. Please close that application first”**

Upgrading from 8.04 to 9.10 with adept-manager.  There is an error after the step where the person hits "finish" and the Distribution Upgrade dialogue comes up.  It then errors out and says it can't establish channel because there is another update process going on in the background like apt-get or something else.  

I have found out that what really is happening is that adept-manager is supposed to shut down (but doesn't), and then distribution manager is supposed to start.  To overcome the problem, you have to hit "finish" and then quickly kill the adept-manager window(you have about two seconds to do this) by hitting the x box, but do it before the distribution manager starts.  The process it says is locking it out is actually adept-manager, and not some other background process.  This worked for me, and it makes sense.  The problem is not ubuntu.

Going into sudo and doing a clean of apt-get or other things didn't work for me.  This did.

Privsman    See below.


Kubuntu 8.04 to 9.10 Upgrade
Kubuntu 9.10 is a major upgrade using the KDE 4 desktop. NOTE: You will not be able to reliably downgrade to KDE 3 again since it will upgrade your application settings.

Upgrade to 9.10 over the Internet
Step 1. Update then launch the upgrade
Ensure you are up to date in the normal way, you must have adept-manager 2.1.3ubuntu25.2 installed


Open Adept Manager from the K-menu and click Fetch Updates


The Version Upgrade button will appear, click it


Follow the upgrade wizard

---

