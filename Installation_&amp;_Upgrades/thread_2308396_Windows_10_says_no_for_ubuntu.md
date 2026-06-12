---
title: "Windows 10 says no for ubuntu"
date: 2016-01-02
forum: Installation &amp; Upgrades
---

### Post by timo_2 on 2016-01-02
Hello all!

I've upgrade my windows 8.1 to windows 10 on my *ASUS Eeebook X205TA* because I'm not into windows 8 and now the 10 is making me insane... (plus windows OS and anti-virus software takes a lot of space from 32GB SSD) 
I love linux so I thought that installing Ubuntu would be cool!
I've installed Ubuntu once in my desktop alongside with Windows 7 and I liked it but I ended up to uninstall it because I wasn't using Ubuntu that much.

Now the laptop refuses to boot from flashdrive eventough the settings are just like people's UEFI (or BIOS?) settings from YouTube "how to install ubuntu/linux in Windows 10" and I know how to make bootable flashdrive or make the computer to boot from USB. I've tried several flashdrives but the laptop boots straight to the windows 10. 

Is there something that I've missed? Thanks for your help guys <3!

-Tio

---

### Post by David2009 on 2016-01-02
Tio, 

I saw a thread with Asus X205TA.  I hope it will help.  
 
[http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)

---

### Post by ubfan1 on 2016-01-02
An X205CA would reset the boot order if booted without the specific USB which was put first in order.  From W10, you probably cannot use the function keys at bootup to select the UEFI Settings, so with the USB install media present, and W10 running, use the shift/restart trick, go through the screens (Troubleshooting/settings ?) to get to the settings, reset the boot order to USB first, and reboot.  Even replacing the USB with another (different brand) will cause the boot order to be reset.

---

