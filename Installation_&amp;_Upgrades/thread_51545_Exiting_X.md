---
title: "Exiting X"
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by tr1cky on 2005-07-24
I've recently installed ubuntu for the first time. So far things are going great with the exception of video drivers. It seems, whenever i play ut2004 (and then only on certain maps) my screen begins to shake wildly and then shut off periodically. My solution is to reinstall my nvidia drivers (i have a FX5600) since remounting etc. hasn't worked. The only issue is that the nvidia drivers require that the X Server isn't running and I can't for the life of me figure out how one does that. If you can explain how its done (or if the problem could be something else), please do. Thanks in advance!

---

### Post by varunus on 2005-07-24
Its not clear from your post, but did you install the proprietary nvidia drivers from synaptic?  You don't need to use the one's on NVIDIA's site unless the older ones don't work for you...You can open synaptic and install the packages "nvidia-glx" and "nvidia-settings" to get the driver.  Then run "sudo nvidia-glx-config enable" in a terminal to enable the drivers.  You may also need to edit your /etc/X11/xorg.conf slightly, or run the nvidia-settings utility (it should show up under applications->system tools if i remember correctly).

If you must get the drivers from NVIDIA's website:

To shut down your X server:

 - Hit CTRL-ALT-F1
 - Type "sudo /etc/init.d/gdm stop"
 - Enter your password at the prompt.

X is now shut down.

---

### Post by tr1cky on 2005-07-24
yes, i apt-got the nvidia drivers as it says on ubuntuguide.org, and thanks for the help

---

