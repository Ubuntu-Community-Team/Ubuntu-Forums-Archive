---
title: "Upgrading 6.06.2 LTS to 6.10"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by jfcous on 2008-05-15
I used lsb_release -a to determine the version and then ran gksu "update-manager" -d to upgrade.  The upgrade manager said that no updates were available.  

How do I upgrade to 6.10 (and eventually to the latest version)?

thank you,
jfcous

---

### Post by dstew on 2008-05-15
I am not familiar with lsb_release, but the usual command line way to upgrade to a new version is```
sudo apt-get update
sudo apt-get upgrade
sudo do-release-update
```

---

### Post by jfcous on 2008-05-15
Appreciate your response.  I would have gone that route but the upgrade instructions on the Ubuntu website states:

"Upgrading using apt-get -- NOT RECOMMENDED

Please note - this method is much less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectedly, etc. Using Update Manager (see above) is likely to be much less problematic."

My level of inexperience is such that I would have trouble resolving problems.

Any suggestions?

thanks again,
jfcous

---

### Post by dstew on 2008-05-15
Can you give me the link to that warning? I think it means you should not try to do a release upgrade using apt-get, which I think would essentially be impossible. But the apt-get update and upgrade commands have to do only with updating your currently installed system, not with doing a release upgrade. Apt-get upgrade is the same thing as doing an update with the graphical Update Manager tool. There is an inconsistency in vocabulary that extends also to the do-release-update command.

The command do-release-update is what gets you the command-line interface to upgrade to a new version.

---

### Post by jfcous on 2008-05-15
Here is the link:

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by dstew on 2008-05-15
I did not see any advice there on using do-release-upgrade. Perhaps it is not available in 6.06. Anyway, do the two apt-get commands I recommended first, and then do```
gksudo "update-manager -c"
```Note that the Update Manager will say "Your System is Up-To-Date" if you have all the latest 6.06 software. But, there should be a "Upgrade to 6.10" button at the top of the Update Manager window. That is the one you want.

The method of upgrading to 6.1 using all apt-get has the problem of editing the sources.list, that is why it is not recommended. It sort of fools the package manager into getting packages for the 6.1 system using the software that usually only is used to update the current system. I would not recommend that method. It would probably be better to do a fresh install using a CD.

---

### Post by jfcous on 2008-05-15
I tried the commands that were posted but the final command "sudo do-release-update" resulted in a "command not found"  

jfcous

---

### Post by dstew on 2008-05-15
Yes, see above, I do not think that command was available in 6.06, only in later versions. Do you see the upgrade button on the Update Manager window?

---

### Post by demetrisk on 2008-05-15
The second link has instructions to upgrade directly from 6.06 to 8.04:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by jfcous on 2008-05-15
> **dstew said:**
> Yes, see above, I do not think that command was available in 6.06, only in later versions. Do you see the upgrade button on the Update Manager window?

No upgrade button shows up.

---

### Post by jfcous on 2008-05-15
> **demetrisk said:**
> The second link has instructions to upgrade directly from 6.06 to 8.04:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Tried the second link but no upgrade option showed up.  I will try again later.

thanks,
jfcous

---

### Post by dstew on 2008-05-15
Did you enable the dapper-updates channel first?

---

