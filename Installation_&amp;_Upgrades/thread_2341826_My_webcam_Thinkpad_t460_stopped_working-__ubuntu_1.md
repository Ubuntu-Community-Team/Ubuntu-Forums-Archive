---
title: "My webcam Thinkpad t460 stopped working-  ubuntu 16.04LTS"
date: 2016-11-01
forum: Installation &amp; Upgrades
---

### Post by saigammar on 2016-11-01
Hello there, 

I have installed ubuntu 16.04 LTS (fresh install) removed windows completely. At the beginning I was able to use my camera with cheese and other applications. but all of a sudden, camera is not detected at all. I have looked for the camera on lsusb, lshw, but could not find it. Also I have tried to unload and load the camera modules using the command modprobe uvcvideo but still nothing seems to work. 

Any Idea of what causes the issue? 

my laptop specifications:
Lenovo Thinkpad T460, i7
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial
===
kernel info: 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



Thank you guys

---

### Post by speedwell68 on 2016-11-01
Can you confirm the camera actually works at all?  I spent hours trying to work out why my camera had stopped working to discover it had actually packed up.

---

### Post by saigammar on 2016-11-01
How can I confirm?. It's a brand new laptop I have just received it 2 weeks ago. And it had windows installed and I confirmed that camera was working. Then I formatted it and installed ubuntu, and also confirmed that camera works. but then I am not sure what application I installed or upgrade I did that caused the issue of my ubuntu not being able to detect my camera at all.

---

### Post by slickymaster on 2016-11-01
*Thread moved to **Installation & Upgrades**.*

---

### Post by ubfan1 on 2016-11-02
Do you any camera references in the output of:
dmesg | grep Camera
If not, it's a hardware problem.  Maybe as simple as a loose cable.  If the camara has just failed (and initial failures are a common failure mode), then replace it.  This situation is one in which the benefits of dual booting become obvious:  You may not care about Windows, but any maintenance people may, particularly if you want the work done under warranty.  Also, take a look at the BIOS/UEFI settings for USB and maybe cameras, toggle any you find to see if that helps.

---

### Post by saigammar on 2016-11-02
It is a built in webcam. My laptop is brand new and camera worked in windows and ubuntu for  awhile. Now I don't have windows anymore I will try to see what I can do to download windows and test it. lsusb -v|grep Camera shows the following line:
        wTerminalType      0x0201 Camera Sensor

dmesg| grep Camera shows nothing. 

do you have any other suggestion before I go into the hard one (installing windows). want to keep it as last resort before I contact the technical support. 

> **ubfan1 said:**
> Do you any camera references in the output of:
dmesg | grep Camera
If not, it's a hardware problem.  Maybe as simple as a loose cable.  If the camara has just failed (and initial failures are a common failure mode), then replace it.  This situation is one in which the benefits of dual booting become obvious:  You may not care about Windows, but any maintenance people may, particularly if you want the work done under warranty.  Also, take a look at the BIOS/UEFI settings for USB and maybe cameras, toggle any you find to see if that helps.

---

