---
title: "HELP!! New Ubuntu 8.10 install, Keyboard Layout is messed up"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by fasteddyktm on 2008-11-07
Ive just just finished an install of Ubuntu 8.10 on a Dell Inspiron 600m, the keyboard is mixed up (no apostraphe, forward slash can be found at shift three, no àt`sign) etc. also at times when typing the text will start to show up way back in the text Ive already typed!! No fun to say the least. Heres what Ive done so far. Ubuntu is running as a guest using Virtual Box on an XP sp2 host. Ive installed the guest additions and have updated and upgraded everything, I ran through this list to make sure.

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
sudo reboot

Once I completed that I went into System-Preferences-Keyboard and tried all the settings there to no avail., I dont think this is machine related as Ive done the same install on my desktop and have the same problem I really would like to make this work. Any help or insight will be greatly appreciated.

Ed....

---

