---
title: "upgrade from feisty to gutsy fails"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by operror on 2007-10-24
The upgrade fails with the following message.

'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  mudeb/source/Sources in Meta-index file (malformed Release file?)'


I installed feisty from CD three weeks ago.   I attempted to use the update button on the Update Manager and the process fails consistently at the same point.  I have ensured that the address in the message is reachable.


Below are the /var/log/dist-update logs:

------- main.log --------------

2007-10-24 10:20:35,313 INFO release-upgrader version '0.81' started
2007-10-24 10:20:37,378 DEBUG lsb-release: 'feisty'
2007-10-24 10:20:37,378 DEBUG _pythonSymlinkCheck run
2007-10-24 10:20:38,412 DEBUG checkViewDepends()
2007-10-24 10:20:39,158 ERROR IOError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  mudeb/source/Sources in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 0)
2007-10-24 10:20:39,936 ERROR IOError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  mudeb/source/Sources in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 1)
2007-10-24 10:20:40,682 ERROR IOError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  mudeb/source/Sources in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 2)
2007-10-24 10:20:40,682 ERROR doUpdate() failed complettely


--------------  end main.log   ---------------------------

------- main_pre_req.log -----------------------------------
2007-10-24 10:20:23,359 INFO release-upgrader version '0.81' started
2007-10-24 10:20:24,046 DEBUG lsb-release: 'feisty'
2007-10-24 10:20:24,047 DEBUG _pythonSymlinkCheck run
2007-10-24 10:20:25,097 DEBUG checkViewDepends()
2007-10-24 10:20:25,098 DEBUG getRequiredBackports()
2007-10-24 10:20:26,317 ERROR IOError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  mudeb/source/Sources in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 0)
2007-10-24 10:20:27,125 ERROR IOError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  mudeb/source/Sources in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 1)
2007-10-24 10:20:28,170 ERROR IOError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  mudeb/source/Sources in Meta-index file (malformed Release file?)
'. Retrying (currentRetry: 2)
2007-10-24 10:20:28,170 ERROR doUpdate() failed complettely
2007-10-24 10:20:30,873 DEBUG marking 'release-upgrader-apt' for install
2007-10-24 10:20:30,976 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-24 10:20:35,018 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1924684 DestFile:'/tmp/tmpkGsYB2/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2'
2007-10-24 10:20:35,019 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1307096 DestFile:'/tmp/tmpkGsYB2/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb' DescURI: 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-apt/release-upgrader-apt_0.6.46.4ubuntu10.'
2007-10-24 10:20:35,020 DEBUG extracting udeb '/tmp/tmpkGsYB2/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb'
2007-10-24 10:20:35,094 DEBUG extracting udeb '/tmp/tmpkGsYB2/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb'

---------------- end main_pre_req.log -------------------------


Any help would be appreciated,
Operror

---

### Post by Bablefish on 2007-10-24
Call this just an observation but there have been quite a few posts like this. I am beginning to wonder if it's the same problem some people have experianced when upgrading Windows. In where trhe only fix was to do aclean install.

---

### Post by operror on 2007-10-29
sudo apt-get update


Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 0s (4B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release)  Unable to find expected entry  mudeb/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by snickers295 on 2007-10-29
try to download the alternate cd and when your system is running, put the cd in and a window should pop-up and tell you you can upgrade from it.
if that doesn't work then do a clean install.

---

