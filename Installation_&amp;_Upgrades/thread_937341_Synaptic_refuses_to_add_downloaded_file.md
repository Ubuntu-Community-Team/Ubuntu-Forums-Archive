---
title: "Synaptic refuses to add downloaded file"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by mringer on 2008-10-03
X-UB 8.04, 


When running synaptic pack-man one can in theory download a package & install it in 2 steps by

file > generate download script

and

file > add downloaded packages

The first worked, the 2nd failed. I can open the directory with the 
downloaded  .deb  files, but these are greyed out and I cannot select 
them. Please what should I do? thank you.

Background: some people have been having difficulty with the upgrade to
wicd 1.5.3. If the upgrade fails, one could be left without a workable network, so it seems sensible to download the old version beforehand.

---

### Post by Partyboi2 on 2008-10-04
For the 2nd stage (add downloaded packages) open up synaptic and then search for all the packages you have just downloaded using the script and after selecting them all go "file>Add downloaded packages" then navigate to where the packages you downloaded with the script are. They will all be greyed out, just press the open button and they should start to install. If you still have no joy then open a terminal and cd (change directory) into the folder that has the downloaded packages and install them with
```
sudo dpkg -i package
``` change package to actual name of package you are wanting to install.

---

