---
title: "Upgrade Ubuntu 10.04 to 12.04"
date: 2021-03-30
forum: Installation &amp; Upgrades
---

### Post by speedy987 on 2021-03-30
We  have an old zimbra mail server that is running on Ubuntu 10.04, I want  to upgrade it, but when I run command 'sudo do-release-upgrade' I get  the following message:
=== Command terminated with exit status 1 ===
Can you help me please?

---

### Post by ActionParsnip on 2021-03-30
You can get the alternative ISO for 12.04 (if its still around) and upgrade to 12.04 that way. The online packages for Precise haven't been around for absolutely ages now.
You may find it easier to create a new Focal (Ubuntu 20.04) server and then restore your email from backups. You will need to be aware of any gotchas between the versions.

---

### Post by mikewhatever on 2021-03-30
Both are unsupported, not sure why bother. To upgrade, you need to have 12.04's repositories available. I doubt anyone keeps them for too many years, after the support ends.

---

### Post by Impavidus on 2021-03-30
I hope this old 10.04 server isn't actually exchanging mail with the untrusted web, right? Because 10.04 server edition has been unsupported for 6 years. 12.04 for 4 years. So indeed, why bother? Get a fresh install of a supported release.

---

### Post by TheFu on 2021-03-30
I've been running zimbra for clients since 2008.  20.04 isn't supported, so 18.04 is the target. The releases that work on 16.04 and earlier have security problems. DO NOT LET THESE SYSTEMS ON THE INTERNET!

OS uprades usually go with zimbra release upgrades.  Do 1 at a time, as documented in the zimbra docs. 
Zimbra Release upgrade ... OS release upgrade ...
Zimbra Release upgrade ... OS release upgrade ...
Zimbra Release upgrade ... OS release upgrade ...

There is a Zimbra release that works for 12.04 and 14.04 - so you'll move to the Zimbra release that was supported on each, do the OS upgrade, then move to the Zimbra release that works for 14.04.  Then you'll move to the zimbra release that works for 14.04 and 16.04.  Repeat.

Read each of the upgrade process docs.  If you have zimbra extensions, it may be required to remove those before any upgrades, then re-do them after.  I know the POSIX/LDAP schema changes work that way. It isn't fun modifying the javascript changes for each new release.

Be certain you have tested the migration on non-production versions and have perfect, recoverable, backups, before beginning. I've had a few upgrades go sideways over the years.  The less planning and testing I did, the worse the upgrades went, usually failing or having some really odd problems afterwards.

I've been burned by not using the system perl during upgrades.  And don't get me started about the mandatory minimal /etc/hosts file that Zimbra demands - only during the upgrade process.  Post-upgrade, I always put back those few extra /etc/hosts lines to make access to the email gateway(s) we run easier.  We don't allow Zimbra to be directly on the internet.  All inbound and outbound SMTP goes through gateway servers.  Access by end-users to zimbra if they aren't on the company LAN requires using a VPN client.

A few releases ago, I had to perform a fresh install - that meant migrating not just emails, user accounts, aliases, distribution lists, certificates, calendars, address books, and setting the outbound relay again.

If it isn't clear - 10.04 and 12.04 aren't supported and haven't been for 4+ yrs.  Ubuntu support is 5 yrs, not 10 like some other commercial Linux vendors provide, unless we pay.  There are 2 LTS releases during that 5 yr support period, so every 4 yrs, plan on moving to the current LTS release.

When *do-release-upgrade* doesn't work, you'll need to fall back to manually doing the upgrade in the old-school, debian way. This isn't perfect and will have some problems.  Earlier this year, I moved from 16.04 --> 18.04 across a number of my servers in this manner.  About 60% went fine. The other 40% had problems - never the same problem.  Basically, expect some problem that will take a few hours to figure out.  I removed all PPAs and upgraded to the current HWE kernel before starting. The things I thought were going to be a problem went smooth. It was things like changes to the inputs (mouse/keyboard) which caught me off guard.  Not being able to use the physically connected keyboard did freak me out a little going to 18.04.

I'd put off the zimbra migration as long as possible, but no 20.04 support by the Zimbra guys meant I couldn't wait any longer and will probably end up moving to 20.04 (from 18.04) just before 22.04 gets released.

Systems that run 1 OS for too long become untouchable. It is best to move during the first year that a new LTS is available, so common issues are fresh in the minds of the community.  I don't recall all the issues moving from 10.04 --> 12.04 --> 14.04 --> 16.04, so you'll probably have to figure those answers out for yourself, when they happen.

---

### Post by QIII on 2021-03-30
Make backups of your data, install a supported (read: safe and secure) release of Ubuntu.  Install the needed software.  Restore your data from backups.

There is really no other choice that can be recommended as safe and we would rather not have the community spend a lot of time trying to sort out upgrading from one EOL release to another.

---

### Post by grahammechanical on 2021-03-30
You need to do an End of Life Upgrade. This wiki page will explain it.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The repositories of end of life releases are moved to old-releases.ubuntu.com/ubuntu. You have to edit the /etc/apt/sources.list file manually. Follow the pattern in that wiki page and set the internet address to > [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)
 You replace CODENAME with lucid. This will let you update lucid (10.04). Then you repeat the process moving to precise (12.04). You should be able to upgrade to 12.04. But you do not stop there. Then to trusty (14.04). On to xenial (16.04). and then bionic (18.04). You have to upgrade to each LTS release in turn until you get to a supported release.

Regards and good luck

---

### Post by rsteinmetz70112 on 2021-03-31
Before you upgrade from 10.04 make sure you first update your currnet release fully and respolve any issues before upgrading to a later release.

---

