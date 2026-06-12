---
title: "Can't update to 10.10 from10.04"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by campb.andrew on 2010-12-08
Earlier today, i was updating to 10.10, but canceled because i had to go somewhere. Now i want to start the update again and the update manager isnt showing me that there is an update available...:-( I dont know what to do...

HELP! Please??

---

### Post by sikander3786 on 2010-12-09
Were any packages being installed while you cancelled the process or they were just being retrieved?

We need to see the output of these commands.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

If there are no errors reported, go to System > Administration > Software Sources > Updates Tab and make sure Normal Release is selected under New Release Notification or something like that. Then this one,

```
sudo do-release-upgrade
```

---

