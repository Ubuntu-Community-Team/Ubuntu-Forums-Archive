---
title: "Can't upgrade to 14.04, wants me to uninstall &quot;ubuntu-release-upgrader-core&quot;"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by jstar10 on 2014-05-07
I currently have 13.10, and I get this error when trying to run do-release-update:

> Calculating the changes


Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


When viewing /var/log/dist-upgrade/main.log, I see this error:

> 
2014-05-07 11:56:54,263 DEBUG blacklist expr 'ubuntu-release-upgrader' matches 'ubuntu-release-upgrader-core'
2014-05-07 11:56:54,263 DEBUG The package 'ubuntu-release-upgrader-core' is marked for removal but it's in the removal blacklist
2014-05-07 11:56:54,282 ERROR Dist-upgrade failed: 'The package 'ubuntu-release-upgrader-core' is marked for removal but it is in the removal blacklist.'
2014-05-07 11:56:54,282 DEBUG abort called
2014-05-07 11:56:54,284 DEBUG openCache()
2014-05-07 11:56:54,284 DEBUG failed to SystemUnLock() (E:Not locked) 
2014-05-07 11:56:56,327 DEBUG /openCache(), new cache size 66182
2014-05-07 11:56:56,327 DEBUG enabling apt cron job


I've looked for a solution to this problem, which is usually "just remove the offending package"... but I can't remove ubuntu-release-upgrader-core, because then I can't run the upgrade!

Any help will be appreciated...

---

### Post by ubfan1 on 2014-05-07
Try running just update the 13.10 system first, then try the upgrade to 14.04.

---

### Post by jstar10 on 2014-05-07
> **ubfan1 said:**
> Try running just update the 13.10 system first, then try the upgrade to 14.04.

Thanks for the response, but that didn't work. I've tried "sudo apt-get upgrade" and "sudo apt-get dist-upgrade", installed all updates, and I still get the same do-release-upgrade error.

---

### Post by ubfan1 on 2014-05-07
Try sudo apt-get update
to bring the 13.10 system up to date first.

---

