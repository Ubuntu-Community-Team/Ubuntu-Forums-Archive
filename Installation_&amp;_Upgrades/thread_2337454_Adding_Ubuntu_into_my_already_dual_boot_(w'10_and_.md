---
title: "Adding Ubuntu into my already dual boot (w'10 and opensuse tumbleweed)"
date: 2016-09-18
forum: Installation &amp; Upgrades
---

### Post by derkaiserel05 on 2016-09-18
A little backstory :
I have my dualboot computer (windows 10 and opensuse tumbleweed) until  last week, in which, I joined my lecturer's research on NDN (Named-data  Network). Unfortunately, the NDNSim itself, so far have been succesfully  installed only in ubuntu. Also the lecturer advised me to use Ubuntu, to get  rid of any unnecesarry OS-related problem in the future. 

So last night I installed Ubuntu. The problem came when I realized the Ubuntu's grub only detected ubuntu and windows 10. The opensuse is nowhere to be  seen. 

Does anyone ever troubleshoot this kind of problem?? Thank you very much

Does anyone know how to make openSUSE appear again on grub  alongside W'10 and ubuntu?

BTW: most of my work is in opensuse, and I don't want to lose/reinstalled  it.

Thank you.

---

### Post by ajgreeny on 2016-09-18
I do not know OpenSuse, but does it install using LVM?  Or perhaps you chose to install OpenSuse in that manner?

If you did you will need to install the LVM packages or Ubuntu will not be able to read or see the OpenSuse partitions.  I'm not sure which packages are required as I have never used LVM on any OS, but I think lvm2 is one, and possibly the most important of them.

If LVM is not involved I have no idea where to go other than making sure you run command sudo update-grub in Ubuntu to see if that updates the grub menu for you.

---

