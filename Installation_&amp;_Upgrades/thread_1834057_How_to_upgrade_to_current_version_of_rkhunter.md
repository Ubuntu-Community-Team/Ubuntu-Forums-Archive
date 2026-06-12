---
title: "How to upgrade to current version of rkhunter?"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by wolfv6 on 2011-08-27
Today I installed rkhunter:D, but an old version got installed:(:

From the terminal```
sudo apt-get install rkhunter
...
sudo rkhunter --versioncheck
[ Rootkit Hunter version 1.3.6 ]
Checking rkhunter version...
  This version  : 1.3.6
  Latest version: 1.3.8
  Update available
```
What is the procedure for upgrading to the latest version?

[http://rkhunter.sourceforge.net/](http://rkhunter.sourceforge.net/) says:
release 1.3.8 obsoletes all previous releases. Please upgrade real soon now.
1.3.8 (17/11/2010) 
1.3.6 (30/11/2009)

I am on Ubuntu 11.04

Thank you.

Should this thread have be posted on "Security Discussions"?

---

### Post by wolfv6 on 2011-08-27
I tried the "update" command.  '1.3.8' was not found, which seems to contradict "Latest version: 1.3.8 Update available".

From the terminal```
sudo apt-get update
...
sudo apt-get install rkhunter=1.3.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '1.3.8' for 'rkhunter' was not found
```
Does this mean that the rkhunter repository is broken?
What other ways are there of getting an update?

---

### Post by whatthefunk on 2011-08-27
You would normally do 
```
sudo rkhunter --update
```

But, I have the same situation and after running the above update command the system says that there are no updates.  Weird...

---

### Post by whatthefunk on 2011-08-27
Okay, figured it out.  The --update command only updates the files for the current version but doesnt upgrade to a newer version.  Go to the rkhunter Source Forge page here:
[http://sourceforge.net/projects/rkhunter/](http://sourceforge.net/projects/rkhunter/)
Download the tar.gz file.  Open up a terminal,go to your downloads directory and do the following:
```
tar xvfz rkhunter-1.3.8.tar.gz
```
```
cd rkhunter-1.3.8/
```
```
sudo ./installer.sh --install
```

That should get the newest version on your system.

---

### Post by wolfv6 on 2011-08-27
Thanks WTF.

Here is how I got rkhunter to work:
Download Rootkit Hunter from [http://rkhunter.sourceforge.net/](http://rkhunter.sourceforge.net/) and untarred it.
Then install and run from the terminal:
```
sudo ./installer.sh --install
sudo rkhunter --versioncheck
sudo rkhunter --update --propupd
sudo rkhunter --checkall
```
It worked.  Got some warnings as expected.

---

### Post by csandrew on 2011-09-08
Thanks WTF and wolfv6, your suggestions worked great on Ubuntu Server 10.04
I'm sorta surprised the ubuntu repositories are so out of date.


Download Rootkit Hunter from [http://rkhunter.sourceforge.net/](http://rkhunter.sourceforge.net/)
```

tar xvfz rkhunter-1.3.8.tar.gz
cd rkhunter-1.3.8/
sudo ./installer.sh --install
...
sudo rkhunter --versioncheck
sudo rkhunter --update --propupd
sudo rkhunter --checkall

```

---

### Post by whatthefunk on 2011-09-08
> **csandrew said:**
> Thanks WTF and wolfv6, your suggestions worked great on Ubuntu Server 10.04
I'm sorta surprised the ubuntu repositories are so out of date.


Download Rootkit Hunter from [http://rkhunter.sourceforge.net/](http://rkhunter.sourceforge.net/)
```

tar xvfz rkhunter-1.3.8.tar.gz
cd rkhunter-1.3.8/
sudo ./installer.sh --install
...
sudo rkhunter --versioncheck
sudo rkhunter --update --propupd
sudo rkhunter --checkall

```

Its not that theyre out of date...there are recent fixes for recent versions in the repositories.  The thing is that the only way to upgrade to a new version of rkhunter is to download the nexest tarball.  Kind of werid...

---

