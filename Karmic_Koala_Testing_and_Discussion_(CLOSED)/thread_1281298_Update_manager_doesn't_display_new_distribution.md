---
title: "Update manager doesn't display new distribution"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by imafatmess on 2009-10-03
I run update manager -d, and I don't get the option to upgrade. I've heard from an untrustworthy source to run sudo apt-get dist-upgrade if theres any issues.

Anyway, can anyone help?

Thanks :)

---

### Post by SlugSlug on 2009-10-03
sudo apt-get dist-upgrade - upgrades your current distribution

$ sudo do-release-upgrade  installs the the next distribution release

---

### Post by imafatmess on 2009-10-03
> **SlugSlug said:**
> sudo apt-get dist-upgrade - upgrades your current distribution

$ sudo do-release-upgrade  installs the the next distribution release

Thanks, I thought it was that. And as I posted it i tried do-release-upgrade -d which worked :)

Anyway, any reason for it not appearing in update-manager?

---

### Post by SlugSlug on 2009-10-03
depending on what your upgrading from / to  you need to check out your config in /etc/update-manager

heres mine

# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
Prompt=normal

---

### Post by dixelpixel on 2009-10-16
The new distribution Ubuntu 8 does not show in my update manager either, it only suggests a further version of my current Ubuntu 7.
I cannot update to either updated versions of my current Ubuntu 7 or to the new distribution using the above commands.

My error message in terminal is as follows:

name@name:~$  sudo do-release-upgrade
Password:
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting '/tmp/tmpV_iVss/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 45, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1139, in open
    return func(name, "r", fileobj)
  File "/usr/lib/python2.5/tarfile.py", line 1200, in gzopen
    fileobj = file(name, mode + "b")
IOError: [Errno 2] No such file or directory: '/tmp/tmpV_iVss/gutsy.tar.gz'

---

### Post by dixelpixel on 2009-10-16
Ooops... I realize I have posted this in the Karmic Koala forum. Sorry.

It's just that the headline fitted my enquiry perfectly, although I am looking to get moving onto Hardy Heron or Intrepid Ibex. Let's hope all you Karmic Koala people will take pity on me anyhow...

---

