---
title: "Problem Installing PHP IMAP  module"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by vazoom on 2012-11-25
Hello and thanks in advance for some help
I recently had to do a downgrade of PHP 5.4 to 5.3 by following the thread located at [http://ubuntuforums.org/showthread.php?t=2074178&highlight=downgrade+php+5.4+to+php+5.3](http://ubuntuforums.org/showthread.php?t=2074178&highlight=downgrade+php+5.4+to+php+5.3)
 
PHP now shows as PHP Version 5.3.10-1ubuntu3 so that's ok. For a program I must run on the system I need to enable the IMAP module. I assume this is done using sudo apt-get php5-imap however I am running into the following error. Can somebody please help me understand what the issue is a hopefully pretty easy fix to get the module to install
 
user@MX1:~$ sudo apt-get install php5-imap
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
php5-imap : Depends: phpapi-20100525+lfs
E: Unable to correct problems, you have held broken packages.
user@MX1:~$

---

