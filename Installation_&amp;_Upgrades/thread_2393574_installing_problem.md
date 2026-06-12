---
title: "installing problem"
date: 2018-06-05
forum: Installation &amp; Upgrades
---

### Post by 08viva on 2018-06-05
hi 
i try to install ubuntu 18.04 on my new laptop (ASUS core i7 hq7700 /geforce gtx1050 /8G memory) but during the installation when appear the load page the lcd back light turned off and when the language selection page  appear the keyboard and mouse doesn&#8217;t work.then every things become freeze.
(i try it with the ubuntu 16.04 and i have same problem)
any one can help me to solve this?

I have say I do this steps  
                                    1.check the installation file (has no error)
                                    2.try on ubuntu without installing (but doesn&#8217;t worked on my laptop)   
                                    3.installed this file on another PC successfully. 

when i google the problem i find some links but i am not sure that can help me.is it possible say your idea about this answer ?   

[https://forums.lenovo.com/t5/Linux-Discussion/How-to-install-Linux-on-UEFI-systems-where-GRUB-fail-to-install/m-p/674617#M3643](https://forums.lenovo.com/t5/Linux-Discussion/How-to-install-Linux-on-UEFI-systems-where-GRUB-fail-to-install/m-p/674617#M3643)

thanks for your attention

---

### Post by ubfan1 on 2018-06-06
Sounds like an Nvidia problem.  In Windows, turn off secure boot, and ensure shutdown is not hibernation (check the power options).  Did you try adding the nomodeset word to the grub command starting with "linux"?  Type "e" at the grub menu to edit, then add the nomodeset word at the "quiet splash" words.  after booting successfully, immediately run
sudo apt-get update  or the software updater from the launcher.  Then in the software and updates icon, look at the "Additional Drivers" tab, let the search complete and select the Nvidia driver which says "tested" if one is offered.  Select the latest if "tested" is not offered. Next boot should not need the nomodeset .

---

