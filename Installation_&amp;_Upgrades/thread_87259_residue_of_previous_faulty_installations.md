---
title: "residue of previous faulty installations?"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by JeeWee on 2005-11-07
I tried installing ubuntu 5.10. SInce I'm Dutch and i got the option to choose for Dutch i did so. Installation failed on with erorr "could not download zlib1g"
Later I learned from somebody that i should install the Englisch version because the Dutch install wouldn't work. (Why give me that choose than?)

But installing in Englisch also doesn't work. Again a report of problems with zlib1g and  additional "unable to install initrd-tools". 

Somebody suggested that the CD was corrupted but i just tried it on an other system and there I didn't experience any problems there so the CD is fine.

Is it possible that somehow a residue of my first attempt is causing problems? How do I get ride of thet eventuall residue?
I deleted the partition and started with FREE SPACE the last few attempts, letting the partinioner create and build a file system on that partiton.

---

### Post by satshen on 2005-11-07
Similar problem here. I tried installing Breezy with English language option & got the following error message "could not download zlib1g". I aborted the installation and tried using an external CD drive - landed up with the same problem. To make sure that the CD was not corrupted I burnt another CD and again tried - but the installation failed with the same error message "could not download zlib1g".

---

### Post by JeeWee on 2005-11-08
I finally installed Ubuntu. I used partition magic to remove the designated partition. Then i did the install again an din partitioner i choose 'use largest continous free space" this time. All went without a hitch this time.

---

### Post by jdong on 2005-11-08
Usually these are problems with the burned medium. Picky CD/DVD drives sometimes will also cause this. Typically trying a new CD or a difference CD-ROM drive works, or just repeatedly trying the procedure hoping for a lucky break :)

---

