---
title: "US ROBOTICS (external) modem installation problem??"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by vanishedsoul on 2006-11-10
hi!

i have installed 6.06 drapper drake(64 bit), on my machine with

pentimum D 2.4GHZ (dual core), intel 945gnt motherbord with kingsten DDR2 512 ram

I have a an external modem of US Robotics (model 5631) 56k fax modem (v.92)....How can i install it on my machine??

---

### Post by lerox on 2006-11-11
hi there 
boot up with modem connected to serial port and on,system-->networking.modem properties enter your isp details,configure modem if your modem is plugged into serial port1 you must use /dev/ttys0 and so on.if all your isp setting are correct you must be able to connect by activating the modem.

---

### Post by vanishedsoul on 2006-11-12
hi again!!!

well i made the connection with the SYSTEM-->Administration-->Networking. My modem was 
detected at /dev/ttyS0, i did gave my ISP setting like the the Dialing number, Username, Password, didn't give anything in the DNS nor made any changes in the host tab and then pressed the Activate button. The connecting tone (handshaking tone) was heard but when the tone ended after 5-8 secs the modem got disconnected (voice came from the modem). Any help with this??

---

### Post by confused57 on 2006-11-12
Here's someone who got the same modem to work:
[http://www.ubuntuforums.org/showthread.php?p=1673661#post1673661](http://www.ubuntuforums.org/showthread.php?p=1673661#post1673661)

Here's the Wiki for dialup, if you haven't already checked it out:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

I don't use dialup, but I've read it can be difficult to configure...I've seen somewhere you can go into your **/etc/ppp/options** file and comment the line with **auth** in it, e.g.

change
```
auth
```
to
```
#auth
```

There' quite a few threads related to dialup in the forums, maybe you can find something in one of them that may help you.

It could be that your ISP may require their dialer program that you install to Windows using their cd?   Good luck...

---

### Post by vanishedsoul on 2006-11-12
believe it or not, thats my first post from the UBUNTU, i have done it. Used the wvdial.conf and here i am. thanks guyz

i have one more problem, i cant play mp3 nor any dvd. It gives an error message that i dont have to download the necessary plugins? Any help???

---

### Post by confused57 on 2006-11-12
> **vanishedsoul said:**
> believe it or not, thats my first post from the UBUNTU, i have done it. Used the wvdial.conf and here i am. thanks guyz

i have one more problem, i cant play mp3 nor any dvd. It gives an error message that i dont have to download the necessary plugins? Any help???
Glad you got it working...see the section on Multimedia, Music & Video:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

---

