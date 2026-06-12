---
title: "Apt-Get fails - superserver script"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by stoaty on 2008-09-12
Hi All :-)
I am trying to clean up a 8.04 LTS installation.
After upgrading from 6.04 at Fasthosts (via ssh - wow that was impressive!), their Matrix control panel failed... 

I then tried to install Plesk, which failed. I have successfully installed Webmin, but now apt-get install phhp5-curl returns the following message.


Removing qmail users (if they exist):

ERROR while trying to Unable to find script for superserver
Check the error reason(see log file: /tmp/qmail_8.6.0_ubuntu8.04.build86080822.19_installing.080912.13.42.log), fix and try again

Aborting...

dpkg: error processing psa-qmail (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 psa-qmail
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried forcing the issue, but the "superserver script" has me beat!

Any clues anyone? Hope so

---

