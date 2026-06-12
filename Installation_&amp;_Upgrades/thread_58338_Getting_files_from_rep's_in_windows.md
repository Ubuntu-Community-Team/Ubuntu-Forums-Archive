---
title: "Getting files from rep's in windows"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by dave9191 on 2005-08-19
Hey guys, 

Sorry if this has been asked before, but Ive spent some time looking and I'm running up a bit of a phone bill. 

I've gone away from home for a few weeks (no broadband for a while) and I need to use dial up. But I never got round to trying to get my laptop modem to work. I've found some drivers but to compile them I need the kernel sources (which I could have sworn I had). 

I need to get from the repositories the following files and install them 

linux-headers-2.6.10-5 linux-headers-2.6.10-5-686 linux-headers-686

But how do I download them under windows (only place I can dial up from). Then I can transfer them to linux and install them. Well at least thats the plan :)

Dave

---

### Post by littlepr on 2005-08-19
Insert the Ubuntu 5.04 install cd and then add the cd using the package  manager (synaptic) click on settings--->repositories---->add cd button. Then click ok. Then do a search for linux-headers. Set them all to "Mark For Installation" and then apply.

---

### Post by jasmuz on 2005-08-19
Just go here: [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/)

Select the corresponding deb packages for your system architecture, then copy the corresponding files to /var/cache/apt/archives and run synaptic once again, if not you can just sudo dpkg -i *.deb to install all deb's in that folder.

---

### Post by josepicco on 2005-08-21
Thanks a lot, I had the same problem and it worked OK!!!

---

### Post by dave9191 on 2005-08-22
Hey guys, sry for the late reply. Thanks for the replies. I haven't got the cd with me, but the web link has put me on the right track. Ill just have to search the repositories for the ones that have the files I need. At least i know what category to look under now :) 

Dave

---

