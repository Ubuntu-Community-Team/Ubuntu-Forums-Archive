---
title: "Screen resolution crashed"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by arcabuntu on 2010-07-30
Hi, this time I screwed up big time. I was wandering around the system parameters and saw that there was an option to activate a non-open nvidia driver for my Asus Emachine EL1200 with Ubuntu 8.04 install (pre-installed, worked fine for a year now).
 
So I did. However, when I restarted, my screen resolution was changed to 800*600 or so, no good. Although I could not see the right part of the same "nvidia" window, I managed to deactivate the driver. Regretfully when restarting the screen resolution was still 800*600. I thought it was 1440*900 for my Asus VK192S-B (checked it on internet) but it didn't work (did not check the refreshrate at that time). So I stared to fiddle around and stupidly accepted a 1280 * 800. As I said before the resolution is completely f***up now. I have about 4 copies of my desktop and the worst part is there are lines over it and I can not see what the windows say. I manage to get the resolution config screen, but can not get the right optios selected, working "blindfolded".
 
I looked at this helpful forum and identified the /etc/x11/xorg.conf file as the important file. Also I saw a xorg.conf.failsafe file with my original config! With the recovery cd of Asus I managed o set up a live session and actually can open the xorg.conf file and see the damned line with 1280*800. Regretfully the original /etc folder as well as the original home folder cannot be written in, or copied. Permission problems, as could be expected. I have some backup, but not of quite a lot of photos I uploadd from my camera recently. Reinstalling from scratch is fo the moment not an option.
 
Basically what I hope is that somebody can bail me out and tell me how I can either replace or edit the xorg.conf file on the original hdd, /etc/x11 folder, using a live session, or with whatever other method you advise me.
 
Thanks all in advance for your appreciated help!
Arjan

---

### Post by arcabuntu on 2010-08-04
Hi, finally I managed to reset the faulty screen resolution, thanks to the information gathered here and there on this forum. The solution is that from the hardly visible desktop, I pressed CTRL+ALT+F1 to start the console, which gave me that comfortable DOS-like text screen. Logged in as usual and executed the command "sudo mv /etc/x11/xorg.conf /etc/x11/xorg.conf.old", and it did NOT work! It said the directory didn't exist and that's when I found out that directory names in Ubuntu are case-sensitive, so when I used /X11/ it found the file and after a reboot it was resetted to 800*600 and I could see what I was doing on the desktop. Now installed EnvyNG to get the real nvidia drivers working... Thank you all that contributed to the other forums and gave so much helpful information.):P

---

