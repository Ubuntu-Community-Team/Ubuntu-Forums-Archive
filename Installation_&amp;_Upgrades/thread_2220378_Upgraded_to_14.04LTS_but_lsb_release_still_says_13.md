---
title: "Upgraded to 14.04LTS but lsb_release still says 13.10"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by pjeung on 2014-04-27
I upgraded to 14.04.  System Settings -> Details says "ubuntu 10.04 LTS". 
Everything looks fine but  lsb_release -a returns

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

I have had some trouble running Software Updater.  Currently when I run it, it says "The sofware on  this computer is up to date.  However, Ubuntu 14.04 is now available  (you have 13.10)."  This is erroneous because I'm using Locally  Integrated Menus which is a 14.04 feature that is not in 13.10.  When I  click the Upgrade button, I have to authenticate, then I get the Release  Notes window.  Clicking on its Upgrade button, I get to the  Distribution Upgrade window, which fails with  "The software on this  computer is up to date.There are no upgrades available for your system.  The upgrade will now be canceled."

Also,
sudo /usr/lib/update-notifier/update-motd-updates-available 

returns a blank line.

So it seens I have a partial upgrade.  How do I complete it? Has anybody else seen this?

---

