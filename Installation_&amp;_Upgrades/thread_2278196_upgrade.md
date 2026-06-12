---
title: "upgrade"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by zhenia on 2015-05-14
I am trying to update my relatively old (12.04) system but get
do-release-upgrade
```

Checking for a new Ubuntu release
Err Upgrade tool signature                                                     
  404  Not Found [IP: 91.189.88.149 80]                                        
Err Upgrade tool                                                               
  404  Not Found [IP: 91.189.88.149 80]                                        
Fetched 0 B in 0s (0 B/s)                                                      
WARNING:root:file 'quantal.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.
```

same via update manager
it shows new version 12.10 is available (I know it is not the latest but I guess I cannot jump it over)
and when i try to upgrade it says "Fetching the upgrade failed. There may be a network problem"

tried
sudo update-manager -d
got
WARNING:root:nothing unsupported running 0 (0)

any idea on what i should do?

---

### Post by grahammechanical on 2015-05-14
There is a network problem. The repositories for 12.10, 13.04 and 13.10 have been archived because those releases have reached end of life. The links to the repositories no longer work. The repositories have been moved to the old-releases archive/server.

You need to change the URLs in the software sources list files using this wiki page as a guide.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Keep in mind that because 13.04 is end of life you will have the same network problems when you have upgrade to 13.04. So, you will have to repeat the process to get on to 13.10 and then you will be able to use Update Manager to upgrade to 14.04.

It is a lot of upgrading and that is why we recommend doing a fresh install of 14.04. Here is another issue to think about. Can that machine run Ubuntu 14.04? Is the video adapter still supported by the latest proprietary video drivers in 14.04? You might need to think about switching to another member of the Ubuntu family.

Either way, I advise to revert to an open source video driver before upgrading.

As you are on 12.04 you should be able to upgrade directly to 14.04. Go to System Settings>Software & Updates and make sure that it is set to notify you of the next LTS release and not the next release. Then you should be offered the opportunity to upgrade to 14.04.

Regards.

---

### Post by zhenia on 2015-05-14
thanks, i can see the 14.04 update possibility now - how do i check the video adapter? which one do i need? sorry, i am really a newbie...

---

### Post by mörgæs on 2015-05-14
You have posted a lot of problems lately. Wasn't it better to erase everything and do a fresh install?

---

### Post by mattharris4 on 2015-05-18
^ I was thinking this anyway even not knowing the OP's history.  I have read too many people having problems with the upgrade function in the Canonical OSes and in most of the cases a fresh install of whatever the person was attempting to upgrade to eliminated the problems.  This also allows a person to use the live CD or USB function to see if the wireless card, video card, etc. function properly before installing (and wiping out a working prior-version install).  I suspect this would be more important with older computers (say pre-2005 or so) where support for parts of the computer may have been removed from the OS in order to keep it at a reasonable size and because Linux programmers assumed that no one was still using the equipment requiring the removed drivers.  Also, Ubuntu 12.04 is supported until April 2017 (although the lesser Canonical OSes versions 12.04 such as Lubuntu 12.04 have exhausted support).

---

### Post by mörgæs on 2015-05-19
It does happen that hardware support is removed but it's a rare event. Main rule is that newer kernels provide better support for both new and old hardware.

---

