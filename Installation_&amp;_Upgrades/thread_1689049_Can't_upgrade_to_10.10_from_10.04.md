---
title: "Can't upgrade to 10.10 from 10.04"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by red33m on 2011-02-16
I can't upgrade to 10.10 

I knew for a long time now that my Ubuntu are in trouble but as long as Firefox was OK I didn't care.

Though now that I want to upgrade nothing seems to work..I typed Alt+F2 then update-manager and the window came up..I installed all the updates and then I clicked check again but it can't find the update. I tried doing the job through the terminal and the terminal won't open..


Please help quickly..I have no time in my hands right now and I need to upgrade!!

---

### Post by red33m on 2011-02-16
What is wrong with my Ubuntu?

red33m@red33m-laptop:~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'maverick.tar.gz'
authenticate 'maverick.tar.gz' against 'maverick.tar.gz.gpg' 
tar: Removing leading `/' from member names

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
WARNING: Failed to read mirror file

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

[100%] 1031kB/s 0s 
Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done

---

### Post by red33m on 2011-02-16
Please help I did install a pre-release version of 10.04 LTS.

What is there left for me to do?

---

### Post by Swagman on 2011-02-16
Go into system/administration - update manager

click on settings - updates tab and select normal releases instead of **L**ong **T**erm **R**eleases only

---

### Post by arubislander on 2011-02-16
> **red33m said:**
> Please help quickly..I have no time in my hands right now and I need to upgrade!!

It is never a good idea to upgrade if you have no time in your hands... You should always set apart sufficient time for that as there are any number of things that might (but more often than not don't) go wrong...

---

