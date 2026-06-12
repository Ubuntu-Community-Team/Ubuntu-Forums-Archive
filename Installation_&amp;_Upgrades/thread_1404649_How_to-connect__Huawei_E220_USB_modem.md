---
title: "How to-connect  Huawei E220 USB modem"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by esmailgad on 2010-02-11
This is my first how to and I hope it will be useful.
I had a problem to connect Huawei E220 USB mobile modem. I used the thread "http://ubuntuforums.org/showthread.php?t=843973" . 
Then when I used the terminal with 
$ wvdial Defaults

I obtained the following message

Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
and the PPPD aborted.

I came over this with the command
$ sudo chmod a+rw /etc/ppp/pap-secrets

Then I repeated the "$ wvdial Defaults", successfully,

I restored the original permissions with:
# chmod a-rw /etc/ppp/pap-secrets
# chmod u+rw /etc/ppp/pap-secrets

I hope you have found this helpful.

---

