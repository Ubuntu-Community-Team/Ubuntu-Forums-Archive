---
title: "Unable to upgrade from 19.04 to 19.10"
date: 2019-12-11
forum: Installation &amp; Upgrades
---

### Post by dougiepunk on 2019-12-11
When I click Upgrade  the Software Updater dialog disappears but nothing else happens. I've done all the 
sudo apt-get update && sudo apt-get upgrade

stuff, so as far as I know 19.04 is completely up-to-date. Help!

---

### Post by #&amp;thj^% on 2019-12-11
If you&#8217;re the kind of Ubuntu user who prefers a solid and inherently stable system I recommend you install Ubuntu 18.04 LTS, which will receive on-going updates until 2023.

Note: if automatic login is enabled you should disable it before attempting to upgrade. There are reports that leaving auto-login enabled during an upgrade will cause a login loop issue on restart.
And don&#8217;t forget: you can always download an ISO and do a fresh install too.
**_This really should of been done before October 17th._**
But you did not so, your on your own here with:
You can forcibly &#8220;check&#8221; for a new Ubuntu release using the terminal app and the following command:

```
sudo do-release-upgrade -c -d
```
Or the confident way:
```
sudo do-release-upgrade -d
```

Follow the onscreen prompts that appear.

Be careful; as soon as you run this command Ubuntu will check for a new development release,**VERY IMPORTANT>>>>** disable all PPAs, and fill your apt list with links to the eoan development branches.

---

### Post by dougiepunk on 2019-12-11
Hm. If I use either of those upgrade commands I get:

Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.

---

### Post by dougiepunk on 2019-12-11
But the Software Updater does offer to upgrade. Its just that nothing happens when you hit the Upgrade button...

---

### Post by ubfan1 on 2019-12-11
Check the thread [https://ubuntuforums.org/showthread.php?t=2432903](https://ubuntuforums.org/showthread.php?t=2432903)  Sounds like your problem.  Solved by removing all additional PPAs, then update/upgrade.

---

### Post by kansasnoob on 2019-12-11
> **1fallen said:**
> If you’re the kind of Ubuntu user who prefers a solid and inherently stable system I recommend you install Ubuntu 18.04 LTS, which will receive on-going updates until 2023.

Note: if automatic login is enabled you should disable it before attempting to upgrade. There are reports that leaving auto-login enabled during an upgrade will cause a login loop issue on restart.
And don’t forget: you can always download an ISO and do a fresh install too.
**_This really should of been done before October 17th._**
But you did not so, your on your own here with:
You can forcibly “check” for a new Ubuntu release using the terminal app and the following command:

```
sudo do-release-upgrade -c -d
```
Or the confident way:
```
sudo do-release-upgrade -d
```

Follow the onscreen prompts that appear.

Be careful; as soon as you run this command Ubuntu will check for a new development release,**VERY IMPORTANT>>>>** disable all PPAs, and fill your apt list with links to the eoan development branches.

The "-d" suffix is only used for upgrading to a development version!

---

### Post by kansasnoob on 2019-12-11
If you'd copy-n-paste the full output from terminal of the command "sudo apt update" that would give us some idea what condition the repos are in. Then we could make a better guess.

---

### Post by dougiepunk on 2019-12-13
Thanks for the answers. guys. I ended up just doing a fresh re-install :D

---

