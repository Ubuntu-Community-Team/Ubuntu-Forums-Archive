---
title: "Package Operation Failed"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by james41382 on 2013-06-25
I am sort of new to linux. I used it for a couple years back in the day, but I am back in school and studying some CS stuff so I thought I'd get back into it. I wanted to install Skype, but it is not listed in the Ubuntu Software Center so I looked on the Skype website and sure enough there was Skype for Linux. I selected the Ubuntu 12.04 distro and chose to open with Archive Manager, which then somehow took me to the Ubuntu Software Center and I then chose to install. But the installation failed toward the end of the operation. I saved the failure details just in case I need it later, but my question is:

So all these packages that are being unpacked during the install process... where do they go when the process fails? _Do I need to go through the failed operation details and manually delete these files/directories?_ I checked to see if Skype is installed by apt-cache policy command, which it appears it is not. I read something that seemed to indicate that the Skype website points to the wrong installation package. [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by DeathByDenim on 2013-06-25
If a package failed to install, there is usually no need to worry. If anything got broken, you can fix it by opening a terminal and running this command:
```
sudo apt-get -f install
```
If there is stuff broken, then it will tell you and try to fix it for you.

Also, Skype should be available in the repositories. I think you need to enable the "Partner" or "Multiverse" repositories though. You can try
```
sudo apt-get install skype
```
The version of Skype that come from there has a fix in it too. At least in my case, I had to mess around with the Skype from Skype website to get it working, but the one from the Ubuntu repository works instantly.

---

