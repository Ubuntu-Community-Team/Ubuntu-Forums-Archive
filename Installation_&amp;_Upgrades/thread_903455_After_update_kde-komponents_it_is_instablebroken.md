---
title: "After update kde-komponents it is instable/broken"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by JanvL on 2008-08-28
Hello,

Yesterday I became from Adept the notification that a lot of KDE-programms were "updateable", so I downloaded and installed with Adept. Today I have a broken KDE environment, I cannot drag windows, have no header to maximize/miminize or close the windows, and no 4 desktops, just 1.

I tried to repair with synaptic, ran Adept to see if I missed a part, with no effekt. Even repaired X on boot but no result.

Does someone have an idea how to solve this?

Thanks in advance,
Janvl

I have installed the full 3.5.10 KDE-package as it is in Adept, strange enough kde-base was "not installed". After that even with booting, no luck.
Now I have entered the system as root, and there I have all the normal features so there must be something wrong with the permissions, I will dig further.

I just made another user, and this one has little permissions on the system but a working KDE-environment. So I will have to see to it to make a new user from the old one  . . .  and copy the homedirectory, carefully not to copy the problem  . .

So, as root, I de-activated myself as user. Carefull to keep all my data in my home-directory "/home/user". Then I renamed my  homedirectory to "/home/old-user" and made a new user that became homedirectory "/home/user" this one was functional in KDE 3.5.10. After that I could move all the dot-directories (and some files) for all applications back to the /home/user" directory, BUT NOT the KDE-configurationfiles!!!!!!! 

Now I have a functioning system again, it only took 4 to 6 hours . . .

I do not know what went wrong with this KDE update, I alway installed them on Dapper and have never had a problem like this so if some developer from Ubuntu reads this please condider what could have caused it and try to avoid it.
Contact me if there are questions.

Still I like Hardy.

---

### Post by JanvL on 2008-09-15
The update was incomplete.
Installed the new version complete (same day) and had it running again.
Now I have all KDE programma so I will have to clean up afterwards, had no time until now.

---

