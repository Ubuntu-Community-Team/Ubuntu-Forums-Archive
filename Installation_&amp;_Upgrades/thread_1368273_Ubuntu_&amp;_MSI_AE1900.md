---
title: "Ubuntu &amp; MSI AE1900"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Joern_MSI on 2009-12-30
Hello,

how can I calibratate the touchscreen after installing Ubuntu 9.04? Does any actuall HowTo exist (maybe multitouch, webcam & ...)?

How can I parallel minimize the power consumption in Ubuntu, because this PC should run as an interface for my home-automatisation 24h/day...

with regard

---

### Post by Joern_MSI on 2010-01-04
if somebody is also seaching for this topic.

Just to use the touchscreen you first have to change the resolution in Xorg.conf to 1366x768.
To calibrate it you can use "Touchscreen calibration", note down the values and enter them by hand in the 50-ideaco.fdi file.

```

sudo aptitude update;
sudo aptitude upgrade -y;
sudo aptitude install xserver-xorg-input-evtouch -y;
mkdir ~/ae1900;
cd ~/ae1900;
wget http://www.chemisus.com/files/ae1900/xorg.conf
wget http://www.chemisus.com/files/ae1900/50-ideaco.fdi
sudo cp -b xorg.conf /etc/X11/xorg.conf
sudo cp 50-ideaco.fdi /etc/hal/fdi/policy/
sudo shutdown -r now;

```

---

### Post by poloni on 2010-10-19
Hi there!

I tried to install Ubuntu Remix 10.10, and the touchscreen didn't work properly. Only in 1/4 of the screen. I followed the suggestion above, and the problem changed with the cursor was crazy.

Now, I installed the Ubuntu Desktop 9.10. I followed the above instructions and the touch screen worked better, but, the cursor is not accurate. I ran the "calibrate_touchscreen" command, but nothing changed.

Well, can someone help me solve this problem?


Thanks!

---

### Post by poloni on 2010-10-19
Hi there!

The chip controller of touch screen IEACO IDC6681 and I found the owner ([http://www.ideacom.com.tw/en_home.htm](http://www.ideacom.com.tw/en_home.htm)).

There you can download the driver to Ubuntu and Fedora distributions. After I'll test and I put the result here.

---

### Post by poloni on 2010-10-19
Hi MSI AE1900 users!

I fixed my touch screen using the device driver supplied by IDEACOM and worked fine.

Now, I'm using Ubuntu 9.10 Desktop with this driver. I'm so happy :).

---

