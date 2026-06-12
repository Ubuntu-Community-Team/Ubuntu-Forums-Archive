---
title: "Got there in the end...9.10 and mythtv 0.22"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by J365 on 2010-01-10
Hello all,

Firstly thanks to all those who post solutions on this forum as without you lot I would have been absolutely stuffed during my recent upgrades.  I thought I would bring together the issues I faced (and solutions I found) in case there they help someone...somewhere....!

1)  Grub2.  ARRRRRRGGGHHHH.  I am sure there are some marvellous additions included in Grub2, but the problems caused at boot time nearly caused me to pop down to PC World and buy Windows 7.   I suffered 2 different errors:

a) Grub Loadingread error - solution provided by kansasnoob here [http://ubuntuforums.org/showthread.php?t=1288661](http://ubuntuforums.org/showthread.php?t=1288661)

b) During one of the many clean installs I got the Error 15 message.  I never solved it though since have found this: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

2)  Audio over HDMI.  I have an nvidia 8200 chipset and on install ALSA had muted my HDMI audio out (first thing was to enable HDMI audio in the Bios during boot).  The fix was simple but took e about 2 evenings to find:

i) open alsamixer bu typing *alsamixer* in a terminal
ii) navigate the volume levels using the left / right arrows and make sure all the ones you can adjust are turned up (make sure you go all the way to the end)
iii) make sure none have 'MM' at the bottom as this means they are muted.  This can be changed by pressing 'm'.
iv) TV - i had to change the hdmi input I was using on my TV.  It is a Sharp AQUOS and was trying to get audio though a pc jack socket rather than over the hdmi.  Once I had changed it to one of the other inputs it worked.

3) Having installed 9.10 I opened up two repositories:

i) [http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html) (I only used the 'release' one - includes VDPAU in myth package)
ii) [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then updated through 'update manager'

4) Restricted drivers - using the synaptic manager I installed nvidia 195XXXXX modaliases.  Then opened the restricted drivers option from system>admin and activated the 195 option.

5) sudo apt-get install ubuntu-restricted-extras (enable playback of MP3s etc)

6) sudo /usr/share/doc/libdvdread4/install-css.sh (enable playback of DVDs)

7) Through synaptic manager install mythtv and follow this guide:

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

8) After a few tweaks I was getting a mythfilldatabase error about a Qwidget.  I also could not get my frontend (seperate machine) to connect to the database.

sudo dpkg-reconfigure mythtv-database

Seemed to sort this... 

9) Jittery playback:

nvidia-xconfig --no-composite 

10) Went to bed...finally :D

I have been sing mythtv since the 0.16 release and I think this has been the most complicated upgrade since my first venture!  

Hope this helps someone and thanks again...

J365

---

