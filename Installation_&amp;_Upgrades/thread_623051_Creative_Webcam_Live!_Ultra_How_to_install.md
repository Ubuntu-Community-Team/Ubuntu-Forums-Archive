---
title: "Creative Webcam Live! Ultra: How to install?"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by schlox on 2007-11-25
Hi Everybody! I am a real newbie. I just installed 7.10 yesterday. 

I have Creative Webcam Live! Ultra and when I connect it to a usb port, even the camera light doesn't turn on. I've seen this page:

> 
sudo apt-get install subversion
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-2.6.20-16-386
make
sudo make install
sudo modprobe ov51x-jpeg


I know that it would most probably won't work for my webcam because the one I have is quite old version. But still tried it. Unfortunately rastageeks.org seems like to have a problem.

So, anyone that may guide me how I can install this webcam, will be appreciated and remembered for a long time.

Greets,
Schlox

---

### Post by linuxwizard on 2007-11-25
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by schlox on 2007-11-26
> **linuxwizard said:**
> [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Thanks for the reply. 

It seems like my Web cam is not supported after a small search I made. My unique ID is :

041e:403c Creative Technology, Ltd WebCam Live! Ultra

Can anybody give advices? It is really important. I don't want to use XP again. Please...

---

### Post by malibusurfer2 on 2008-02-02
I have the same webcam and also can't get it to even power up under Ubuntu 7.10. I also run Windows XP using VirtualBox and got the cam to work there, so it does work. Seems like Creative doesn't have a linux driver for this model.

System,Administration, Easycam 1.35 shows it listed as Bus 002 Device 007: ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra. When selected, it displays "This software, EasyCam is still in test status. If your webcam is not detected, it may not be compatible with autodetection yet".

If anyone comes across a solution for the problem, please post it here.

Of interest check out:  [http://gkall.hobby.nl/sq930x.html](http://gkall.hobby.nl/sq930x.html)

Thanks.

---

