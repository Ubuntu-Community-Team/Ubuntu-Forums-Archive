---
title: "not able to upgrade 20.10 from 20.04"
date: 2021-05-22
forum: Installation &amp; Upgrades
---

### Post by sainim007 on 2021-05-22
i am getting error when i am refreshing cashe and also new upgrade of 20.10 is available for my laptop but when i click on upgrade it doesn't download. please help if any one know about this proble

---

### Post by TheFu on 2021-05-22
10.10 has been unsupported since 2011. Of course you can't upgrade that. Do a fresh install.
BTW, getting details correct is very important in computing.

---

### Post by mIk3_08 on 2021-05-22
Ubuntu 10.10 you mean?
Maybe your try to say is that you are going to downgrade the system from Ubuntu 20.04 to Ubuntu 10.10.
I don't think you can do that. I never heard such a thing downgrading a system from a higher version system to a lower version system. 
If there is such thing like that, maybe it's a rare thing.
TheFu is right; you need a new fresh copy of the Ubuntu 10.10 and install it. Maybe that help.

---

### Post by dddman on 2021-05-23
It's still out there
[https://old-releases.ubuntu.com/releases/maverick/](https://old-releases.ubuntu.com/releases/maverick/)

Maybe you can stick a new kernel in it and call it kinda sorta good?  I don't know, mileage may vary.

---

### Post by deadflowr on 2021-05-23
Title fixed,
as every other indicator shows it's about moving from 20.04 to 20.10.

Perhaps think try running apt update/upgrade commands.
```
sudo apt update
sudo apt upgrade
```
and post back any results.

(Best to copy and paste the output rather than posting screenshots,
just use code tags to properly format the output in a post see [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")


Also, any reason to be in the Developer Options section of Software and Updates,
or was that just coincidence or something?

---

### Post by grahammechanical on 2021-05-23
I think you should know that Ubuntu 20.04 has at least 5 years of life support starting from April 2020 but 20.10 has only 9 months support starting from October 2020. If you do manage to upgrade to 20.10 you will find yourself in a traffic jam of upgrading. Ubuntu 20.10 reaches end of life in July 2021, then you must upgrade to 21.04 and then in January 2022 you will have to upgrade to 21.10 and then to 22.04 before you get to an OS that has 5 years support.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Regards

---

