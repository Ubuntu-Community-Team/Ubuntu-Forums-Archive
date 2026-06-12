---
title: "problem with flash player plugin in ubuntu 9.10"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by skkmaths on 2010-01-22
i installed ubuntu 9.10 . while installing flash plugin from synaptic package after some time it stops where  connecting to archive .canonical.com . please help me to resolve this problem ,,,please mail me to <snip>__[EMAIL="skkmaths@gmail.com"][/EMAIL]

---

### Post by Sef on 2010-01-22
Applications > Accessories > Terminal

then copy and paste these commands:

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

Then copy and paste any error messages that you get.

---

### Post by skkmaths on 2010-01-22
i got the following thing ,,,,,,please help me to resolve this thanks


[sudo apt-get update && sudo apt-get install flashplugin-nonfree
Err [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                                                                      
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://download.skype.com](http://download.skype.com) stable Release.gpg                                                                         
  Could not connect to download.skype.com:80 (78.141.179.2), connection timed out [IP: 78.141.179.2 80]
Err [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_IN                                       
  Unable to connect to download.skype.com http: [IP: 78.141.179.2 80]
0% [Connecting to archive.ubuntu.com (91.189.88.31)]

---

