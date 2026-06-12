---
title: "'apt-cdom add' broken?"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by darkshvein on 2010-05-16
Run in 10.04:
sudo mount -o loop  mirror-dvd/ubuntu-10.04-2010-05-16-complete-i386-dvd1.iso /cdrom
sudo apt-cdrom add 
&#1055;&#1086;&#1074;&#1090;&#1086;&#1088;&#1080;&#1090;&#1077; &#1101;&#1090;&#1086;&#1090; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1076;&#1083;&#1103; &#1074;&#1089;&#1077;&#1093; &#1080;&#1084;&#1077;&#1102;&#1097;&#1080;&#1093;&#1089;&#1103; CD.
root@ubuntu10:/media# sudo apt-cdrom add -d /cdrom/
No resuilt
root@ubuntu10:/media# cat /etc/apt/sources.list
*empty* !!
cat /etc/apt/sources.list.d/*any*
empty
updated yesterday, i386.

Have any ideas?

---

### Post by mistichu on 2010-05-16
if your root you dont need to use sudo infact sudo will break most commands given as root if not all try doing it without sudo then post results

---

### Post by darkshvein on 2010-05-17
no matter. without sudo (as root) not work too

---

