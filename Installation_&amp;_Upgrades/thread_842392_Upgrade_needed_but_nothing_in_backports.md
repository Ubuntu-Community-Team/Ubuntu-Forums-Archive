---
title: "Upgrade needed but nothing in backports"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by boupartac on 2008-06-27
Hi all,

Our web servers have been checked recently by an external security firm. We have been told that our webservers need to be upgraded to the latest version in order to fix some security issues.

Security updates are applied every week on our servers. If I want to upgrade Apache to version 2.2.9 and PHP to 5.2.6, how do I proceed if my servers are already up to date and if there is nothing to upgrade, even when I use the backports repository?

I know that I can download and compile these programs myself, but for future updates, it becomes complicated since we have lots of servers...

Currently, for Gutsy, the version of Apache is 2.2.4-3ubuntu0.1 and PHP is PHP5.2.3-1ubuntu6.3.

Any ideas on how to softly upgrade those two programs?

Thanks,

Boupartac

---

### Post by BillyBerry on 2008-08-16
I also need to upgrade urgently to PHP 5.2.5 for the same reasons and want to avoid compiling from source. A response to this will be greatly appreciated.

---

### Post by RiPPeR on 2008-09-18
I'm in exactly the same boat, Were running Ubuntu Gutsy (Apache 2.2.4) and need to upgrade to 2.2.9 to meet security requirements - but I'm not really sure on what the best way to do this is?

Can anyone help?

---

### Post by matthewboh on 2008-09-29
I also need 5.2.5 but am on Hardy Heron - 8.0.4

I just put in a bug report - found out that the next version of Ubuntu will ship with 5.2.6, but asked for at least 5.2.5 in a backport.

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/275844](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/275844)

UPDATE

They closed this out - I just need php 5.2.5 for another reason, but I learned an awful lot today - thought I would share.

Ubuntu uses this - [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn) - web site to let everyone know about security updates and enhancements.  I "think" USN stands for Ubuntu Security News - but that leaves another number - the CVE number.

The CVE number or ID stands for  Common Vulnerabilities and Enhancements and is kept by the National Institute for Standards and Technology - the same people that bring you CERT.

Anyway, find the CVE number, then look at the Ubuntu News - just a quick look - they get the High security risk items out of the way as quickly as possible.

So take a look at the Apache2 release notes for the CVE-ID then take a look at the Ubuntu Security News pages - it may already be included in a release

---

