---
title: "Removing Bad Archive"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by drwho200 on 2007-09-23
I wanted to install Virtual Box so I downloaded the .deb and double clicked I couldn't install it as I couldn't accept the user license, as I didn't know what to press I had to click the X button and quit.

However I cannot install anything now it comes up with 
```
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
```


What do I do?

---

### Post by jamvegan on 2007-09-25
You could try installing the package again from a terminal, and maybe then you'll be able to accept the license?  Open a terminal (Applications->Accessories->Terminal), then navigate to the directory which contains the .deb file.  If it's on your desktop, for instance:
```
cd ~/Desktop
```
Then type the following command:
```
sudo dpkg -i package_file.deb
```
(where you replace "package_file.deb" with the actual name of the file, of course).

Even if you've decided that you don't want the package anymore, it's best to try to get it properly installed in order to be able to cleanly remove it.

---

