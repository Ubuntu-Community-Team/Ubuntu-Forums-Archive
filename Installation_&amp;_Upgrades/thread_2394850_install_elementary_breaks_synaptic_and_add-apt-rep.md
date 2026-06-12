---
title: "install elementary breaks synaptic and add-apt-repository"
date: 2018-06-22
forum: Installation &amp; Upgrades
---

### Post by Mattias on 2018-06-22
Hello
On some stupid whim I installed Elementary on my working 18.04 distribution and apparently it wrecks havoc with synaptic and add-apt-repository. Tried to remove it but no luck. when trying to run add-apt-repository i get :
 File "/usr/bin/add-apt-repository", line 107, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 128, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 623, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 93, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for elementary/juno
lsb-a gives:
No LSB modules are available.
Distributor ID:	elementary
Description:	elementary OS 5.0 Juno
Release:	5.0
If i manually try to edit sources in synaptic it keeps telling me that repositories changed every time i try

Anyone have a clue where and how to get lsb to revert to Bionic ?

---

### Post by deadflowr on 2018-06-22
Can you install ppa-purge?
(Or install anything?)
From a terminal run
```
sudo apt install ppa-purge
```
then try running it against the elementary ppa(?)
(I'm guessing you added the elementary ppa, or one of them at least.)
ppa-purge removes the repository and then downgrades all affected packages back to the Ubuntu versions.
more (or less): [https://askubuntu.com/questions/307/how-can-ppas-be-removed]("https://askubuntu.com/questions/307/how-can-ppas-be-removed")

If installing anything doesn't work, then it might be best to backup and reinstall clean.

---

### Post by Mattias on 2018-06-23
Hello 
Thank you for the useful tips. It worked. I will now add ppa-purge to my list of useful command line tools
Thanks

---

