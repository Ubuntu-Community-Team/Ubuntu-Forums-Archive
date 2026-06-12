---
title: "Upgrade 8.04  to 10.10"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by wiseguy12851 on 2011-01-12
I am trying to get Ubuntu 8.10 upgraded to Ubuntu 10.10,  I'm having all sorts of errors:

```

No valid mirror found 

While scanning your repository information no mirror entry for the 
upgrade was found. This can happen if you run a internal mirror or if 
the mirror information is out of date. 

Do you want to rewrite your 'sources.list' file anyway? If you choose 
'Yes' here it will update all 'hardy' to 'lucid' entries. 
If you select 'No' the upgrade will cancel. 

Continue [yN] 
```After pressing yes
```

A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade is now aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

Traceback (most recent call last): 

File "/tmp/tmpgKu8J-/lucid", line 7, in <module> 
sys.exit(main()) 

File "/tmp/tmpgKu8J-/DistUpgradeMain.py", line 159, in main 
if app.run(): 

File "/tmp/tmpgKu8J-/DistUpgradeController.py", line 1649, in run 
return self.fullUpgrade() 

File "/tmp/tmpgKu8J-/DistUpgradeController.py", line 1567, in 
fullUpgrade 
if not self.updateSourcesList(): 

File "/tmp/tmpgKu8J-/DistUpgradeController.py", line 686, in 
updateSourcesList 
) % (self.fromDist, self.toDist)) 

File "/tmp/tmpgKu8J-/DistUpgradeViewText.py", line 191, in 
askYesNoQuestion 
res = sys.stdin.readline()A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade is now aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

Traceback (most recent call last): 

File "/tmp/tmpgKu8J-/lucid", line 7, in <module> 
sys.exit(main()) 

File "/tmp/tmpgKu8J-/DistUpgradeMain.py", line 159, in main 
if app.run(): 

File "/tmp/tmpgKu8J-/DistUpgradeController.py", line 1649, in run 
return self.fullUpgrade() 

File "/tmp/tmpgKu8J-/DistUpgradeController.py", line 1567, in 
fullUpgrade 
if not self.updateSourcesList(): 

File "/tmp/tmpgKu8J-/DistUpgradeController.py", line 686, in 
updateSourcesList 
) % (self.fromDist, self.toDist)) 

File "/tmp/tmpgKu8J-/DistUpgradeViewText.py", line 191, in 
askYesNoQuestion 
res = sys.stdin.readline()
```

EDIT:
I'm following the Ubuntu instructions at this link:
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)
The errors above happened after 
**do-release-upgrade**
command was issued

---

### Post by kostkon on 2011-01-12
For EOL upgrades check [this wiki page]("https://help.ubuntu.com/community/EOLUpgrades").

---

### Post by Quackers on 2011-01-12
That's a lot of versions to upgrade! It would be a lot quicker to clean install a newer version (and probably safer!)

---

### Post by wiseguy12851 on 2011-01-12
Unfortunately I am forced to upgrade this, I purchased a dedicated server from godaddy expecting the latest Ubuntu OS and instead I get Ubuntu 8.04 LTS - The support team said it's my server so they provide no support whatsoever.

I allowed to do whatever I want with it but I'm on my own. I'm fine with that but I can't do anything until it's upgraded and I don't have access to the actual keyboard, only remotely. That means I can't format it since I would have no way to access it for installation.

Is there any way I can trick Ubuntu into doing an auto-mount for a CD-ISO image and performing the installation via RDP or SSH. From what I've learned with Linux, everything possible.

---

### Post by wiseguy12851 on 2011-01-12
That messed it up so I'm reverting it back to original installation, I'm going to try a different approach - 


[LIST]
[*]Keep 8.04
[*]Install the desktop version
[*]Connect via RDP
[*]Try to upgrade using a visual interface that does auto error checking
[/LIST]

---

