---
title: "Upgrade 7.10 - 8.04 LTS - Error authenticating"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by bodley on 2008-04-29
Error authenticating

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

screenlets
gtk2-engines-murrine
________________________________________________

Steps to error using the the Update Manager:

1. Click on CHECK

2. Click on UPGRADE

3. Upgrade tool stops with following message:

No valid mirror found

While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'gutsy' to 'hardy' entries.
If you select 'no' the update will cancel.


4. Click YES

5. Upgrade stops and rolls back after displaying the Error authenticating..... message as above.

__________________________

I uninstalled the Screenlets package which successfully removed it from the the error message.

I installed the gtk2-engines-murrine package successfully (it had never been installed on my system) which made no difference.

I uninstalled the gtk2-engines-murrine package successfully. Again, no difference.

I am still left with gtk2-engines-murrine package not able to be authenticated and can't proceed with the upgrade.

---

