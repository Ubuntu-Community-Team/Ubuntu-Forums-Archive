---
title: "nvidia current driver and no sound"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by ar87 on 2010-06-17
I am facing an interesting problem. When the nvidia current driver is enabled, about 30% of the time there is  no sound when I turn on my laptop (HP G60). When I check the Sound/Hardware, there is nothing listed there. I know that there are no problems with my sound card since I don't have this problem on vista (dual boot) and when the nvidia driver is deactivated. 
  In addition, when this happens, and when I try to shutdown or reboot, the system just logs out and stays there. I am forced to login again and use (sudo shutdown -h now) command. 
  What might be the problem?   

ps. I am using lucid. 

Thank you for any help.

---

### Post by lidex on 2010-06-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by ar87 on 2010-06-18
Hi lidex. Thanks for your reply. Here is the information you requested:

Laptop Information:

              hp G60-120US
              s/n  2CE83970KN

 ```

uname -a
Linux aapyan 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

aplay -l
aplay: device_list:223: no soundcards found...

dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                       
   ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                   
              ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                          
         Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                    
   GStreamer plugin for ALSA

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20561 (Hermosa)

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP78 HDMI

 
```

---

### Post by lidex on 2010-06-18
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by ar87 on 2010-06-19
Thank you very much for your help lidex. The problem disappeared after I added those lines to the file.

---

