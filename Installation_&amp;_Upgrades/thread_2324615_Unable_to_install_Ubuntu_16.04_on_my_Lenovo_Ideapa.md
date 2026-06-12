---
title: "Unable to install Ubuntu 16.04 on my Lenovo Ideapad 100-14IBY"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by Nayab Basha Sayed on 2016-05-15
Yesterday I bought Lenovo Ideapad 100-14IBY laptop. I was very excited to install new Ubuntu 16.04. I wanted to try Ubuntu before installing. When I boot from my USB pen drive, I couldn't able to open Terminal (Remaining applications working fine). I thought after installing Ubuntu it might work. But the installer also not starting when I try to open it. Can anybody help me please...:confused:

---

### Post by ubfan1 on 2016-05-15
Seems like you can successfully boot. Did you run any media checks?
1) Did you md5sum check the downloaded iso?                                                                             
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)                                                                     
  Check the number against the listing in the link for your release listed at                                           
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.                                                                    
2) If using a CD/DVD, did you burn the disc as slowly as possible?                                                      
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)                                                                 
3) Did you select the media check before trying to install?                                                             
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)                                                        
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?                                
Doing the above can save you a lot of time struggling with a bad install media.

---

### Post by ubfan1 on 2016-05-15
I just saw a similar problem on an older Thinkpad W520, W10 on hdd, Ubuntu 16.04 on a USB2 reader plugged into a USB3 port.  The desktop was visible, but the ctrl-alt-T did not start a teminal, and dash could not find anything (let alone a terminal).  The USB had worked just fine several hrs earlier. The problem seemed to be a failed mount of the media on /cdrom (it was empty).  Many things did not run, but I could switch to a virtual terminal (crtl-alt-F1) and login as ubuntu (no password).  From there, setting the DISPLAY (export DISPLAY=":0" )
and trying to run gnome-terminal, showed the failure errors reading squashfs.  Not even sudo worked, so shutdown wouldn't work, had to do a powerbutton shutdown.  Ran the media check next, and all was OK.  Rebooted again, and things were working.  Same port, not even a removal/reinsert of media.  Maybe try other ports.  I will have to look into this further.   I might need a BIOS upgrade, but you machine is new isn't it?

---

### Post by Nayab Basha Sayed on 2016-05-17
> [COLOR=#000000]1) Did you md5sum check the downloaded iso? [/COLOR]
[COLOR=#000000]See [/COLOR][https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
I did md5sum check. The result did not match with the original. So I downloaded again that image. It's installed successfully. Now I am using Ubuntu 16.04 64bit version on my laptop.
Thank you....
> [COLOR=#000000]I might need a BIOS upgrade, but you machine is new isn't it?[/COLOR]
There is an update available for my firmware too.:P

---

### Post by andrea109 on 2016-05-19
Hi I am waiting for the ideapad to be shipped home. In the meantime can I ask you how's everything working so far? WiFi issues? I need to get ready so I can install it on my machine any suggestions will be appreciated. 
Thanks

---

### Post by andrea109 on 2016-05-19
Also how are you planning to upgrade the bios?

---

