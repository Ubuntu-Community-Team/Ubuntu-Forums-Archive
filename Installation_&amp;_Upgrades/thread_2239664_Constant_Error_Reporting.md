---
title: "Constant Error Reporting"
date: 2014-08-15
forum: Installation &amp; Upgrades
---

### Post by Jeff_McLellan on 2014-08-15
I have upgraded my Toshiba laptop from 12.04 to 14.04. (I'm new to Unix platforms)

I then had to follow the instructions in this web help when it failed to boot.

[http://askubuntu.com/questions/452631/ubuntu-14-04-doesn-t-boot-after-upgrade-from-12-04-installed-inside-windows-8-1/454373#454373](http://askubuntu.com/questions/452631/ubuntu-14-04-doesn-t-boot-after-upgrade-from-12-04-installed-inside-windows-8-1/454373#454373)

Ubuntu then booted correctly but now it constantly finds errors to report.

How do I find out how to fix this please??

---

### Post by ian-weisser on 2014-08-15
Please paste the output of the following command here.
```
ls -lt /var/crash
```
This will show us the contents of your /var/crash directory, sorted by time.
So we can see what is crashing, and when.

---

