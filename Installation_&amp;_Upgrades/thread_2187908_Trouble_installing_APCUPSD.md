---
title: "Trouble installing APCUPSD"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by brian.conti on 2013-11-14
I installed APCUPSD previously, then made some changes to the config file and didn't make a backup, so I wanted to start over. 

Did apt-get remove apcupsd
Then apt-get install apcupsd

For some reason, now I do not see /etc/apcupsd/apcupsd.conf (/etc/apcupsd is there, but does not have the conf file inside) or /etc/default/apcupsd.  Any ideas?

---

### Post by tgalati4 on 2013-11-14
```
sudo apt-get purge apcupsd
sudo apt-get clean
audo apt-get check
sudo apt-get install apcupsd
```

Don't forget to install the cgi interface if you want a web interface and the documentation files:

tgalati4@Mint14-Extensa ~ $ apt-cache search apcupsd
apcupsd - APC UPS Power Management (daemon)
apcupsd-cgi - APC UPS Power Management (web interface)
apcupsd-doc - APC UPS Power Management (documentation/examples)

---

### Post by brian.conti on 2013-11-15
Perfect.  Thank you very much for the help!

---

