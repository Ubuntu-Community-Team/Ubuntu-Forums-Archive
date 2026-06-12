---
title: "Effects of upgrading from 15.04 to 16.04"
date: 2016-11-18
forum: Installation &amp; Upgrades
---

### Post by tonma on 2016-11-18
I need to upgrade from my 15.04 to 16.04, and I wanted to ask what happens to some important files such as SSH and bashrc configuration, and even the rest of the files on the system (Obviously I will backup, but I still need to know if anything is going to be changed / deleted)

Thanks!

---

### Post by ian-weisser on 2016-11-18
It's hard to say. We don't know anything about your SSH or bashrc configuration.
The question implies that you made changes that you wish to keep.

The question also implies that you have never release-upgraded Ubuntu before.
There is no supported upgrade path from 15.04 to 16.04 anymore. You missed that train (15.10), which left the station several months ago.
You can try an (unsupported) upgrade if you wish, or you can clean-install 16.04 and restore customizations from your backups.

Er, you do realize that your 15.04 system has not received security updates in almost a year, and is vulnerable to known, published exploits?
I would clean-install 16.04 LTS immediately for that reason alone.

---

### Post by tonma on 2016-11-19
Wow, thank you! 
Didn't know, it's an older machine (not my main), in my main I am using 16.04 though.

Btw, according to what you say, if I ever plan to upgrade from my 16.04 LTS to anything in the future (say 18.04 :o), I have to do it by going 16.10>17.04>17.10...?

---

### Post by Impavidus on 2016-11-19
No, you can go directly from one LTS release to the next LTS release.

---

### Post by tonma on 2016-11-19
Thank you! :D

---

### Post by mörgæs on 2016-11-19
Since you mentioned that the computer is old you could use the opportunity to install a lighter desktop environment than Ubuntu, say X/Lubuntu. They also have long term support but only three years as opposed to five years for Ubuntu.

---

