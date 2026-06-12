---
title: "Upgrading to 10.10: &quot;AttributeError: 'Template' object has no attribute 'official'&quot;"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by gardara on 2010-10-12
When I try to upgrade from 10.04 to 10.10 I get this:

```

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

File "/tmp/tmpoIug3Y/maverick", line 7, in <module> 
sys.exit(main()) 

File "/tmp/tmpoIug3Y/DistUpgradeMain.py", line 158, in main 
if app.run(): 

File "/tmp/tmpoIug3Y/DistUpgradeController.py", line 1616, in run 
return self.fullUpgrade() 

File "/tmp/tmpoIug3Y/DistUpgradeController.py", line 1534, in 
fullUpgrade 
if not self.updateSourcesList(): 

File "/tmp/tmpoIug3Y/DistUpgradeController.py", line 664, in 
updateSourcesList 
if not self.rewriteSourcesList(mirror_check=True): 

File "/tmp/tmpoIug3Y/DistUpgradeController.py", line 486, in 
rewriteSourcesList 
distro.get_sources(self.sources) 

File "/tmp/tmpoIug3Y/distro.py", line 103, in get_sources 
source.template.official == True and 

AttributeError: 'Template' object has no attribute 'official' 


```

Been trying to google but I haven't found any solutions.


Any ideas?:)

---

### Post by gardara on 2010-10-13
Anyone?:)

---

### Post by Noo 2 Ubuntoo on 2010-10-13
I got something similar to this when doing a fresh install of Lucid which I didn't and still don't understand. I just did another fresh install from the same disk and it went fine.

What I'm really saying is you might want to try doing a fresh install as a workaround to upgrading via update manager.

---

### Post by gardara on 2010-10-16
Just installed some updates today (didn't pay attention to what updates they were) but after that the error disappeared so I was able to successfully upgrade to 10.10 :)

---

### Post by meanderingthoughts2 on 2010-11-05
I'm a newbie here to who ran into the same problem. I figured my way out of it and I can give you the "how-to", but not the "why?". 

system>administration.>software sources
Under "Ubunutu Software" tab, check the box: Cannocial-supported Open Source software (main)

A popup should come up telling you may need to reinstall software, but if you have recently done an update (which you probably had when trying to first upgrade), then never mind this message.

Go to system>admin>update manager and try to upgrade again. 

If this doesn't work go back to to Software Sources and also check the box: Community-maintained Open Source software (I can't remember if I checked this or not, that is why I'm suggesting try this if the upgrade doesn't work)

Hope this helps!

-meanderingthoughts2

---

### Post by mastapat11 on 2011-10-31
> **meanderingthoughts2 said:**
> I'm a newbie here to who ran into the same problem. I figured my way out of it and I can give you the "how-to", but not the "why?". 

system>administration.>software sources
Under "Ubunutu Software" tab, check the box: Cannocial-supported Open Source software (main)

A popup should come up telling you may need to reinstall software, but if you have recently done an update (which you probably had when trying to first upgrade), then never mind this message.

Go to system>admin>update manager and try to upgrade again. 

If this doesn't work go back to to Software Sources and also check the box: Community-maintained Open Source software (I can't remember if I checked this or not, that is why I'm suggesting try this if the upgrade doesn't work)

Hope this helps!

-meanderingthoughts2


Thanks for this!  it got me down the right path to my natty --> oneiric upgrade.  i had to do some other steps and a partial up, but eventually got to a full 11.10 working system :)

---

