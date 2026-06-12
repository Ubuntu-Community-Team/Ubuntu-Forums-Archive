---
title: "Preseeding (Ed)Ubntu10.04"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by mrebholz on 2012-05-17
Hi there, I have successfully built a server to PXE-boot PC clients to install Edubuntu 10.04 over NFS (I used APPEND arguments on the boot line in the DEFAULT menu to mount an nfs exported drive which is the Ubuntu install CD ISO).
 
This all works fine, and the client loads all the way to the desktop and then the tech can double-click 'Install Ubuntu' and away (s)he goes.
 
Now though, I want to PRESEED this so that no questions are asked, and rather than being dumped to the desktop on startup, it just gets on with installing. I have created a PRESEED file, and I can see from the console messages on the client that it gets downloaded and parsed ok. 
 
So why does it dump me to the desktop and ignores all of the commands I've already given it?
 
If anyone knows, I'd be grateful for a response!
 
Many thanks
Mark

---

