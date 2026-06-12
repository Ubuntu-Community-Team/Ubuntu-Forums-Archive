---
title: "Apps requiring flashplayer won't run under 12.04"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2012-06-09
One of my PCs that I have upgraded 12.04 LTS won't run apps (e.g., youtube, speakeasy speedtest) that require Flash Player.  Latest versions of Adobe Flash Player are installed (You have Flash player 11.2.202 installed.) and Java scripts are installed.  VGA is  NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3) using the Nouveau video drivers.

How do I get apps that require Flashplayer running correctly?

John

---

### Post by ajgreeny on 2012-06-09
I do not know if this will help, but I can not get any videos to work on my system using that 11.2.202.228 or later version of flash.  No video window shows, just a blank area on screen.

In order to keep a working flash I have to use flash 11.1.102.63 and that works brilliantly.  I have an older ATI 9200SE card, not nvidia, so this info may not be any use to you, but to try it out see this thread from lovinglinux, the forum member who also made the flash-aid add-on for firefox, where you can download the 11.1.102.63 version and then install with flash-aid, or do it manually by following the instructions.

Note carefully the security warnings advising using **noscript** or **flash-block** if you go the downgrade route

---

### Post by Frogs Hair on 2012-06-09
I run the Firefox Nightly build and have the latest flash an 8 series Nvidia Card with current proprietary drivers installed.

Besides Youtube I used the following sites today, but it was required to allow scripts with the NoScript add-on.  

[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

[http://www.crackle.com/](http://www.crackle.com/)

---

### Post by darkod on 2012-06-10
You can also try installing the flash library manually, I always do that.

Go to the adobe.com website and download the flash for linux. It's a tar.gz compressed archive. Unpack it where ever you want. You will see a libflashplayer.so file and some folders.

Inside your Home folder, hit Ctrl + H to show hidden folders. Inside the .mozilla folder create a folder named plugins. Copy the libflashplayer.so in there and restart firefox if it was open.

That should be it. It's better to remove all packages you installed while trying to make it work so that they don't interfere.

---

### Post by Davey H on 2012-08-04
Has anyone got any updates if this is fixed. I have just installed Xubuntu 12.4 on my daughters Viao laptop and U Tube won't work on it for her. I have downloaded the latest flash player through software centre.

---

### Post by jmore9 on 2012-08-04
Have you gone to the adobe flashplayer test site and see if it says your flash is installed and working and it tells you what version you have.

Just google how to check version of flashplayer installed

---

### Post by cigtoxdoc on 2012-08-04
I have foud this to be a function of the PC.  I have one PC that passes the flashplayer test, but won't handle applications.  The only logical reason is that 12.04 does not have the correct nVidia driver (96 series) and the nouveau driver does not cut it.

John

---

### Post by darkod on 2012-08-04
I will say again, as in post #4, do it manually. Unless you have some driver related issues, it should work 100%.

I am still on 11.10 because I am waiting for 12.04.1 to come out to install it, but I have been using the manual flash plugin file since 9.10 and it always worked.

---

