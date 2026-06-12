---
title: "Ubuntu 20.04 - Nvidia fan / overclock control issue (gpu mining rig)"
date: 2020-05-04
forum: Installation &amp; Upgrades
---

### Post by mstrozier on 2020-05-04
Afternoon.  I have installed Ubuntu 20.04 on this rig multiple times today due to screwing various parts up when trying to enable fan and overclock controls on my gpu's.   I now think I've yet again screwed something up with xorg so in the process of a clean fresh reinstall and looking for some guidance on my next steps.   What I have is a rig of 4 gpu's and it's running off the onboard video from the intel cpu.   After the clean install it is great to see it installs the nvidia drivers correctly and when I do a nvidia-smi all looks well.  In the past my next step was to do a sudo nvidia-xconfig  -a  -cool-bits  -28  and this is where my problem arises.  After doing this step I can no longer boot.  It'll stop at a blank screen with Ubuntu written at the bottom and nothing else.  Control + Alt + F2 does nothing.  And on this first install I forgot to setup SSH so well, had to reload.   2nd time around I installed both XRDP (so I can remote locally with windows remote desktop) and I also added SSH as a backup.   I read that I needed to run nvidia-settings and go to x config and save the configuration.  Well problem arose with this.  All that shows up is at first 3 options to choose.  Power Mode.  Nvidia On Demand or Intel power saver (can't recall exactly the wording).  I choose Nvidia On Demand and rebooted.  Then going into nvidia-settings I now see what I am familiar with, however still no nvidia x configuration screen.  All I have is my 4 gpus with their thermal, power and a profile option to save and then the screen again to choose from the 3 original options (power, nvidia on demand, intel).

So this time I ran sudo nvidia-xconfig  -a  -cool-bits  -28  again so it created a config file for me.   Made a backup of the file.  And then sudo nano  to edit the original file and tried to make changes to mimic what a default file would look like (had I just done sudo nvidia-xconfig with no options, the output that gives).   And after reboot well, same issue.  Blank screen with just Ubuntu at the bottom.  And Control Alt F2 does nothing.  So tried SSH and that worked.  Great.  So did a rm over the file rebooted, and tried again.  I read in another forum that I could create a folder within X11 named xorg.conf.d and then create a conf file like 28-coolbits-conf and then the following:
[COLOR=#1C1C1C][FONT=&amp]Section "Device"      Identifier "Device0"      Option      "Coolbits" "28"  EndSection

Tried this, back to blank screen.  Edited this file thru SSH to -28 thinking maybe I needed that hyphen and well still not working.

So my question is how can I enable fan control and overclocking abilities on nvidia gpu's now? 

Thanks


[/FONT][/COLOR][IMG]https://ibb.co/c1dBwPP[/IMG][COLOR=#1C1C1C][FONT=&amp]
[/FONT][/COLOR][IMG]https://ibb.co/c1dBwPP[/IMG][COLOR=#1C1C1C][FONT=&amp]
[/FONT][/COLOR] [COLOR=#1C1C1C][FONT=&amp]






[/FONT][/COLOR]

---

