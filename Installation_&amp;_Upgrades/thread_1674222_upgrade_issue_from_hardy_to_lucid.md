---
title: "upgrade issue from hardy to lucid"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by fmlmpg on 2011-01-23
Hi, 

Recently I upgraded my operating system from hardy to lucid, While using python 2.6 in the latest release I am getting a UserWarning message in my console. I followed the below URL [https://bugs.launchpad.net/ubuntu/+source/distribute/+bug/576434](https://bugs.launchpad.net/ubuntu/+source/distribute/+bug/576434) and made a work around according to #9 suggested by TJ user. Still I am getting the same warning message. Does anyone have an idea to get rid of the same. 

In Python 2.5 it is working perfectly fine as follows: 

Python 2.5.2 (r252:60911, Jul 22 2009, 15:33:10)
[GCC 4.2.4 (Ubuntu 4.2.4-1ubuntu3)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pkg_resources
>>> env = pkg_resources.Environment( platform=pkg_resources.get_platform() )
>>>

but in Python 2.6 

Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pkg_resources
>>> env = pkg_resources.Environment( platform=pkg_resources.get_platform() )
__main__:1: UserWarning: Unbuilt egg for pytz [unknown version] (/usr/lib/python2.6/dist-packages)
>>>

few more information:
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

linux-x86_64-ucs4


Thanks in advance, Vipin

---

