---
title: "ATI HD 4870 - total crash after kernel update..."
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by pawhtiobo on 2011-07-01
Hi,

I have just done a fresh install of 10.10 (full updates) with my new HD 4870, downloaded the last catalyst 11.6 from AMD, i have done the normal procedure of the driver installation, Ubuntu booted correctly, i changed some options in CCC, one of them the "video tearing option" after that X crashed, rebooted the machine, but it stays that way, before the login screen, the X crashes (corrupted image) only reset button restarts the machine.
I removed the installed driver, purged the configurations and started all over using the deb package creation procedure of the driver and also the manual script installation, but it stays the same way, removed again the driver, installed the OSS driver, it logins correctly, tested also with the restricted driver of the Ubuntu repository, it works, but no "video tearing option".
Done a new fresh install of 10.10 (no updates), installed the driver and enabled the "video tearing option", everything is ok, but if I upgrade the kernel the problem returns (if "video tearing option" is enable), i managed to overcome the video tearing option by always enabling VSYNC. 

After all this, my question is how can i reset CCC settings via command line, the aticonf --initial dont work in this case, CCC is keeping the settings in some config file (I think) that i dont know the location, i googled, but no concrete answer found, i need that because i want to do some testing, and its annoying to remove, install , reinstall the driver when the X enters this crash loop.

Thank in advance,

See ya all...

---

### Post by dino99 on 2011-07-01
So you know why & where the problem is.

sudo rm /etc/X11/xorg.conf
 Use synaptic to purge catalyst, then install fglrx-amdcccle

and check that you have some fallback drivers installed (vesa, ...)

---

### Post by pawhtiobo on 2011-07-01
Hi,

Thank you for your reply, i will do has you suggest...i also I'm going to try the CCC 11.5 instead of the 11.6, just for testing propose :), and i will post the results of the tests.

See ya

---

### Post by pawhtiobo on 2011-07-15
Hi all,

After lots of testing with all 11.x version of the FGLRX driver (HD4870), none of them work using the "Desktop tearing option" and the last released kernel, if I enable that option the system just crashes before login, after lots of install/reinstall of the driver (annoying thing)...I found a way to disable that "cursed" option (cursed for now :P), no more re-installation  of the driver....i done it this way:

- start Ubuntu in "Recovery mode"
- Drop to root command prompt option
- type this command:

**aticonfig --del-pcs-key=DDX,EnableTearFreeDesktop**

-reboot....et voilá...Ubuntu boots again normally..

About the tearing...we got 3 options:

1- No kernel update, and everything works well...better than nothing :D

2-Activate "Always VSYNC" but its not as perfect as the "tearing option"...but better than nothing...

3- Wait for a fix from the Kernel or AMD developers...

If anyone have this issue and manage to solve it, just let us know...


See ya...all

---

### Post by pawhtiobo on 2011-07-15
> **dino99 said:**
> So you know why & where the problem is.

sudo rm /etc/X11/xorg.conf
 Use synaptic to purge catalyst, then install fglrx-amdcccle

and check that you have some fallback drivers installed (vesa, ...)


Thank you for your hint, but in all my tests this didn't solved the problem :confused:, the settings of CCC are stored in some place and they persist through re-installations...weird thing...haven't found the location of these config files...

Thank you again for your help....

See ya....

---

