---
title: "Failed, Incomplete upgrade &gt; ubuntu 10.04 beta"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by mitulv4u on 2010-04-02
Hey,

I tried upgrading to the new beta version 10.04 from 9.10 but th computer hung in between and made a restart itself.....it had completed downloading and around 30% of up gradation, the time it hung. Now i am facing problems while rebooting and the Option for upgrading to new distro cannot be seen in Update Manager anymore. Can anyone tell me how can i continue from where it stopped or even restart the upgradation process.


Thanks

---

### Post by akakingess on 2010-04-02
I hope someone corrects me if/when I am wrong, but I believe you can do it from the terminal by doing a sudo apt get update -d ( I think the d is for distribution), again I may be mistaken, but I do know there is a way to do it from the terminal (maybe an update? or update --help) will give you the exact vernacular, but not sure if it will work for a beta release. Also, you could I guess download the release onto another computer and burn it to disk and do it that way. Just some suggestions, I hope someone else can help more than I can as my brain is now officially fried (time for bed), good luck to you.

---

### Post by deeminter on 2010-04-02
akakingess is correct in his reply, you can upgrade with package replacements of an incomplete or corrupt install. I had the same thing happen to me during my installation of 10.04 Beta 1. I used the terminal command apt-get dist-upgrade to fix the problem. Hope you are able to install and enjoy the latest Ubuntu offering.

---

### Post by mitulv4u on 2010-09-14
Thanks a lot...it works fantastic.

---

