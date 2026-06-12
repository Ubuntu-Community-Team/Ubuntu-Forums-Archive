---
title: "Installing Ubuntu 12.04 LTS on VMware will make it a broken package?"
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by abdul_rahman2 on 2013-08-24
Hi Friends am new to ubuntu....so i started to try ubuntu in a VMware(Virtual Machine) before start using it actually...the problem i face is that whenever i use terminal to install something i find myself ending with errors like "am holding broken package" and missing "make" commands....kindly help me....also help me in installing aircrack-ng.

---

### Post by TheFu on 2013-08-24
As a new-to-Linux user, it is best to avoid installing software from outside the Canonical Repository.  That means you should get all the software that you use from either the "Software Center" or Synaptic tools.

Linux doesn't work like Windows. We don't find an "install.zip" file somewhere and install that.  We use the built-in package manager software to locate the software we like ... 22,000+ packages at my last count.  Further, unlike other OSes, when we tell the OS to update for new fixes, it will also update all the applications on the machine which were installed through the package manager too.  No need to hunt down Firefox, Adobe, Microsoft or any 3rd party tools to see if there are any updates or not.  If there are updates, the normal OS update process will get them automagically.

So, in short, 
* don't install from source
* don't install from a .deb file
* avoid installing through a PPA ... unless you completely, 100%, always have and always will, trust the PPA owner.

Feel free to ask any questions or clarify if I completely missed the point of your post.  After all, you didn't include any error messages.

---

