---
title: "Cannot install"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by richardrosa on 2007-12-08
Greetings All
  
 I am attempting to install Ubuntu (7.10-dvd-am64) on an Asus M2NPV-VM system, without any 
success. The first tries using the defaults result in a locked display about 30 seconds into 
the boot. I then tried removing the "quiet" option i(as suggested by a few other posters) on the boot and it got a little farther into the boot before displaying a scrambled screen. The final try was removing "quiet" and selecting "Safe graphics mode". This ALMOST seem to work . However, 
I end up with a black screen and nothing to do but power off the machine.


Any ideas, suggestions or help is greatly appreciated. 


 Thanx in advance.


 Rich

---

### Post by i586 on 2007-12-08
Try checking the CD for defects. You can do that by selecting the option from the boot menu.

Regards.

---

### Post by Pumalite on 2007-12-08
You need to do md5sum before burning, burn in good quality CD-R media at 4x, check CD integrity before install.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Thanoulis on 2007-12-08
It is your monitor, not your hardware...
Try to edit /etc/X11/xorg.conf, and include the HorizSync and VertRefresh ranges of the monitor you're using...that way the X server will work properly...:)
Good luck!

---

### Post by Pumalite on 2007-12-08
At the end of the installation, on a blank screen, try:
Ctrl+Alt+F1 to get command line
username
password
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver
Then: startx
Or sudo /etc/init.d/gdm start

---

### Post by richardrosa on 2007-12-08
>> Try checking the CD for defects. You can do that by selecting the option from the boot menu.

I ran the check on the DVD (when I first encountered the problem) and the check ran clean. I don't think this is a problem with the DVD. I was able to boot this DVD on another system to the point 
where the system was usable. 

>> Try to edit /etc/X11/xorg.conf, and include the HorizSync and VertRefresh ranges of the monitor you're using...that way the X server will work properly..

 How do I modify xorg.conf on a DVD? I cannot get to a point in the boot process where I can change this. Maybe a parm on the boot line? If so, can you suggest one that might work?

 Thanx for the help &  suggestions..


 Rich

---

