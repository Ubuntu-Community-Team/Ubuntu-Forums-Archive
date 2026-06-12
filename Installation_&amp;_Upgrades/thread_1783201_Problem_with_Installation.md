---
title: "Problem with Installation"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by Georrgi on 2011-06-15
Hi,

I tried to install Ubuntu 11.04 but i couldn't because the installation did'n go on. I show you with one screenshot. The installation stays always in this position. What can be the problem ?

Thanks

---

### Post by sikander3786 on 2011-06-15
Welcome to the forums :)

The installer might require you to be connected to the Internet while installation. And you aren't connected. If possible, connect your PC to the Internet and try again. Or we can try by-passing that check.

---

### Post by Georrgi on 2011-06-15
I tried a lot of times to install it, with internet, without internet, with all the tings checked but nothing helped. Also I formated the usb and one more time installed Ubuntu on it, but the problem stayed. :(

---

### Post by sikander3786 on 2011-06-15
Click the network icon in notification area and click 'Disconnect' under 'Auto eth0'. Restart the installer and try again. Thats the only thing I can think of, at the moment.

---

### Post by sikander3786 on 2011-06-15
Well, just tested. The installer should have no problem at all with installation if the PC isn't connected to the Internet so that is something else...

Did you check the MD5SUM of your downloaded image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that is ok, check your burnt disc for defects. You might need to press 'any key' as soon as the computer starts booting from the disc.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

And also, please post the hardware specs of your PC and the output of this command from Terminal: (You can press <Super> (Windows logo key) and search for 'Terminal')

```
sudo fdisk -lu
```

---

