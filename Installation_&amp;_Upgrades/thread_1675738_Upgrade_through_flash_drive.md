---
title: "Upgrade through flash drive"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by joyneo04 on 2011-01-26
Hi,

Recently I have purchased a laptop of compaq. Currently I have windows xp and I have installed Ubuntu 9.10 in my laptop. Now I have downloaded Ubuntu 10.4 from the net. Now I want to upgrade from 9.10 to 10.4. The downloaded contents of 10.4 is there in my flash drive.
 Kindly let me know how can I upgrade. Also kindly note that I am having a reliance USB net connect but I am not able to connect to the internet through it as 9.10 is not supporting. I have tried to install the wvdial but was not able to install the same.
Kindly help me out as I am fully non technical guy and don't have any idea of software but I want to learn.
In case I have to save it to root or home folder kindly let me know the path and other things that I have to type in the terminal.As I don't have any idead of any command as well.

---

### Post by sikander3786 on 2011-01-26
Regarding the upgrade issue, you can only use the alternate iso for upgradation.

> Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1. Download and burn the alternate installation CD.
   2. Insert it into your CD-ROM drive.
   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:
gksu "sh /cdrom/cdromupgrade" 

Regarding the wireless issue, I think it would be more helpful to post that query in a separate thread under Networking & Wireless.

You don't need to save root or home anywhere else. Instead, save all your personal files and important data to a safe place as having a backup is a good habit.

---

### Post by joyneo04 on 2011-01-26
Thanks a lot but right now I dont have cd and can't wait any more. Thats why I installed 9.10. Is there any way to upgrade through pen drive.

---

### Post by sikander3786 on 2011-01-26
No, you can do it from a Live USB. You need a disc with alternate Ubuntu image. That is not the desktop image that we use most of the time.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

As another workaround, did you try booting your system with the USB in "Try" mode. If it boots and everything works as it should, you can do a clean install with 10.04 or 10.10.

---

### Post by joyneo04 on 2011-01-26
Hi,

Thanks a lot...Actually I have arranged alternate internet connection and now I am directly upgrading it from the net. Although thanks a lot once again for your prompt and timely revert.

---

