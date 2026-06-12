---
title: "dist-upgrade halted"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by dannytherocker on 2010-12-22
Hi,

some days ago, I tried to upgrade from Lucid to Maverick but had to stop it for many reasons (thought no space enough on hd). Now, as I type sudo do-release-upgrade -d, I get the following:
```
Traceback (most recent call last): 

File "/tmp/tmpQZrWQy/maverick", line 7, in <module> 
sys.exit(main()) 

File "/tmp/tmpQZrWQy/DistUpgradeMain.py", line 158, in main 
if app.run(): 

File "/tmp/tmpQZrWQy/DistUpgradeController.py", line 1616, in run 
return self.fullUpgrade() 

File "/tmp/tmpQZrWQy/DistUpgradeController.py", line 1534, in 
fullUpgrade 
if not self.updateSourcesList(): 

File "/tmp/tmpQZrWQy/DistUpgradeController.py", line 664, in 
updateSourcesList 
if not self.rewriteSourcesList(mirror_check=True): 

File "/tmp/tmpQZrWQy/DistUpgradeController.py", line 486, in 
rewriteSourcesList 
distro.get_sources(self.sources) 

File "/tmp/tmpQZrWQy/distro.py", line 103, in get_sources 
source.template.official == True and 

AttributeError: 'Template' object has no attribute 'official' 

```
How can I fix it?
Thanks

---

### Post by dino99 on 2010-12-22
how are you doing this upgrade: with chroot ? or your system work 24/24 ?

you might need to clean the cache:

sudo rm /var/cache/apt/archives/*

---

### Post by dannytherocker on 2010-12-22
> **dino99 said:**
> how are you doing this upgrade: with chroot ? or your system work 24/24 ?

you might need to clean the cache:

sudo rm /var/cache/apt/archives/*

it was done via "upgrade-manager -d". I chose command line only after.

---

