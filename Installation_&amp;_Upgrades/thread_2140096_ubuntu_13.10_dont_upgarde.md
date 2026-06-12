---
title: "ubuntu 13.10 dont upgarde"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by albaniaguard on 2013-04-28
hi
i have 12.10 version and i try to upgardr to 13.04 but i cant,when i try to upgarde i set the code,dont doing nothing...:???::???::???:
what i can doing?

soryyy 13.04

---

### Post by MAFoElffen on 2013-04-28
13.04 was released days ago. Dev version 13.10 repo's were "just" set up but is only days into it, so there are only minute changes if any, so far.  

Are you really trying to go to 13.10? If you do want to live on the edge, have lots of patience and want to do dev testing, go to the "Ubuntu +1" forum and follow the instructions there... What it entails (this early on) is changing your repo's to the dev repo (manually w/ SED) and doing a do-release-upgrade.

...Otherwise, you might want to try 13.04 first.

---

### Post by albaniaguard on 2013-04-28
i edit the post,i try for 13.04 from update menu and i cant..

---

### Post by deadflowr on 2013-04-28
Go to the system settings, and then go to software sources and open it.
Then go to updates and look at the part that says 
Notify me of new versions, and select "For any new version."
Then run the software updater.

---

### Post by ibjsb4 on 2013-04-28
Try this

[https://help.ubuntu.com/community/RaringUpgrades#Upgrade_from_12.10_to_13.04_Beta](https://help.ubuntu.com/community/RaringUpgrades#Upgrade_from_12.10_to_13.04_Beta)

---

### Post by albaniaguard on 2013-04-28
i find the new version ij update menu,but when i try to install dont work...

---

### Post by MAFoElffen on 2013-04-28
You are currently on 12.10 right?

Try this:
```

sudo do-release-upgrade

```
Tell us if it works or gives you an error. If it returns an error, please post that error here...

---

### Post by albaniaguard on 2013-04-28
thankyou varyyy muchhhh

---

### Post by ibjsb4 on 2013-04-28
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

