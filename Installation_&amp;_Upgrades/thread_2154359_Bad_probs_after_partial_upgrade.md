---
title: "Bad probs after partial upgrade"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by Lateralus138 on 2013-06-14
Hi, I recently upgraded to 13.04 and only had to fix a few problems after the upgrade, but after that it was working fine. Then yesterday there was an update message and it said it could only do a partial upgrade and like an idiot I did it. There wasn't a reboot message (though I know it's smart to always reboot after any upgrading operation) so I then commenced to install the Intel graphics drivers from here [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads). I then rebooted to find I had major problems as you will see in the screenshot below. I sort of assumed it was either my failure to reboot before i installed anything else or that the drivers I installed were screwy and so I went to the forum for those drivers and someone told me that it only updates a certain lib file and that what he seen in the screenshot would have nothing to do with my current issue. So I have come here for help. The Unity bar hides, but leaves a sort of "ghost" background of the bar when it hides and all other animated docks leave a sort of tracer behind as they move... everything is extremely slow and can't be maximized/minimized when in the background, the only way I can alter a window is if I alt-tab through them which takes a long time to do. My guess is that I have done something to Compiz.I have tried uninstalling the graphics drivers and, of course, it didn't fix anything. Please help.
[[IMG]http://i254.photobucket.com/albums/hh119/faithnomoread/th_Screenshotfrom2013-06-13111017_zps51cf8233.png[/IMG]]("http://s254.photobucket.com/user/faithnomoread/media/Screenshotfrom2013-06-13111017_zps51cf8233.png.html")

---

### Post by dino99 on 2013-06-14
Times should have teached you to mostly use ubuntu archives & trusted sources (like ppa(s) ) only.

Boot in recovery mode , select the root option after having enabled the network, then clean the system (clean/autoclean/autoremove), update (using the "dpkg" option)
Try to purge the installed intel driver, then install xserver-xorg-video-intel
Finally select "resume" to continue booting

---

### Post by Lateralus138 on 2013-06-14
> **dino99 said:**
> Times should have teached you to mostly use ubuntu archives & trusted sources (like ppa(s) ) only.

Boot in recovery mode , select the root option after having enabled the network, then clean the system (clean/autoclean/autoremove), update (using the "dpkg" option)
Try to purge the installed intel driver, then install xserver-xorg-video-intel
Finally select "resume" to continue booting

Believe it or not I do know better, but while playing games, especially Minecraft, it is a considerable difference in fps from Windows to Ubuntu... In Windows I can get a steady 30 fps, while in Ubuntu I can barely get more than 20 with and average of 15 and I was hoping anything would work so I tried that driver.... 

Anyway, I had done everything you mentioned already up until installing xserver-xorg-video-intel. I'm not as familiar with dpkg as I am with apt-get, so I am not sure what you mean by update with dpkg? I see there is an --update-avail option, but seems to depend on a specific package, but I am not sure what to do there. 

I tried to use apt-get to install xserver-xorg-video-intel and it says a dependency is missing called xorg-video-abi-11 and says it is not installable so I am getting ready to search that issue, or maybe you can shed some light please? Thanks for your help.

---

### Post by Lateralus138 on 2013-06-15
Anyone please?

---

### Post by Lateralus138 on 2013-06-17
You not getting notifications[**[COLOR=#000000]dino99?[/COLOR]**]("http://ubuntuforums.org/member.php?u=129712")

---

