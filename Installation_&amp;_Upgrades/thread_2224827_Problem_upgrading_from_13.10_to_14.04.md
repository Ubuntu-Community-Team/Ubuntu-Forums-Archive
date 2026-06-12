---
title: "Problem upgrading from 13.10 to 14.04"
date: 2014-05-18
forum: Installation &amp; Upgrades
---

### Post by jorritTyb on 2014-05-18
I have a problem upgrading from 13.10 to 14.04. When the upgrade starts it ends with an error saying that it 'Could not calculate the upgrade'. I checked /var/log/dist-upgrade/main.log and the only error that I could find there is the following:

> 
2014-05-18 16:42:09,332 DEBUG blacklist expr 'ubuntu-release-upgrader' matches 'ubuntu-release-upgrader-gtk'
2014-05-18 16:42:09,332 DEBUG The package 'ubuntu-release-upgrader-gtk' is marked for removal but it's in the removal blacklist
2014-05-18 16:43:38,881 ERROR Dist-upgrade failed: 'The package 'ubuntu-release-upgrader-gtk' is marked for removal but it is in the removal blacklist.'


I have no clue how to solve that. Any tips for me?

---

### Post by kowloon2 on 2014-05-19
I have similar problem before due to obsolete packages.
This commands works for me "sudo apt-get autoremove", after all were removed, click the "Software Updater" icon.

---

### Post by jorritTyb on 2014-05-19
No I had already done that. A lot of packages were removed in my case but it doesn't solve the issue I'm afraid.

---

### Post by jorritTyb on 2014-05-26
Sorry for reviving this thread but I still have not found a solution for this. Perhaps I'm not asking the right place? Is there some place where I can get better help about this issue?

Thanks!

---

### Post by mastablasta on 2014-05-26
how are you doing the upgrade ? via CLI or upgrade manager? i am asking becuase i just got dupped by the manager on one of the mashcines... i solved it all by recovery and then manual upgrade so i could boot into the desktop where **update** manager did the rest.

---

### Post by jorritTyb on 2014-05-26
Well when I start up my system I get a dialog which tells me that there is an update and this error I get when I press the upgrade now button (or something like that).

---

