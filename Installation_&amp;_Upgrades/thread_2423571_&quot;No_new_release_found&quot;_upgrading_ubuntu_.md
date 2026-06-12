---
title: "**&quot;No new release found&quot; upgrading ubuntu from 16.04 to 18.04 LTS"
date: 2019-07-25
forum: Installation &amp; Upgrades
---

### Post by nareshnani529 on 2019-07-25
Hi, 

Trying to upgrade a VM in our infrastructure which is initially 14.04LTS trusty, we successfully able to upgrade to 16.04LTS,the actual objective to have the VM on ubuntu 18.04LTS. When I tried form 16.04 t 18.04LTS its says

sudo do-release-upgrade / -d

"No new release found"

Any suggestions will be helpful in this regard. Thank you!

---

### Post by deadflowr on 2019-07-25
Run without the -d flag.
Also, since there are no releases supported anymore between 16.04 and 18.04 see if running it to look for any new release works
versus running it with to only look for lts releases.

You can switch the option in the file /etc/update-manager/release-upgrades.
edit the prompt= to prompt=normal to check any new release.
then run an apt update then try do-release-upgrade.

---

### Post by nareshnani529 on 2019-07-25
Thanks for your reply on this!

Tried both do-release-upgrade and -d" came up with same message " No new release upgrade" and to before this performed these steps and did upgrade step. No luck. Any further advice would be appreciated! And am performing this on VMware.

sed -i 's/changelogs.ubuntu.com/apt/' /etc/update-manager/meta-release
sed -i 's/Prompt=never/Prompt=lts/' /etc/update-manager/release-upgrades

---

### Post by rsteinmetz70112 on 2019-07-25
Did you actually change /etc/update-manager/release-upgrades to Prompt=lts?
Does "sudo apt update" work on your 16.04? 
Does "sudo apt upgrade" work on your 16.04?
Have you tried to install or reinstall update-manager-core?
I've recently done several release upgrades (not on VMware) and they all recognized the new lts release was available and even told me it was there.
Sorry if this is too basic, I'm not sure exactly what has already been tried.

---

### Post by nareshnani529 on 2019-07-28
Verified all your steps mentioned and tried. Still the same message. Not able to get the issue, for testing on another machine I tried 14.04lts trusty to 16.04 Xenial with out no issues. But from 16.04lts to 18.04lts its gives same message " No new release found".

* it was able to apt update and upgrade & ping.

---

### Post by rsteinmetz70112 on 2019-07-29
Have you tried to install or reinstall do-release-upgrade?

```
# sudo apt install do-release-upgrade
```

If it's installed it should tell you the most recent version is already installed.

You might try to reinstall it

```
# sudo apt install --reinstall do-release-upgrade
```

Finally or maybe first you can run a check to see if everything is installed correctly?

```
# sudo dpkg --configure -a
# sudo apt install -f
```

Just another little note I recently discovered that do-release-upgrade does not need to be run as superuser, it will prompt for authorization after it downloads the files it needs.

---

