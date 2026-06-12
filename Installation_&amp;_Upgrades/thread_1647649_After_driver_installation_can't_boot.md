---
title: "After driver installation can't boot"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by Ramy89 on 2010-12-17
Hi,I have a notebook with dual-boot, windows 7 and ubuntu 10.10.
I have ubuntu in a different partition than windows,It was working fine since I activated the broadcom STA wireless driver,it was present but not active (I also activated nvidia driver).
The I selected restart to complete updates,and when I restart I find out that after loading ubuntu's writing,instead of starting the GNOME session I am in a sort of recovery mode.
It asks me the password,I log and it says:"Your cpu appears to be lacking expected security protections.Please check your bios settings,or for more information,run: /usr/bin/check-bios-nx --verbose".
Doing as it says I get:
"This cpu is family 6,model 37,and has capabilities but is unable to use these protective features because the bios is configured to disable the capability.Please enable this in your bios."
It also gives a link:  
[http://wiki.ubuntu.com/Security/CPUFeatures](http://wiki.ubuntu.com/Security/CPUFeatures)
But I don't have any idea of how changing that flag,I also tried ctrl+alt+7 but it sticks at something like "enabling sensors" or something like this,It blocks and GNOME doesn't want to start.
A solution would be to reisntall ubuntu,but if I reinstall will I get that problem if I activate the driver again,or anyone know a solution to change that flag to permit the execution of non-executable memory?
And since I work with C programming,will this get any problem with an eventual stack overflow caused by the programs I compile and run?

Thanks previously for the answers (I hope).

---

