---
title: "trying to update from 10.04 to 10.10-ran into an issue"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by ganeshsugunan on 2011-05-18
so I'm updating from 10.04 to 10.10, and the gui gets all the way to fetching is complete, and then it just hangs; roughly 5-10 mins later, the update process just dies, with no error report; I do get an error when I do sudo do-release-upgrade; but I can't quite remember it off the top of my head, updates on that error message will follow. Also, the end goal is to get to 11, so if anyone knows of a way to skip 10.10 altogether, that would be nice.

---

### Post by mörgæs on 2011-05-18
If you want to upgrade, one has to install all versions in the path. There is no option of skipping one. 

As you have experienced, an upgrade is a risky process. I would recommend testing 11.04 in a live boot and after that a clean install, if the live boot works well.

---

### Post by ganeshsugunan on 2011-05-18
so the error is:

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


A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

Traceback (most recent call last): 

File "/tmp/tmpsh2JEH/maverick", line 7, in <module> 
sys.exit(main()) 

File "/tmp/tmpsh2JEH/DistUpgradeMain.py", line 158, in main 
if app.run(): 

File "/tmp/tmpsh2JEH/DistUpgradeController.py", line 1616, in run 
return self.fullUpgrade() 

File "/tmp/tmpsh2JEH/DistUpgradeController.py", line 1534, in 
fullUpgrade 
if not self.updateSourcesList(): 

File "/tmp/tmpsh2JEH/DistUpgradeController.py", line 664, in 
updateSourcesList 
if not self.rewriteSourcesList(mirror_check=True): 

File "/tmp/tmpsh2JEH/DistUpgradeController.py", line 486, in 
rewriteSourcesList 
distro.get_sources(self.sources) 

File "/tmp/tmpsh2JEH/distro.py", line 103, in get_sources 
source.template.official == True and 

AttributeError: 'Template' object has no attribute 'official'

---

### Post by ganeshsugunan on 2011-05-19
I'm attaching the log files; and responding to the second poster: i've tried the live cd for 11.4, while I don't like the new desktop env, that's easy enough to swap out, but I don't want to have to go through a full reinstall on my machine in order to upgrade; at least as long as 10.04 is supported.

---

