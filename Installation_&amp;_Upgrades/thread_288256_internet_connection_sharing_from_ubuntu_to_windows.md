---
title: "internet connection sharing from ubuntu to windows"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by shashi123 on 2006-10-29
hi

i have installed a ubuntu 6.06 lts as a server

i am able to surf the net also i am able to see and access the windows client now i want to use ubuntu as a mail server and internet server

but i am not ablt to give internet access to windows 98 machines through ubuntu server

i tried apt-get install firestarter but it says its not available

can u plz help me
Forward Message

---

### Post by jd65pl on 2006-10-29
Firestarter is a firewall graphical interface which is used to configure the firewall iptables which is installed as default.
I think you may want to configure your ubuntu machine as a DHCP server to enable internet connection sharing.

Here is a similar post to resolve this issue [http://ubuntuforums.org/archive/index.php/t-18733.html](http://ubuntuforums.org/archive/index.php/t-18733.html)

You might want to have a look at this page for your email server [http://ubuntuforums.org/showthread.php?t=40047](http://ubuntuforums.org/showthread.php?t=40047)

---

