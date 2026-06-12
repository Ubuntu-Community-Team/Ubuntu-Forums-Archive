---
title: "Scribus - Not able to Install on Ubuntu 14.10"
date: 2015-01-31
forum: Installation &amp; Upgrades
---

### Post by commoner2 on 2015-01-31
Dear All,

I am not able to install scribus on Ubuntu 14.10. It does not reflect in the Ubuntu Software Center for installation. I have tried PPA from ubuntuhandbook but it did not work either. Kindly provide instructions on how to go about installing it.

I am a basic-level user of Ubuntu and wish it was more installation-friendly. However, I have switched completely from Windows and am striving to get used to Ubuntu.


Thanks in advance.

---

### Post by ajgreeny on 2015-01-31
Show us the output in terminal of ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install scribus
```
Scribus **is** in the repos of 14.10 and installs OK; I have just done it just to make sure on a live 14.10 system.

I wonder if you have enabled the **universe** and **multiverse** repos in software-sources as scribus is in universe.

---

### Post by commoner2 on 2015-01-31
> **ajgreeny said:**
> 

I wonder if you have enabled the **universe** and **multiverse** repos in software-sources as scribus is in universe.

Yes, u r right. Thanks a lot for the resolution.

---

### Post by ajgreeny on 2015-01-31
Great!

Please go to **Thread Tools** menu at the top and mark this as SOLVED.

---

