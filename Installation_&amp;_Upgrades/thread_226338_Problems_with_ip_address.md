---
title: "Problems with ip address"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by paddygman on 2006-07-31
Hey guys
I recently upgraded from breezy  to dapper and also moved house and somewhere in the upgrade and change of ip address my domain wont connect to my machine now. I have updated with my provider the ip address and am certain it is not a problem there as when i try the local ip 127.0.0.1 it trys to send me to the old ip.
I have searched for what is causing it to forward the ip but cannot find it.
I have tried setting the device to static and again have returned to dhcp but it still redirects to the old ip.

Anyone any suggestions as to what is redirectin it.
ie my old ip was 110.40.12.147
      new ip is  110.40.8.12

when i access [http://110.40.8.12](http://110.40.8.12) or [http://127.0.0.1](http://127.0.0.1) it tried to load [http://110.40.12.147](http://110.40.12.147).

I have tried to reinstall apache and all of its plugins but i believe it is not a problem with that but the actual configuration somewhere else. 

Anyone any suggestions??

---

### Post by halitech on 2006-07-31
check this and see if you set something incorrectly 

/etc/hosts

[page 3 setup hosts]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3")

---

