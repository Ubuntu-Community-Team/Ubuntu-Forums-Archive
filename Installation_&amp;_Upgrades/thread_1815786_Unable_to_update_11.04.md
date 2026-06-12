---
title: "Unable to update 11.04"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by Entyrion on 2011-07-31
I've been out of the country for several months and was unable to update my 11.04 computer. Now, when I try to update, it says I need to do a partial upgrade first. After I select that option, the update process then fails because it says it was unable to access the proper repositories or some such. I'm really not sure what I should do to fix this and update my distro. Any help would be appreciated. Screenshots are attached. Thanks in advance!

---

### Post by Foxheadz on 2011-08-01
Seems you just have outdated ppa(s) open the Software center and from there go edit>software sources>other software and remove the ones that are causing you problems.

---

### Post by Entyrion on 2011-08-01
Alright, but all of those PPAs seem to be related to Unity2D... if I remove them, doesn't that mean that my Unity2D will no longer be updated?

---

### Post by Foxheadz on 2011-08-01
Yes, you will have to find the working ppa, from what i can find it's this one [https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

---

### Post by varunendra on 2011-08-01
Unity 2D is in default repositories. You shouldn't need ppa's for it. If you do, just remove it and reinstall from default repository.

---

### Post by Entyrion on 2011-08-01
Thanks for your help guys! I deleted the old repositories, then uninstalled and reinstalled Unity2D via the USC to be on the safe side and the computer updates smoothly now!

---

