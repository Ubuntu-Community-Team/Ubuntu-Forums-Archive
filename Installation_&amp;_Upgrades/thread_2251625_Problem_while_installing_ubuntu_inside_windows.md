---
title: "Problem while installing ubuntu inside windows"
date: 2014-11-05
forum: Installation &amp; Upgrades
---

### Post by tarek5 on 2014-11-05
hey all i downloaded ubuntu 14.10xi386 when i extracted the iso file and press on wubi.exe i put the size and language then i press "install" then i found it say "downloading" ubuntu 14.10 amd64.iso.torrent  , idk why its downloading the 64 not the i386 i have and also when it finished it gave me an error i don't remember what it was so what is the problem?

---

### Post by Mark Phelps on 2014-11-05
You should  NOT be installing using WUBI anymore.  WUBI support was dropped when it was discovered to be incompatible with Windows 8 in UEFI mode.

You should consider installing to its own partition, instead.

---

### Post by tarek5 on 2014-11-05
i am using windows 7 , so how can i setup ubuntu inside windows?

---

### Post by tarek5 on 2014-11-05
> **Mark Phelps said:**
> You should  NOT be installing using WUBI anymore.  WUBI support was dropped when it was discovered to be incompatible with Windows 8 in UEFI mode.

You should consider installing to its own partition, instead.

i am using windows 7 , so how can i setup ubuntu inside windows?

---

### Post by yancek on 2014-11-05
If you really want to install using wubi, then use the wubi guide at the link below but remember it is not supported any longer.

[URL="https://wiki.ubuntu.com/WubiGuide"]https://wiki.ubuntu.com/WubiGuide

[/URL]You would be better off installing Ubuntu to its own partition.  If you don't want to do that, install VirtualBox on windows 7 and install Ubuntu that way.

---

### Post by hakuna_matata on 2014-11-05
I don't recommend Wubi, too. But I try to answer your questions:
> why its downloading the 64 not the i386 i have
This is not a bug, it is a feature of Wubi. It downloads 64 bit version because your computer supports 64 bit version: [Can I force Wubi to download and install a 32 bit version of Ubuntu]("https://wiki.ubuntu.com/WubiGuide#Can_I_force_Wubi_to_download_and_install_a_32_bit_version_of_Ubuntu.3F") 
> when it finished it gave me an error i don't remember what it was so what is the problem?
I assume, it is bug [1385930]("https://bugs.launchpad.net/wubi/+bug/1385930").
> i am using windows 7 , so how can i setup ubuntu inside windows?
You can find a good summary of recent Wubi issues and workarounds [here]("http://ubuntu-with-wubi.blogspot.ca/"). For testing purpose I use an unofficial version of Wubi (wubi1410.exe) with all fixes and workarounds which I know. This version is  [here]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na").

But IMHO the best solution would be to install Ubuntu to its own partitions.

---

