---
title: "Update Manager Errors"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by clbaines on 2010-07-28
As you all know no good deed goes unpunished. I decided to upgrade from Hardy to 10.04. I did the upgrade on line from the Upgrade Manager. I feel 
this was and is why I am having problems with the Upgrade Manager and Package Manager.  I started out today trying to install a copy of Google Chrome from a downloaded .deb file and got this error:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I took their advice and ran those commands. That error:

Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing ircd-hybrid (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/mirrors.rit.edu_ubuntu_dists_hardy-security_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

Seems to be something funny happened during the upgrade.


Now when I run the package manager I get this error  (All of this has 
a common cause I think):

     An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf), E:Error occurred while processing limewire-basic (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'


sudo apt-get update -o APT::Cache-Limit=25165824

Any help would be appreciated.

---

### Post by tekkidd on 2010-07-28
it looks like their are errors in the sources.list from the upgrade. You can try popping in a 10.04 cd and taking the sources.list from the cd and copying it over to the install. then doing a sudo apt-get update

---

### Post by clbaines on 2010-07-28
Thanks I will give it a try. I have 10.04 installed on a mini 10 and have no problems with either manager.

---

