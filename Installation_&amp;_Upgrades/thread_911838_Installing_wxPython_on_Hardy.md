---
title: "Installing wxPython on Hardy"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by indira_tung on 2008-09-06
hi,
for some reason, I can only install deb packages by downloading the files 1 by 1 from web. although the dependency issue was very troublesome, usually this could be settled by patience.
however, I found something strange that made me stuck installing wxPython.
the package python-wxgtk required package python-wxversion, but at the same time python-wxversion also required python-wxgtk to be installed first.
I believe I am not the only one experienced this, therefore, pls share any idea that can make me proceed with the installation.
thx&rgds,
indy

---

### Post by Partyboi2 on 2008-09-06
Have you tried installing the version that is in the ubuntu repository? This should then take care of any dependencies and save you time.
You can install it by opening up Synaptic Package Manager (System>Admin>Synaptic Package Manager) and searching for python-wxgtk or opening a terminal and typing
```
sudo apt-get install python-wxgtk2.8
```

---

### Post by indira_tung on 2008-09-08
hello partyboi2,
thanks for your advice.
unfortunately, at the moment I do not own the repository CD and our proxy server does not allow me to update the package automatically.
btw, can we make a dummy repo cd by writing the deb files we downloaded into a CDRW? sorry for this silly question.
thx&rgds,
indy

---

### Post by Partyboi2 on 2008-09-08
> btw, can we make a dummy repo cd by writing the deb files we downloaded into a CDRW? sorry for this silly 
You could use something like [[COLOR=Blue]aptoncd [/COLOR]]("http://ubuntuforums.org/btw,%20can%20we%20make%20a%20dummy%20repo%20cd%20by%20writing%20the%20deb%20files%20we%20downloaded%20into%20a%20CDRW?%20sorry%20for%20this%20silly")

---

### Post by indira_tung on 2008-09-09
@ Partyboi2,

Thanks for the good advice. AptonCD works flawlessly to install the packages.
I believe this application can help a lot of people with limited internet access.

Best regards,
Indy

---

