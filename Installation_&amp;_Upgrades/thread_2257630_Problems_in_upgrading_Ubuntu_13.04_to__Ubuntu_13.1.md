---
title: "Problems in upgrading Ubuntu 13.04 to  Ubuntu 13.10"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by Zombir on 2014-12-21
Dear all, 
I've been using Ubuntu 13.04 for a while now. Due to internet connectivity problems I couldn't update my OS but now I want to do it. Since I cannot directly go to 14.04, I downloaded an ISO of Ubuntu 13.10, created a bootable USB stick using Unetbootin and booted my computer with it. 

Much to my disappointment, the Upgrade option is not available and is grayed out. 
I really cannot afford erase the old operating system and install the new one since I don't have enough space to backup my whole hard-drive. 
I'm running one more operating system in addition to Ubuntu 13.04. I've been searching in the internet for a reason but couldn't find a solution yet.

The ISO I've been using is named ubuntu-13.10-desktop-amd64.iso
The following describes my current system:

```
virat@virat-Inspiron-N5110:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
virat@virat-Inspiron-N5110:~$ uname -a
Linux virat-Inspiron-N5110 3.8.0-35-generic #50-Ubuntu SMP Tue Dec 3 01:24:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```


Please help. 

Thanks in advance.

---

### Post by sudodus on 2014-12-21
> **Zombir said:**
> Dear all, 
I've been using Ubuntu 13.04 for a while now. Due to internet connectivity problems I couldn't update my OS but now I want to do it. Since I cannot directly go to 14.04, I downloaded an ISO of Ubuntu 13.10, created a bootable USB stick using Unetbootin and booted my computer with it. 

Much to my disappointment, the Upgrade option is not available and is grayed out.

Unfortunately both 13.04 and 13.10 have passed end of life. It might be possible (but is complicated) to follow the upgrade path, and I discourage doing it. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]
> 
I really cannot afford erase the old operating system and install the new one since I don't have enough space to backup my whole hard-drive. 


Upgrading to a new version is risky, and you should not do it without a ***current backup*** of at least your personal files (documents, pictures ...). So I recommend strongly, that you wait until you can get an external drive or space in the internet cloud, where you can store the backup.

-o-

And when your data are backed up, you might as well do a fresh installation of Ubuntu 14.04.1 LTS, and then copy back your personal data. It is much easier, still risky, but much safer that an upgrade from 13.04, and above all, much faster.

A method between those methods is to keep your /home directory, copy it to a separate home partition, make a fresh installation, where you select ***Something else*** at the partitioning window, select the home partition and ***do not format*** it. That might work well, but some old settings might create problems and need tweaking. You still need the backup for this method.

---

