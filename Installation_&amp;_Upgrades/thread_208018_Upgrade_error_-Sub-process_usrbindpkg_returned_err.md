---
title: "Upgrade error -Sub-process /usr/bin/dpkg returned error"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by inspired on 2006-07-02
Hello,

I encountered an error whilst upgrading from breezy to dapper.
I have the Ubuntu 6.06 dapper cd (alternative install... from downloaded ISO)

I followed the instructions given at [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

under UPGRADING FROM A 6.06 CD

During the "sudo apt-get update && sudo apt-get dist-upgrade " part of the process all seemed to go well, until I got the following output:

> 
....
Preparing to replace libsdl1.2debian 1.2.7+1.2.8cvs20041007-5.3ubuntu2 (using .../libsdl1.2debian_1.2.9-0.0ubuntu2_i386.deb) ...
Unpacking replacement libsdl1.2debian ...
Preparing to replace libsdl1.2debian-oss 1.2.7+1.2.8cvs20041007-5.3ubuntu2 (using .../libsdl1.2debian-oss_1.2.9-0.0ubuntu2_i386.deb) ...
Unpacking replacement libsdl1.2debian-oss ...
Preparing to replace libopenal0 0.2004090900-1.1build1 (using .../libopenal0_0.2005080600-2.1build2_i386.deb) ...
Unpacking replacement libopenal0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/enlightenment-data_1%3a0.16.7.2-3ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonathan@ubuntu:~$


This happened after many (perhaps hundreds) of lines of successful unpacking and installing etc.

Now I have no idea what to do. I've looked for answers but didn't come across any... although I am sure I am not the only one to have this issue. Please advise, or direct me to a post that already covers this issue.

ANOTHER QUESTION
I notice that during all this unpacking and installing the took place during the upgrade, nothing seemed to be getting read from my CD. As far as I could tell from the lights on my hub nothing was downloading from the net either. Therefore I was wondering where these packages were coming from? I want to ensure the upgrade is taking place from the data on the CD as this will be much faster than relying on my internet connection.

I am not sure what will happen if I reboot my computer, now that a heap of stuff has been partly upgraded... so I shall wait and see what replies come to this message first.

With thanks,

Jonathan
:confused:

---

### Post by inspired on 2006-07-02
I see on other posts that it would be helpful to provide a copy of files:
> 
In your own new thread : be elaborate about your problems. Post the errors you get. If the package management problem is solved but you are still having problems then post your /var/log/Xorg.0.log and ~/xsession-errors log files and post the result of $lspci

I don't know how to find the ~/xsession-errors log. Please advise.
I also have no idea what $lspci is. Please advise.
The content of /var/log/Xorg.0.log is:

***[ Tried to paste it here... but made message too long. So I have attached it instead  - as three files to make them small enough]***

Let me know if any other info would be helpful.

BTW... is there any way to use the automated Upgrade tool AND having it get the packages from the CD rather than downloading them from the net ?

Thanks a lot,

Jonathan

---

### Post by inspired on 2006-07-03
Well, I simply repeated running the update routine, including the GUI one, and all the packages etc went on. As far as I know I am now upgraded to 6.06.


How do I confirm what version of Ubuntu I am running?

Thanks,

Jonathan

---

