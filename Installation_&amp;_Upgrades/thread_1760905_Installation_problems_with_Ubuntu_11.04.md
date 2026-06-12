---
title: "Installation problems with Ubuntu 11.04"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by pyromaniacwolf1994 on 2011-05-17
Hey I'm having a problem installing Ubuntu 11.04 using wubi, with Windows 7. I was apparently able to install it, but when I try to log in with the username and password I created, with anything other than "Ubuntu Classic (No Effects)" it acts like it's loading onto the desktop, but stops. Basically it loads a blank screen with what I'm assuming is the background for the desktop but...that's all. It doesn't load any icons, or apps, or anything. The cursor works just fine, but that's about it....I waited 15 minutes before I finally got mad and did a hard shutdown then turned it back on and booted it into Ubuntu...I did this about 5 more times, only each time I waited only 5 minutes. I then uninstalled Ubuntu, then reinstalled it, had the same problem. I uninstalled it a 2nd time and then reinstalled it a second time...same problem. I haven't yet uninstalled it a 3rd time yet since I figured I could come here. If it helps my computer is a Dell Inspiron 15R notebook PC that I got just after last Christmas and as far as I know the graphic card shouldn't be a problem since I ran games like World of Warcraft and Dungeons and Dragons Online with Windows just fine. I'd really appreciate any help. Thanks and have a nice day.

---

### Post by bcbc on 2011-05-17
Maybe this will help - the answer has two parts - the first regarding the USB doesn't seem to affect you [http://askubuntu.com/questions/16077/cant-install-on-dell-inspiron-15r/16080#16080](http://askubuntu.com/questions/16077/cant-install-on-dell-inspiron-15r/16080#16080)

---

### Post by pyromaniacwolf1994 on 2011-05-17
I tried this and it didn't work...thanks anyway. I'm gonna try and install Ubuntu 10.04 LTS and then upgrade from there to 11.04

---

### Post by pyromaniacwolf1994 on 2011-05-18
Okay...I installed Ubuntu 10.04 LTS and the install went fine except for one thing...now my wi-fi sin't working!!!!

---

### Post by bcbc on 2011-05-18
> **pyromaniacwolf1994 said:**
> Okay...I installed Ubuntu 10.04 LTS and the install went fine except for one thing...now my wi-fi sin't working!!!!

Is it a broadcom? Try this sticky from the Networking and wireless subforum: [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by pyromaniacwolf1994 on 2011-05-18
No it's not a Broadcom...also I just noticed something. I ended up trying to download the .iso image and when I did so, it came as a .zip file instead of an .iso image, and when I burned that to a disk, and then tried to install from there, it wouldn't even boot into linux..it still booted into Windows automatically...and yes I made sure that the settings are arranged to boot from a cd/dvd

---

### Post by bcbc on 2011-05-18
If you have winzip or winrar (or other compression software) it associates the .iso extension as a "Compressed file" so you'd see Zip file or RAR file. It's not.

Change Windows to always show the file extension.

You have to use special software to burn the ISO to the CD. See [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (step 2, Show me how)

My dell's have intel wireless cards and they always connect first time. What type do you have?

---

