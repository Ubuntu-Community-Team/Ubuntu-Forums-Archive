---
title: "Need help with apt-get install"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by Talha_Ahmed on 2014-07-22
I am trying to install freeswitch 1.4.5 on Ubuntu 13.10 x64 and it requires libjpeg-dev which is not installing.
I have tried following.
I am trying to apt-get install libjpeg-dev and getting following message.

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libjpeg-dev : Depends: libjpeg8-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

When I apt-get install libjpeg8-dev I get.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libjpeg8-dev : Depends: libjpeg-turbo8-dev (>= 1.1.90+svn722-1ubuntu6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

When I apt-get install libjpeg-turbo8-dev, I get
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libjpeg-turbo8-dev : Depends: libjpeg-turbo8 (= 1.3.0-0ubuntu1) but 1.3.0-0ubuntu1.1 is to be installed
E: Unable to correct problems, you have held broken packages.

When I apt-get install libjpeg-turbo8, I get.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libjpeg-turbo8 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by grahammechanical on 2014-07-22
Ubuntu 13.10 reached end of life on 17th July. That could be the reason for this happening. Perhaps you are indeed requesting an impossible situation. What happens if you use the software centre to install some small application? Does that work? May be the 13.10 repositories are closed.

Regards.

---

