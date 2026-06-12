---
title: "problem with language support"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by ahmedhamdy27 on 2008-07-23
while i'm trying to install arabic language support on ububtu 7.10  it stopped at the following output and took alot of time 
> 
Setting up language-support-ar (1:7.04+20070309) ...
Generating locales...
  ar_AE.UTF-8... 



i restarted the computer and after restart  when i try to open synaptic or update manager it gives me this error

> 
Only one software management tool is allowed to run at the same time

Please close the other application e.g. "Update Manager", "aptitude" or "Synaptic" at first.


what should i do , now o cant install any package or update :S:S

---

### Post by ahmedhamdy27 on 2008-07-23
fixed 

i tried the following command 

 sudo dpkg -r -a

i can start update manager or synaptic but when i tried to add the arabic support again it stopped at the same area . what should i do

---

