---
title: "Continue to use Xubuntu 13.04"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by gabbello on 2014-08-14
Hello,

I have a xubuntu 13.04 installed on a rather old laptop and I would not like to upgrade to newer versions due to amount of time it takes, possible incompatibilities with HW and also due to the fact that I got a few hints online that 13.04 is actually better in terms of performance on old machines than newer versions.

However right now I can no longer use the ppa/repositories as they seem discontinued, eg:

```
sudo apt-get install openssh-server 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ncurses-term python-requests python-urllib3 ssh-import-id
Suggested packages:
  ssh-askpass rssh molly-guard monkeysphere openssh-blacklist
  openssh-blacklist-extra
The following NEW packages will be installed:
  ncurses-term openssh-server python-requests python-urllib3 ssh-import-id
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 844 kB of archives.
After this operation, 3,436 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ncurses-term openssh-server python-urllib3 python-requests ssh-import-id
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com/ubuntu/ raring/main ncurses-term all 5.9-10ubuntu4
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com/ubuntu/ raring/main openssh-server amd64 1:6.1p1-4
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com/ubuntu/ raring/main python-urllib3 all 1.5-0ubuntu1
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com/ubuntu/ raring/main python-requests all 1.1.0-1
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com/ubuntu/ raring/main ssh-import-id all 3.14-0ubuntu1
  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/ncurses-term_5.9-10ubuntu4_all.deb  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_6.1p1-4_amd64.deb  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/python-urllib3/python-urllib3_1.5-0ubuntu1_all.deb  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/r/requests/python-requests_1.1.0-1_all.deb  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/ssh-import-id/ssh-import-id_3.14-0ubuntu1_all.deb  404  Not Found [IP: 91.189.92.201 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

Are there any alternative PPAs that I could use (I understand I will not get updates/bugfixes etc), but I would like to be able to at least install packages that I don't have on my machine (or cache) right now.

---

### Post by grahammechanical on 2014-08-14
You will have a problem upgrading anyway. The next version to upgrade to has also reached end of life. It is possible to upgrade but not easy to set up. Likewise with continuing to use an end of life Ubuntu and install software. It is possible.

[http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards.

---

### Post by claracc on 2014-08-14
PPAs will be discontinued too as the release reaches its end of life support, it doesn make any sense to mantain an obsolete repository. You can install software specific for the old release since there are repositories available at [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) but as it is clear you won't obtain any securitu update nor new versions of installed software. In order to use it you will have to change in your file /etc/apt/sources.list all the entries with archive.ubuntu.com by old-releases.ubuntu.com.

It is a security risk to stand on an EOL support release, so I suggest you to backup your /home folder and install one supported as ubuntu 14.04 or 12.04.

If your laptop is old you can think in installing lubuntu 14.04 or ubuntu lxle 12.04 or 14.04.

---

### Post by coffeecat on 2014-08-14
Your system is rapidly becoming a security liability. You won't get better advice than to upgrade or re-install with a supported version. If you are worried about hardware incompatibility, simply download the 14.04.1 ISO for Xubuntu, and run the session live. You can test whether your hardware works without committing to an install.

If you begrudge the amount of time it takes to re-install, then you shouldn't be running a release that has only 9 months life, and would be better off in the long term installing the Long Term Support 14.04 version of Xubuntu, which is supported for three years.

---

### Post by Dennis N on 2014-08-14
One solution is to create a dual boot with 14.04. Then, any time you feel nostalgic, or have some special things on there you need to use, you can start up 13.04 instead. After a while, you will move on. 

Also, Firefox is one vital application you can keep up to date directly from Mozilla.

---

### Post by kansasnoob on 2014-08-14
> **coffeecat said:**
> Your system is rapidly becoming a security liability. You won't get better advice than to upgrade or re-install with a supported version. If you are worried about hardware incompatibility, simply download the 14.04.1 ISO for Xubuntu, and run the session live. You can test whether your hardware works without committing to an install.

If you begrudge the amount of time it takes to re-install, then you shouldn't be running a release that has only 9 months life, and would be better off in the long term installing the Long Term Support 14.04 version of Xubuntu, which is supported for three years.

+1!

Best to pull off the band-aid quickly and be done with it 8-[

I do however continue to remind anyone reinstalling to be acutely aware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

