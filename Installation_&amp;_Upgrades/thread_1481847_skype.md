---
title: "skype"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by varun30 on 2010-05-13
hello.
im trying to install skype , but to no avail, this is what it says after trying to install. im not very good at this, so any help will be appreciated.




varun@the-observor:~$ wget -O skype-ubuntu-current_i386.deb [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
--2010-05-13 14:57:32--  [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
Resolving [www.skype.com]("http://www.skype.com")... 78.141.177.7
Connecting to [www.skype.com|78.141.177.7|:80]("http://www.skype.com%7C78.141.177.7%7C:80")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://download.skype.com/linux/skype-ubuntu-intrepid_2.1.0.81-1_i386.deb](http://download.skype.com/linux/skype-ubuntu-intrepid_2.1.0.81-1_i386.deb) [following]
--2010-05-13 14:57:32--  [http://download.skype.com/linux/skype-ubuntu-intrepid_2.1.0.81-1_i386.deb](http://download.skype.com/linux/skype-ubuntu-intrepid_2.1.0.81-1_i386.deb)
Resolving download.skype.com... 212.72.53.130, 204.9.165.83
Connecting to download.skype.com|212.72.53.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20165034 (19M) [application/octet-stream]
Saving to: `skype-ubuntu-current_i386.deb'

100%[======================================>] 2,01,65,034  378K/s   in 33s     

2010-05-13 14:58:06 (603 KB/s) - `skype-ubuntu-current_i386.deb' saved [20165034/20165034]

varun@the-observor:~$ sudo dpkg -i --force-architecture skype-ubuntu-current_i386.deb
(Reading database ... 168924 files and directories currently installed.)
Unpacking skype (from skype-ubuntu-current_i386.deb) ...
dpkg: error processing skype-ubuntu-current_i386.deb (--install):
 trying to overwrite '/usr/share/icons/skype.png', which is also in package skype-common 0:2.0.0.68+repack-0medibuntu3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 skype-ubuntu-current_i386.deb
varun@the-observor:~$ 
varun@the-observor:~$ 
varun@the-observor:~$ sudo rm skype-ubuntu-current_i386.deb
varun@the-observor:~$ 
varun@the-observor:~$

---

### Post by joshruehlig on 2010-05-13
I would cleanup any mess you made, should all be in that folder still unless you ran make install. Then google search ubuntu tweak. Download it, Openit and go to source center, enable skype, refresh. Then Applications, Enable Skype and download it. Should run perfectly... 

Except for under dual screen, cant get skype under dual screen working.

---

