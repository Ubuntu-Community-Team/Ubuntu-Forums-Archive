---
title: "Upgrade to 13.10 breaks drush"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by bkline on 2013-10-25
I just upgraded from 13.04 to 13.10 and now drush is broken.  The error message I get is

> The following restricted PHP modes have non-empty values:
disable_functions. This configuration is incompatible with drush. 
Please check your configuration settings in /etc/php5/cli/php.ini or
in your drush.ini file; see examples/example.drush.ini for details.

So it looks like PHP has become more restrictive with this release of Ubuntu.  However, attempts to follow the instructions to override the setting of the disable_function variable don't work.  According to the documentation, putting the line
```
disable_functions =
```
in ~/.drush/php.ini or ~/.drush/drush.ini should solve the problem, but although I can tell from `drush status` that php is finding and reading my drush.ini (or php.ini - I've tried both), the original assignment of the long list of functions to be disabled is still in effect.  If I put that line (assigning the variable to nothing) directly under the assignment in the system file, the error message goes away.  That's not an attractive solution, however, because it involves hacking a file managed by the Ubuntu package management system, something I go to great lengths to avoid.  Clearly something more subtle than I've been able to figure out has been broken here.  Anyone else experience this?  Did you come up with a better solution?

---

### Post by tkoopa on 2014-01-03
on a fresh 13.10 install drush status reports that it's using /etc/php5/cli/php.ini. Commenting the line starting with disable_functions= works in solving the problem

---

### Post by rpms on 2014-01-09
Are you still needing help? I just worked through the same problem. Here is what worked (both for me as user and as root):
Copy file:///etc/php5/cli/php.ini to ~me/.drush and to /root/.drush
Comment out the line starting with disable_functions .. 
; disable_functions

---

### Post by snowguy on 2014-01-30
rpms's solution of adding the php.ini file to the .drush directory didn't work for me unfortunately.

I had to go with the tkoopa's solution of editing the php.ini file @ /etc/php5/cli/

---

