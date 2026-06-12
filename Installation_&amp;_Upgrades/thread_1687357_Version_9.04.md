---
title: "Version 9.04"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by maustin2 on 2011-02-13
I have been down for a while, nearly three years. There are over three hundred updates waiting to be install and an upgrade to 9.04. A lot happens in three years.
 When I attempt to install the packages there is a message that some are not authenticated. Looking at the list of these show nearly all of the packages in the to be install list. In the past there has been some problems with installing packages, but I have always been able to find solutions.
 Are there any problems with version 9.04? Should I ignore the not authenticated message and install the packages? Should I attempt to install the version upgrade first? There was always problems with at procedure. I have the following setup:
 
  DELL PowerEdge SC 430 server
  3Gb of RAM
  Ubuntu 8.10
  Linux kernel 2.6.27-9-server
  GNOME 2.24.1
 I currently have approximately thirty point four gigabytes of files. 

 Any assist with this situation would be greatly appreciated and my thanks in advance for the assist.

---

### Post by P4man on 2011-02-14
Im surprised you are getting any updates at all, as Ubuntu 8.10 and 9.04 are end of line, no longer supported, so the repositories are down AFAIK. That makes upgrading pretty damn hard. If you dont intend to upgrade every year or so (as is likely with a server), you should stick to LTS versions which have 3 year or 5 year (for server) support cycles:
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)


That wont help you now, but I have no idea what will.

---

### Post by coffeecat on 2011-02-14
Have a look at this link for using the old-releases server:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you are running 8.10, then you will have to go 8.10 > 9.04 > 9.10 to get to a supported release. But 9.10 will only be supported for another few weeks, so you really need to update  to 10.04. That's four release upgrades, a lot to download and install and a lot to go wrong, particularly if you have any non-repo stuff installed.

You'd be better off backing up your 30.4GB of data and making a fresh install of 10.04, imho.

**EDIT**: by the way, your profile in your post says you are running 6.06/Dapper. Once  you've installed 10.04/Lucid, you might want to amend your personal details. :wink:

---

