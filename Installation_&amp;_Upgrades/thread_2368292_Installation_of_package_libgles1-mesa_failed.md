---
title: "Installation of package libgles1-mesa failed"
date: 2017-08-09
forum: Installation &amp; Upgrades
---

### Post by oleander2 on 2017-08-09
I've recently installed Ubuntu 16.04 LTS on my HP Elitebook 8440p Laptop. In order to update the graphics driver I downloaded the Intel Update-package from 01.org (V2.0.2). This update failed because of a "package problem". After a few hours of trying to find the reason for my problem, now I'm convinced that there is a bug related to the official packages:

On Ubuntu packages, I found the current packages related to "xenial updates":
**libglapi-mesa as **[COLOR=#333333][FONT=Ubuntu]**17.0.7-0ubuntu0.16.04.1**
[/FONT][/COLOR]and
**libgles1-mesa as **[COLOR=#333333][FONT=Ubuntu]**12.0.6-0ubuntu0.16.04.1**

[/FONT][/COLOR]The package libglapi-mesa is already installed on my system.
Trying to 'sudo apt-get install libgles1-mesa', it says that it wants to have another version of libglapi-mesa: a version called 12.0.6-0buntu0.16.04.1, instead of the installed one (17.0.7-0ubuntu0.16.04.1)

But a package like **libglapi-mesa 12.0.6-0buntu0.16.04.1** seems not to exist!
From my point of view, the package libgles1-mesa points to a wrong version number and aborts the installation.

Could this be possible? Is there a way to make the libgles1-mesa believe that the appropriate libglapi-mesa package is already installed by editing the version number?

Any help would be highly appreciated! Many thanks in advance!

---

### Post by oleander2 on 2017-08-12
In the meanwhile, the bug has been solved by a package update.

---

