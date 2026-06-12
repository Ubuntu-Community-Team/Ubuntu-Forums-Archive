---
title: "Problem: nVidiaOnly one monitor detected - Fresh install"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by DoRullings on 2011-12-17
Hi guys

I really need your help with this issue. This post is long, but I want to provide as much information as possible.

**Problem: **I have two monitors connected to my desktop PC  with a GeForce 7950 GT display card. I tested if my system is compatible  by running Ubuntu 11.10 from an USB stick, and everything worked fine. I only  had to activate the second monitor in System Settings -> Displays. After the installation NVIDIA drivers has haunted me. Please read the description below:

**Ubuntu version: 11.10 64 bit**

**System: **

[LIST]
[*]Two Dell monitors:
[LIST]
[*]Dell E2209W
[*]Dell E228WFP
[/LIST]
 
[*]Video card: GeForce 7950 GT
[LIST]
[*]Two DVI outputs
[*]The monitors are connected with DVI cables
[*]I have tried to connect with VGA adapter, but that did not make any difference
[/LIST]
 
[/LIST]
 
[B]
First attempt to install Ubuntu: 
[/B]If I remember  correctly I was made aware of that there was "third party drivers"  available for my graphic card after the installation of Ubuntu was done  and I entered the Displays settings dialogue box. I accepted this and  installed the highlighted driver. From then on all settings had to be  done in "NVIDIA X Server Settings". I tried *all* possible  settings, and all available drivers, including the recommended one,  which Ubuntu did not choose by default. The best result I got was with  the recommended driver,  that both monitors was activated and the  desktop was extended, but I got an error message every time I logged  inn. I can not remember exactly what the error-message said, but it  believe it complained about that the resolution and/or refresh rate was  wrong and it had to choose a different settings. 

At this point the xorg.config file was so messed up and I decided to reinstall Ubuntu and **not** install the NVIDIA drivers.

**Second attempt to install Ubuntu:**
After  the installation I opened the Displays settings, but only one monitor  was detected. I checked if the NVIDIA drivers was installed, and it was.  After the installation I haven not changed anything because I realize  that I need help and that it is better to go to this forum with a system  clean as possible as a starting point for debugging. 

**Current status:**

[LIST]
[*]Driver installed: NVIDIA version 173 ( see screenshot below )
[*]Monitor 0 - "DFP-0-(Dell E2209W)" is detected and activated ( see screenshot below )
[*]Monitor 1 - "DFP-1-(DELL E228WFP)" is detected, but not activated ( see screenshot below )
[*]"X Server Display Configuration" display an error message only:
[LIST]
[*]"Unable to load X Server Display Configuration page: Failed to query NoScanout for screen 0"
[/LIST]
 
[/LIST]


**Conclusion: **I  do not need 3D support in Ubuntu. It would be fine if it worked because  I might do some programming using Open GL in Ubuntu in the future, but  that's it. I see two solutions that you guys may help me with:

[LIST=1]
[*]The  configuration that was used when I booted Ubuntu from USB worked fine. I  thinkl that involves removing the NVIDIA drivers and install Nouveau  drivers. What is the best way to accomplish this?
[*]Get the NVIDIA  drivers to work. This would of course be the best result, as I wrote  above, not necessary. 3D would be great to have, but if it makes my  system unstable or it involves a lot of tweaking to get there, I prefer  the first solution.
[/LIST]

**Log files: **I saved the  Xorg.0.log file when I loaded Ubuntu from USB and directly after the  installation. I have tried to find sensitive information in this log  files, but I did not find any so I take the risk to post them. I can see  that they contain useful information. If anybody find sensitive  information in them, please alert me so that I can remove them.
[URL="http://fildeling.no/docs/forum/Xorg.0.log"]
[/URL]
[LIST]
[*][Xorg.0.log from USB]("http://fildeling.no/docs/forum/Xorg.0.log")
[*][Xorg.0.log after installation]("http://fildeling.no/docs/forum/From_USB_Xorg.0.log")
[*][The current xorg.conf]("http://fildeling.no/docs/forum/xorg.conf")
[/LIST]
[B]
Screenshots:[/B]

[LIST]
[*]Aditional Drivers
[/LIST]
[IMG]http://fildeling.no/img/forum/Additional_drivers.png[/IMG]


[LIST]
[*]Detected and activated monitor:
[/LIST]
[IMG]http://fildeling.no/img/forum/Detected_and_activated_monitor.png[/IMG]



[LIST]
[*]Detected but not activated monitor:
[/LIST]
[IMG]http://fildeling.no/img/forum/Dell_E228WFP_settings_window.png[/IMG]



[LIST]
[*]X Server Display Configuration:
[/LIST]
[IMG]http://fildeling.no/img/forum/X_server_display_configuration.png[/IMG]



[LIST]
[*]Graphic Card Information:
[/LIST]
[IMG]http://fildeling.no/img/forum/Graphic_card_info.png[/IMG]

[LIST]
[*]X Screen Information:
[/LIST]
[IMG]http://fildeling.no/img/forum/X_Screen_0.png[/IMG]

---

### Post by dino99 on 2011-12-17
what i can see:
- nvidia 173 should not be used, but nvidia-current

so i suppose that xorg.conf is borked. As actual kernel directly deals with X, try to start with a clean config:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo synaptic
- remove/purge ALL the installed nvidia related packages
- add this ppa to get the latest nvidia-current: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
- add it to your synaptic/third party tab
- update
- install nvidia-current and nvidia-settings

sudo reboot
sudo jockey-gtk

from the menu, run nvidia-settings to deal with the dual monitors config

---

### Post by DoRullings on 2011-12-19
Thanks for your reply dino99!

I followed your instructions almost exactly as you described them. When I write "almost" is it because I removed all nvidia related packages by typing nvidia in synaptic search box and removed all installed packages that came up from the search query. I noticed that jockey-gtk was one of the packages that came up, or was it a dependency? I do not remember. Anyway, I assumed that it would be installed when I installed the nvidia-current or nvidia-settings, but it did not. I looked into the nvidia controll panel and everything looked fine, and I set the monitors in TwinView, and from then on everything has worked just fine. I have just installed jockey-gtk because I read that it handles more than display drivers, and I have some problems fine tuning my MS Wireless keyboard and mouse, especially the mouse wheel scroll speed and that middle button is not doing anything. I will continue doing research on this.

Thanks for your help! I really do appreciate it! :-)

---

