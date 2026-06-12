---
title: "No internet connection after upgrade to 14 (Trusty Tahr)"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by athro on 2014-09-26
Hello,
I have upgraded this evening from 12.04 to 14 and now cannot get an internet connection either by wireless or connecting to the router with ethernet. The bar at the top of the screen indicates that I am connected but I cannot reach websites; and Thunderbird fails to connect for email. I have searched for previous answers to this and found a number of obscure suggestions in April or so of this year, but wonder if there is any more consensus now on what to do? The laptop is a Lenovo G550 and the router is a Netgear N600 ADSL2+.
thanks for any help!

---

### Post by qianian2 on 2014-09-26
Connect the cable. When you click on the top panel icon, is Ethernet an option or grayed out? If it's an option, turn off wireless from the same drop-down menu. Try different options under Ethernet. The best way to tell if you're connected (as opposed to a browser problem) is to open terminal and $ ping google.com

---

### Post by athro on 2014-09-27
Thanks. I had done that. Eventually found something that worked from the suggestions earlier this year: setting BSSID in the edit connections menu and going
```
[COLOR=#000000][FONT=Ubuntu]sudo apt-get remove --purge resolvconf[/FONT][/COLOR]
```. No idea why that should be necessary.

---

