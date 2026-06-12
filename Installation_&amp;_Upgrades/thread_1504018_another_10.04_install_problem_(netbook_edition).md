---
title: "another 10.04 install problem (netbook edition)"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Asagrim on 2010-06-07
I browsed the forums for the better part of the day, and did not seem to find anything that would fit to my problem, or a proper solution to it.

Please before posting a possible solution, bear in mind that though i consider myself a professional Windows user, i do not have any knowledge of Linux!

I have a Windows XP/Windows 7 dual boot system.

My problem:
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

I follow these instructions to the letter, the live "CD" works fine - using a USB stick, i do not have a DVD drive, in- or external -. When i try to install Ubuntu from the live system, it corrupts my master boot record, i get the Error: No Such Device #####################. After i fixed this i tried to install Ubuntu under windows, using the same usb's wubi installer. The install completes, i reboot, and after selecting Ubuntu in my boot menu, i get that likewise well known error with wubildr.mbr ([http://ubuntuforums.org/showthread.php?p=7980168#post7980168](http://ubuntuforums.org/showthread.php?p=7980168#post7980168))

Rebuilding the USB stick doesn't make any difference, it behaves the same way.

The wubi installer has the very annoying habit of downloading the iso during the installation procedure every time, i don't know why i can't just select the iso downloaded in the first step of the above link. This way i can not check any md5 because i have no idea where it downloads the iso.

What should i do to get Ubuntu working? Reinstalling any of my Windows systems is not an option, it is every time like gambling, i am using the same installation files, but sometimes the result is just not the same.

---

### Post by Asagrim on 2010-06-08
Strange as it is - i tried 4 times to verify - i solved the problem. When i created the USB drive, and installed Ubuntu with wubi _without_ using the live CD feature it worked. Using the live CD feature created the issue.

---

### Post by bcbc on 2010-06-10
When you download the 'wubi' cd you are in fact downloading the ubuntu cd and it happens to have a wubi.exe file on it - so you can install under windows.

When you run as a live cd/usb you are not running wubi, but actually booting ubuntu from the cd.

If you run as a live cd, and then click install, you are installing ubuntu directly to the hard disk - this is not a wubi install.

The only way to install wubi is by running wubi.exe under windows.

PS in answer to your other question, if you place wubi.exe and the ubuntu .iso in the same directory it shouldn't download the iso image every time. (It will only do this if it doesn't like the version of ubuntu you have, but there are some overrides to force wubi.exe to use the version in the same directory).

---

