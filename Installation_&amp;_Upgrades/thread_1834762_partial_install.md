---
title: "partial install"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by ineedanswers on 2011-08-28
i created a live cd on an usb stick using unetbootin and installed ubuntu 11.04 on my netbook as a duel boot and when i went to boot windows xp it did not work so i decided to make my netbook just a ubuntu system so i used the same usb stick to reinstall ubuntu on my entire hd and when i did the installation crashed now i have very limited use of my system i have tried to reinstall it several times and it crashes at the same spot every time i tried to download unetbootin again to recreate a new installation usb and it downloads but i cant run it the software center does not work properly and i tried to get to it by going through synaptic package manager but gives me an error evey time i click on it  i am very new to linux and dont understand command line yet but want to learn that is why i was installing ubuntu in the first place

---

### Post by dino99 on 2011-08-28
standard install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

sudo synaptic

which error did you got ?

---

### Post by ineedanswers on 2011-08-28
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by rajibkudas on 2011-08-28
I tried to install Wine from winehq.org....got following error message when installing 
"W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.2-0ubuntu6~lucid5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.2-0ubuntu6~lucid5_all.deb)
  404  Not Found [IP: 91.189.92.170 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.2-0ubuntu6~lucid5_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.2-0ubuntu6~lucid5_i386.deb)
  404  Not Found [IP: 91.189.92.170 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7~dfsg-1ubuntu3.2_i386.deb)
  404  Not Found [IP: 91.189.92.166 80]

---

