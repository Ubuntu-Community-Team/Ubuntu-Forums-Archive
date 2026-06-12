---
title: "ubuntu 14-04 x-unikey needs to be reinstalled"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by le_quang_toai on 2014-07-20
Dear all,

I've tried to install the x-unikey to type in vietnamese. However, the installation seems to to work. moreover, my software center cannot open now. And there is an error, which says that E: the package x-unikey needs to be reinstalled, but I can't find an archive for it. 

Do you think what I should do now? I've already tried with terminals to use this command, but not work. What next?
sudo dpkg --remove --force-remove-reinstreq x-unikey

Thanks.

---

### Post by ibjsb4 on 2014-07-20
Please give us a link to the download.

---

### Post by le_quang_toai on 2014-07-21
Sorry, I've checked my history in firefox but cannot figured out where I downloaded the x-unikey file. But the file name is x-unikey_1.0.4-5_i386.deb. If you want, I could send it to you.

---

### Post by le_quang_toai on 2014-07-21
dear all,

in the end I figured out how to solve it after trying with different methods. 
[http://askubuntu.com/questions/122699/how-to-remove-package-in-bad-state-software-center-freezes-no-synaptic](http://askubuntu.com/questions/122699/how-to-remove-package-in-bad-state-software-center-freezes-no-synaptic)

so basically, I need to delete any information about the bad package from /var/lib/dpkg/status then get it update. now software center works normally.

Thanks a lot for your support anyway.

---

