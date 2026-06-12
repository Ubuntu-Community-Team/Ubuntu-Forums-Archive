---
title: "commit error upgrading 8.04 to 11.04"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by sangline on 2011-05-16
Tried upgrading from 8.04 to 11.04. Got message saying "error during commit. couldn't configure pre-depend for openoffice.org writer2latex(?) probably a dependency cycle". I don't have clue what this message means. Any help on I might correct the problem so I might successfully upgrade would be greatly appreciated!

---

### Post by zvacet on 2011-05-16
You tried to skip versions,that what I think that message mean.You can upgrade from 8.04>10.04 directly because both releases are LTS,but after that you have to upgrade **10.4>10.10>11.04**.Otheer option is to  back up all your data and do fresh install of Natty.

---

### Post by sangline on 2011-05-16
Thank you for the response. My sytem's automatic updates default was setup to notify me daily of only LTS updates, so I suspect that was why I skipped  the non-LTS updates. *I can't upgrade to 10.4 because of the commit error regarding openoffice*. Would it be wise to uninstall openoffice to see if 10.04 will install w/o errors or would it be just better to  install 11.04? If I do the latter what data has to be backed up, is it just my personal data files or are there system files that contain info like  remembered passwords, adm password, etc.?
  Used Synaptic Package Mgr to remove OpenOffice "writer2latex" and 10.4 installed w/o errors.:)

---

### Post by tritri on 2011-05-31
Im having a similar issue... but im on 8.10 and when i try to update through the built in Update Manager, it says 9.04 is no longer supported, 10.xx doesnt even show up, ive tired downloading 9.04, 10.04, and 11.04, and tried booting from a CD and booting from a flash drive. Any easy way around this?

---

### Post by mörgæs on 2011-05-31
> **tritri said:**
> ...and tried booting from a CD and booting from a flash drive. Any easy way around this?

What is the problem when booting?

---

### Post by tritri on 2011-06-01
Well i have a CD with 10.10 (might be 11.04 ill check) burned onto it, im currently running 8.04, when i tried to update through the update manager it couldnt find the files... then i boot off the CD it will load up, then it will jumble a bunch of code on my screen. eventually it ends and says the CD couldn't mount.

---

### Post by mörgæs on 2011-06-01
10.10 and 11.04 will both be all right. 

There can be several reasons for your computer not booting from the CD. First of all, how much memory does it have?

What exactly does the error message say? 

Have you done the MD5 test? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by tritri on 2011-06-01
well i have a brand new 360 GB hard drive installed, and i have 2GB of RAM and the CD was a 1GB CD.  ill post exactly what it says later when i can get on the computer i'm working on

---

