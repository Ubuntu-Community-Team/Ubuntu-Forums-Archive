---
title: "Upgrade 16.04 LTS to 18.04 LTS"
date: 2022-03-13
forum: Installation &amp; Upgrades
---

### Post by azharaziz on 2022-03-13
Hi,

Can I know upgrading the version mention above is available?
I recently have difficulty.

Thanks.

---

### Post by guiverc on 2022-03-13
Ubuntu 16.04 has been *end of public* support for some time, so upgrades will now be much more difficult than before it's *end of public support* was reached.

- [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

A 16.04 system will have *expired* [certificates]("https://ubuntu.com/security/notices/USN-5089-2"), so may refuse to use some web sites (*as it's internal certificates will show the site as potentially risky** unless internal certificates were manually upgraded OR ESM support was added and replacement certificates were discovered and installed*). Whether or not this will impact you may depend on your ISP, which mirror you're using etc, so it'll impact some users more than others. (*example of upgraded package question can be found here - [https://askubuntu.com/questions/1378534/update-the-certificates-on-ubuntu-16-04-tls](https://askubuntu.com/questions/1378534/update-the-certificates-on-ubuntu-16-04-tls)*)

Yes problems can be expected anytime after *end of public* support is reached.  Your actual messages though will provide the most clues; and your question is missing any specifics.

---

### Post by grahammechanical on 2022-03-13
What is the difficulty that you are experiencing with 16.04? Is the failure to update/upgrade 16.04?

Ubuntu reached end of its support life April 29, 2021. The time to upgrade to Ubuntu 18.04 was the beginning of April 2021. The software sources/repositories for 16.04 have been moved to old-releases/ubuntu.com. This is a different internet address to the internet address for the software sources on your 16.04 installation.

[http://old-releases.ubuntu.com/releases/16.04.4/](http://old-releases.ubuntu.com/releases/16.04.4/)

You need to perform an End Of Life upgrade. This means editing the internet address in your /etc/apt/sources.list text file to the internet address for old-releases/ubuntu.com. This is how you do it:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you do not feel confident to do that then it would be better to backup the data that you do not wish to lose and do a fresh install of Ubuntu 20.04 and be ready to upgrade to Ubuntu 22.04 some time before April 2025.

Regards

---

### Post by rsteinmetz70112 on 2022-03-15
What difficulty did you encounter? I assume you attempted a do-release-upgrade. Please be specific. 

Many people do not use the do-release-upgrade but rather prefer to do a fresh install. You can still download the isos for 16.04 LTS and 18.04 LTS to do a fresh install.

You may not need to jump through all of those hoops. First, archives are not moved to old releases exactly on the stroke of midnight and often are available for some time after the end of official support. Extended Security Release is also available for free for up to 3 machines. I don't subscribe but you can register here [https://ubuntu.com/advantage](https://ubuntu.com/advantage) it is available until April 2026. Once registered you should be able to do-release-upgrade.

---

