---
title: "Upgrade 8.10 Server to 12.04 Server"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by geraldbrandt on 2012-05-04
Hi,

Is it possible to upgrade from 8.10 server to 12.04 server?

I tried, and I get this:


# do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 

Gerald

---

### Post by darkod on 2012-05-04
8.10 is not a LTS release. As such it would have only 3yrs support from 10/2008 which means support is expired.

Also, not being a LTS it can only upgrade to the next version, 9.04 which also has support terminated.

It might be possible to upgrade using the server cd, but I'm not sure if it would be better to try to upgrade to 10.04 LTS first. It's kind of a huge jump from 8.10 to 12.04.

Plus 12.04 is just released and upgrade of servers is not really recommended in the first few months and until you do all the testing how will it work for you.

---

### Post by CharlesA on 2012-05-04
8.10 is EoL. In order to upgrade it you would have to do each hop up until at least 10.04, then upgrade to 12.04 from there.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I would recommend a clean install in any case.

---

### Post by geraldbrandt on 2012-05-04
Perhaps I should have been more clear.  I understand I would need to step up from 8.10 to 9.04 to 9.10, etc.  Heck, I'm even willing to stop at 10.04 right now.  Normally I only run LTS's, but I needed something specific that wan't in 8.04 at the time.

As can be seen from my original post, the upgrade from 8.10 to 9.04 fails:

# do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading 
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 

Gerald

---

### Post by snowpine on 2012-05-04
See here for instructions on End Of Life upgrades:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Since you are **six** releases out-of-date, I really do recommend a **test drive** of 12.04 on a non-production machine, followed by a fresh reinstall and migration. Good luck!

---

### Post by CharlesA on 2012-05-04
> **geraldbrandt said:**
> Perhaps I should have been more clear.  I understand I would need to step up from 8.10 to 9.04 to 9.10, etc.  Heck, I'm even willing to stop at 10.04 right now.  Normally I only run LTS's, but I needed something specific that wan't in 8.04 at the time.

As can be seen from my original post, the upgrade from 8.10 to 9.04 fails:

# do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading 
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 

Gerald
[https://help.ubuntu.com/community/EOLUpgrades/Intrepid](https://help.ubuntu.com/community/EOLUpgrades/Intrepid)
[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

+1 to test drive.

---

### Post by geraldbrandt on 2012-05-04
> **snowpine said:**
> See here for instructions on End Of Life upgrades:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Since you are **six** releases out-of-date, I really do recommend a **test drive** of 12.04 on a non-production machine, followed by a fresh reinstall and migration. Good luck!

Thanks!

---

### Post by geraldbrandt on 2012-05-04
> **CharlesA said:**
> [https://help.ubuntu.com/community/EOLUpgrades/Intrepid](https://help.ubuntu.com/community/EOLUpgrades/Intrepid)
[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

+1 to test drive.

The EOLUpgrades don't work either.  After adding the repos and updating, I get the same error:


# do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 

Gerald

---

### Post by neuling1 on 2012-07-31
Hello guys,

right now I'm working at the same issue. In our company we have an old server running 8.10 - the services should now be split on to 3 virtual machines, which run 12.04.
So I already have 12.04 installed on the new servers and need to migrate the configuration of the old 8.10 server to these new servers.

Is there any HowTo or something like that, which can tell me how to accomplish this migration? Or maybe someone of you knows how to do this, since you mentioned migration?

Thanks!

---

### Post by CharlesA on 2012-07-31
It would depend on what services are being used. Sometimes config files change between releases, especially when you are using one that is EOL.

---

### Post by neuling1 on 2012-07-31
I have...
appache
SVN
Typo3
vBulletin
and FTP...
running on it.

I really don't know which is the best way to accomplish this task. Since I have the virtual machines already installed with 12.04 I would prefer a migration...since I have ssh access to the old server, I thought that I could maybe just copy the needed files and directories to the new virtual machines via scp!?

But since you mentioned the problem with changing config files it would maybe be a better idea to install 8.10 on the virtual machines -> make an image of the old system -> put the image on the virtual machines -> upgrade the virtual machines from 8.10 to 12.04

...but maybe someone of you knows a better approach?

---

### Post by CharlesA on 2012-07-31
You could also do a diff between the old and new config files and see what changes were made.

Also: Backup, backup, backup. ;)

---

