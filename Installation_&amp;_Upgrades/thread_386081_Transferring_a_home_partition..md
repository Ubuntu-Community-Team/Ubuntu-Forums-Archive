---
title: "Transferring a home partition."
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by Nevermore Burning on 2007-03-16
Ok, I have a fairly rubbish lappy on which I'm currently dual-booting That Other OS and Ubuntu 6.10. I am getting soon a bigger hard drvie and more memory for said laptop, as well as a usb caddy for the old laptop. I intend to install Feisty on the new hard drive, when It's out. I intend to create a seperate /home partition during the installation, so i won't lose all my settings when 7.10 comes out. 

My question is this- can i transfer my current /home folder to the partition on the new hard drive, without messing up my installation? I have stuff in it I'd dearly liek to keep,

I've resigned myself to the fact that I'll lost all my had-installed programs, (including wireless drivers, eep!) but that;s the price of upgrading and I want to do a clean install.

So will it be possible?

Corollary question- If I decide to do an upgrade instead of an install, can i transfer the entire current 7.5gb partition to my new 80gb drive and increarse the size of said partition?

Hope that's all clear. bear in mind I'm a bit of a n00b at this, so use short sentences, please. :)

---

### Post by kingcharles1666 on 2007-03-16
yes you can.
Best way is to do a fresh install and during which you create a seperate home partition. You can use the same login details as your old one but make sure you have the same id number!.
Then create a second user with admin rights for failsafe purpose (do not use it to copy the files!).
Now you can copy the entire old home folder content (make sure you include the hidden files)
There may be some discrepancies if you copy the home folder from different releases with regards to icons and that sort of thing but that should not be a show stopper.
If you want to avoid this than upgrade the old drive to feisty first before the copy.
have fun

---

### Post by Nevermore Burning on 2007-03-16
Small question. What is an id number and how do i ensure I keep teh same one?

---

### Post by Nevermore Burning on 2007-03-17
Am i allowed to bump this up? it's falling behind and I just need to knopw what an id numnber is, please..

---

### Post by pejcao on 2007-03-19
> **Nevermore Burning said:**
> Am i allowed to bump this up? it's falling behind and I just need to knopw what an id numnber is, please..

Would be the same one (probably, UR the first user created {during install}). you can issue "echo $UID" or "sudo cat /etc/passwd | grep ~your~user~name" to check it out.

---

