---
title: "Upgrade from 9.10 to 10.04 and installed softwares"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by praveensripati on 2010-04-16
Hi,

I am planning to upgrade from 9.10 to 10.04.

Dropbox and some other softwares are not there in the Ubuntu default repository. So, I have included the following in the sources and installed DropBox.

deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) karmic main
deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) karmic main

After the upgradation from 9.10 to 10.04 will the softwares like DropBox work? I don't see a DropBox release for 10.04 yet. I wan't to make sure that the additional installed softwares work in 10.04. Is it advised to postpone the upgrade till the necessary softwares are available for 10.04? Also, do I need to updated the sources like the above after the upgrade from Karmic to Lucid?

Thanks,
Praveen

---

### Post by brucewagner on 2010-04-16
Yes DropBox for 9.10 seems to work fine on 10.04

I just installed it today. 

Personally I recommend that you NOT "upgrade"... but instead,  do a fresh new clean install of 10.04

I did today, and I installed Dropbox by adding that repository to my Software Sources, then installing it in Synaptic.... it works great.

---

