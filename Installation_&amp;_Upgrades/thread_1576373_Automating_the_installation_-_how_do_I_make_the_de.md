---
title: "Automating the installation - how do I make the debian installer start automatically?"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by grayFalcon on 2010-09-17
Hello folks,

I have been trying for quite a while now to get an automated installation running based off the ubuntu desktop live CD. I have worked my way through preseeding and generated a .seed file which should do what I need. Now the problem is that I can't get the installer to start - I have not been able to find any documentation on what I have to put into isolinux.cfg to make that happen. Whatever I try (I currently have "append preseed/file=... debian-installer/locale=en_US console-setup/layoutcode=us auto DEBIAN_FRONTEND=text boot=casper initrd=casper/initrd.lz quiet"), it always boots up into the live cd X session, or, if I do only-ubiquity, into the GUI installer (which is not what I want, since I cannot automate that using a preseed file). Is there some kind of option analogous to only-ubiquity to automatically only start the debian installer? 

Thanks a lot in advance!

Edit: No idea how to set the thread tag as solved, but here is the solution: Just use the alternate installer CD ;)

---

