---
title: "How to install wireless driver?"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by RealGomer on 2010-07-26
Right. I found the following link thru the Forum "Check if already posted" function - [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-bz2-files-491508/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-bz2-files-491508/) and
[http://ubuntuforums.org/showthread.php?t=1420464&highlight=install+wireless+driver%3F](http://ubuntuforums.org/showthread.php?t=1420464&highlight=install+wireless+driver%3F).
As I'm not the sharpest nail in the box, would someone kingly translate those posts to simpleton English. I just installed Ubuntu 10.04 and I found the drivers for my USB wireless-n dongle at [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) (it's a Zoom 4411 and WinXPSP3 says it's a rt2870 kit).
Thanky thanky.

---

### Post by RealGomer on 2010-08-21
My router, D-Link DIR-628, has two passwords. One is for the network itself and the other for the wireless security. When trying to connect using wireless and WPA/WPA2 security, make sure you enter the WPA/WPA2 password, NOT the network password. I still have wireless security (WPA) and I have wireless-n on my Ubuntu box.
So if you can't connect wirelessly:
First disable all wireless security to make sure the adapter is working correctly.
Second, enable WEP security and enter the WEP password, NOT the network password, as part of the setup. IF that works, then...
Third, enable WPA-Personal security and enter the WPA-Personal password.

---

### Post by RealGomer on 2010-09-17
I'm going nuts with this wireless. My D-Link DIR-624 stopped accepting requests from all four of my wireless clients. After much trial and error and rending of cloth and gnashing of teeth, I got the wireless to work on the three Windows clients. The Ubuntu 10.04 won't connect. Following my own advice above didn't help. Is the rt2870 driver in the kernel already? That's what the wireless claims to use. I deleted the wireless network and then created another using the same setting as used by my Windows clients - WPA2 security, same Network passpharse / preshared key, same SSID, same Automatic DHCP. The network shows up as a Hidden Wireless network (?) and the icon indicates the Ubuntu box is connected. When I try to get on the network, nothing. What am I missing? 
(I've also posted a message I received when trying to install the RT2870.bin file for the wireless card.)

---

