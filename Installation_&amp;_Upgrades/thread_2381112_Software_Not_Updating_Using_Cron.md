---
title: "Software Not Updating Using Cron"
date: 2017-12-27
forum: Installation &amp; Upgrades
---

### Post by arnold.pietersen on 2017-12-27
Hi

I am running the following cron job every day at 1 o clock in the mornings in /etc/crontab:

0  1    * * *   root    apt-get update >> /home/arnold/ubuntu-update-cron.log

The log file has the following entries:

Hit:1 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:3 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:4 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:5 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Get:6 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [217 kB]
Get:7 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [185 kB]
Get:8 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [261 kB]
Get:9 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Get:10 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:11 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4,712 B]
Get:12 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [62.4 kB]
Get:13 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [57.6 kB]
Get:14 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [51.3 kB]
Get:15 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Fetched 1,547 kB in 11s (130 kB/s)
Reading package lists...

However, when I run System Tools -> Administration -> Software Updater, it show a number of software packages which requires updating.

Any help will be appreciated in tweaking the cron to update the software packages.

Kind Regards

ARNOLD

---

### Post by Impavidus on 2017-12-27
apt-get update will only refresh the list of available upgrades, it won't install any upgrades. And you're creating an ever-growing and probably root-owned log file in your home directory.

But there's no need to do it this way. Open your software updater and check its settings. There should be a setting to check for updates daily or some other interval and security updates can even be installed automatically. Also look into unattended upgrades, which can install all updates automatically and autoremove old packages. Some disable it because they want to know when something gets upgraded.

Checking and installing updates automatically won't make it run at a fixed time of the day, but it will work even if your computer is off or off-line at 1 o'clock. It will typically run shortly after boot or shortly after midnight.

---

### Post by arnold.pietersen on 2017-12-28
Hi Impavidus

Thanks for your reply.

I have free bandwidth between 12 midnight and 7AM in the morning. Thus, I want my system to automatically update between that time. Even if the update packages just download between that time, that will be fine.

Kind Regards

ARNOLD

---

### Post by deadflowr on 2017-12-28
You can set up cron-apt to set a very specific time:
[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo#cron-apt_method]("https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo#cron-apt_method")

---

