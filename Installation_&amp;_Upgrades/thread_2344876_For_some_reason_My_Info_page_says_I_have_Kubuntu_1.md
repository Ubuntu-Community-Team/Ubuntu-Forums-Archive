---
title: "For some reason My Info page says I have Kubuntu 17.04"
date: 2016-11-28
forum: Installation &amp; Upgrades
---

### Post by reb682 on 2016-11-28
I don't know how I skipped 16.10 but When I do info It says Kubuntu 17.04. I am having trouble with updates (daily) and with Synaptic. Am I really in 17.04. My updates say I have no Release program. This is what I get in Synaptic.
_______________
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
The repository 'http://ppa.launchpad.net/ondrej/php/ubuntu zesty Release' does not have a Release file.Updating from such a repository can't be done securely, and is therefore disabled by default.See apt-secure(8) manpage for repository creation and user configuration details.The repository 'http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu zesty Release' does not have a Release file.
------------------
I do not know how to overcome this. Do I set my repositories to "Pre release"

---

### Post by oldos2er on 2016-11-28
I would temporarily disable the [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) PPA; the error you're seeing occurs because there is no "zesty" version of it available.

Can you post the output of ```
cat /etc/apt/sources.list
``` If you ran a version upgrade recently, how exactly did you do so? What Kubuntu version were you running previously?

---

