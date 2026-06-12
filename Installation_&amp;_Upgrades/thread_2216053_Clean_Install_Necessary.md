---
title: "Clean Install Necessary?"
date: 2014-04-09
forum: Installation &amp; Upgrades
---

### Post by Kurt_Alan on 2014-04-09
****

When TT launches, I'm upgrading from PP.  Internal update or clean install?
.
Given the inefficiency of Window's registry, I would always do a clean Windows install for a major upgrade.

But as I have done internal upgrades with Ubuntu, lately from LL to PP, and watched the terminal, it seems that Linux is very precise in how it handles its programs: update, change, or delete.

So now I have PP on top of LL.  Should I feel comfortable putting TT on top PP on top of LL or go for a reformat and clean install?

---

### Post by grahammechanical on 2014-04-09
Precise Pangolin (12.04) is sitting on itself. What was 10.04 has been removed by the upgrade process. Likewise if you upgrade to 14.04 that process will remove all unnecessary packages that came with 12.04.

some of us recommend a fresh install as some people do hit problems. I tested the upgrade process from 10.04 to 12.04 when 12.04 was a couple of weeks away from release and everything went fine but I was upgrading a default (fresh install) of 10.04 put in just for testing purposes. I might test the upgrade process of 12.04 to 14.04 but again I shall be putting in a fresh install of 12.04 simply to test the upgrade process.

I suggest that if you choose to upgrade then deactivate any proprietary video driver and make sure the user interface is as default as possible. Disable any PPAs that you have. Remember the upgrade process might not do a good job with any third party software that you may have installed if those developers have not upgraded their software to the 14.04 repositories. 

Regards.

---

### Post by Kurt_Alan on 2014-05-12
**[SIZE=5][/SIZE]**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]

My conclusion:

Optimal: Clean install from 14.04.1 LTS

Actual: Clean install 10.04 LTS < upgrade to 12.04 LTS < upgrade to 14.04 LTS:
no fundamental problems.

Marked: SOLVED

---

### Post by LastDino on 2014-05-12
Clean install is always recommended as it both saves time and unnecessary backtracking if there happens to be any odd problem. Especially if we are talking about LTS version which we want to keep around for while, make it as stable and as clean as possible by installing fresh.

---

