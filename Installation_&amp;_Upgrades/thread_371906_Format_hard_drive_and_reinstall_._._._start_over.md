---
title: "Format hard drive and reinstall . . . start over"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by Statik on 2007-02-27
so, I've been banging my head off several little problems with Ubuntu, starting with my Hoary install. I've upgraded and upgraded, tweaked and fiddled. I'm now in Edgy, 6.10. Still there are little problems. I'm wondering if its just better to backup my home folder, erase the HD and reinstall Edgy from scratch.

If so, will backing up my home directory keep evolution and palm pilot settings? Firefox bookmarks and login cookies? 

If I do this, what's the best way to get back my functionality? Blender, Gimp, I'd like Cinelerra, LMMS, Flash with sound in Firefox, K9Copy with CSS decode. Easy Ubuntu? Automatix?

Statik

---

### Post by navilon on 2007-02-27
Yes, your home folder will contain virtually all your configuration files and settigns

---

### Post by bulldog on 2007-02-27
Try this script,I picked up from a fellow user.[don't recall his name,sorry]
It makes a list of all programs currently installed.
You can import it again and your new install will have the same programs as you had before.

**************************************************************************************
To install all your application on your new install try this.
dpkg --get-selections > mypackages 
#writes all installed packages to "mypackages"
# save "mypackages" on a USB stick, copy it to a fresh install
cat mypackages | sudo dpkg --set-selections 
#selects all packages from "mypackages"
sudo apt-get dselect-upgrade #installs them
**************************************************************************************
It provides you with a list which you have to import in your new install.

---

