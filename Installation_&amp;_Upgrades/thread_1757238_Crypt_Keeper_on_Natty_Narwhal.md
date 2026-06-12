---
title: "Crypt Keeper on Natty Narwhal"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by seanjuan on 2011-05-13
After upgrading to Natty Narwhal my Crypt Keeper app will not launch. I am now unable to access secure files. Has anyone had this issue after their upgrade to Natty Narwhal? If so, How were able to resolve this issue.

---

### Post by seanjuan on 2011-05-13
I was able to resolve the issue by typing in the the following commands in the terminal.


gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Skype', 'Dropbox', 'Cryptkeeper']" 


setsid unity

---

### Post by metasoarous on 2011-06-05
See my comment here - [https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071)

Basically, this solution can cause some weirdness with your Unity environment, so I don't think it is really a viable solution. 

Chris Small

---

