---
title: "Boot-repair is no longer available for download?"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2014-11-23
I am using Xubuntu 14.04 and tried to download and install boot-repair, but it is no longer seems to be available? The PPA is accepted but it doesn't find the sofftware. It is not available from any website, Synaptic or the Ubuntu software center.

```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)

```

---

### Post by ajgreeny on 2014-11-23
Have you checked that the sed command worked properly and that you sources.list.d file is actually edited as needed?

---

### Post by oldfred on 2014-11-23
A couple of hours ago Yann released current ppa for Boot-Repair.
Do not run the rename to saucy line as that is not a current version.

Updated instructions now here without extra line:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
 [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair/+packages)
Precise, Trusty, Vivid, & Utopic all should work now

---

### Post by ineuw on 2014-11-23
Many thanks for all your help. The new link to yann's boot-repair ppa and install works fine. But, I lost the Canonical ppa's. I can reinstall the peripheral ppa's like menulibre, officelibre, and bleachbit, but the rest is missing because I was messing with it, trying to eliminate the duplicate sources reported by apt-get update. How can I restore the Canonical ppa's?
I tried suggestions in other posts with similar problems but it didn't help. How can I stall clean and fresh to rebuild the sources?

---

### Post by oldfred on 2014-11-24
If you removed the ppa, then you have to reinstall just like you did originally.
But if an upgrade there may not be new versions  or versions that work well until creator of ppa updates. 
Boot-Repair just now updated, and was a bit late. Some others may never update as they have too many compatibility issues.

---

### Post by ineuw on 2014-11-24
The originals were installed by the software installation process. However I just found an excellent source at [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/).

---

