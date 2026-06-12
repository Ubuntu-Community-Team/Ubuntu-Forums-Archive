---
title: "Kubuntu installation failed!"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by Citta on 2013-10-28
Hi,

Just tried to install K. via Wubi. After completion and restart, bootloader-Win and Kub-klicked Kub. A black and white surface with "no wubildr" and " error prefix not set" or something similar appeared.
It was so fast displayed(how to stop?), perhaps the quotes are not complete. 
Then "grub" and blinking sign was displayed. 
How to solve this mishap?
Thanks!

---

### Post by Citta on 2013-10-28
Continued: Now a black surface with "normal mode" appeared. Entered "normal mode", a very short moment a Kubuntu screen with this moving dots was displayed, the monitor went black with a white mouse-pointer......waiting....nothing happened...pressed "esc" and several others, no progress. 
I had to reboot the PC via off/on switch.
What to do??
Thanks for your advice!

---

### Post by Toz on 2013-10-28
*Seperate related threads merged. Please use the reply buttons instead of creating a new thread for the same issue.*

---

### Post by Citta on 2013-10-28
I did not understand  your reply completely, just that something went wrong? What to do now?

---

### Post by Toz on 2013-10-28
You created two threads for the same issue. One was a continuation of the other. Nothing to do now as I have merged them so it is easier to follow.

---

### Post by mastablasta on 2013-10-28
wubi is no longer supported.

what is the Kubuntu you are tryign to install? 

What is the OS (which windows ver.) you are trying to install into?

IF you want to only try Kubuntu use the Live boot option or use virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by bcbc on 2013-10-28
See this: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by Citta on 2013-11-07
It was the newest version.
Win7HomeProf..
I burned Kub on a DVD, restarted the PC, the Kub-screen appeared for a while...then the monitor was filled with a kind of colored threads. Another try-same result. 
Ubuntu on a DVD, this went well, but when trying to install it on C, a SSD, it failed, this option was not given, just D, a 1TB HDD. On C was still much capacity, because I deleted a lot before the installation. 
There were around 50GB left!

-Why did the Kub-installation failed?
-How to install it on the SSD?
-Dualboot(Win/Linux) wanted!

Thanks a lot for your patience and advice,
Citta

---

### Post by mastablasta on 2013-11-07
if all is well with the image you downloaded (you checked the md5sum?) then probably you need to add nomodeset paramenter on boot: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

you need to give it emtpy, **unformatted** disk space. not NTFS formated empty space. the empty disk space then needs to be formated in linux file format. this is done automaticly during install. you may need to use "something elese" option and manually create root (/) and swap (/swap) partitions. i am not sure but kubuntu has this specify parittion manually and not like ubuntu which has the option to thrown itself on empty HD space. : [https://help.ubuntu.com/community/GraphicalInstall/Kubuntu](https://help.ubuntu.com/community/GraphicalInstall/Kubuntu)

---

