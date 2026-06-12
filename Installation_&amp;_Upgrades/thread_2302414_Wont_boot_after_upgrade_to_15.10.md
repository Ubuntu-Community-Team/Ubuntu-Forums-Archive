---
title: "Wont boot after upgrade to 15.10"
date: 2015-11-10
forum: Installation &amp; Upgrades
---

### Post by Lucetius on 2015-11-10
Evening all, I'm having a bit of trouble booting up my system after updating to the new OS.

Everything seemed to install as it should although at one point I was asked if I wanted to keep or replace a previous config file, I chose replace, which may have been the wrong thing to do.

Anyhow, now when I try to boot the computer it gets stuck at the purple "Ubuntu" loading screen. The dots will freeze and turn orange.

I can boot using the old 3 series kernel no problems, however it will freeze every time if I try and boot with the new Kernel.

Any help would be appreciated :)

---

### Post by grahammechanical on 2015-11-10
Load using the 3.19 kernel and then try a different video driver from Additional Drivers. Did you revert to using the open source video driver prior to running the upgrade to 15.10. Do you have an AMD video card?

> AMD's **fglrx** driver does not work with the current kernel ([1493888]("https://bugs.launchpad.net/bugs/1493888")).  It is warmly recommended to uninstall the fglrx driver before upgrading  to Ubuntu 15.10. The open source "radeon" driver can be used as a  temporary replacement until a fix is available.

[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes)

Regards.

---

### Post by Lucetius on 2015-11-10
Yes I have an AMD card and no I did not revert back to the open source driver before I upgraded.

I have tried reverting to the open source driver and then rebooting, but it still wont boot with the new kernel.

---

### Post by ajgreeny on 2015-11-10
At the login screen, if you get that far, try using Ctrl+Alt+F1 t6o get a command-line.  Login there with your username and password, then see if you can simulate removal of the fglrx driver with ```
sudo apt-get -s remove fglrx*
```
If the simulation runs OK remove the **-s** switch from the command and run it again.

Now reboot to see if you get a GUI.

It is a long time since I had an AMD graphic card, and I am no longer fully aware of the problems of using them, nor how well the Additional Driver utility works for them, but my suggestion will make sure the driver is uninstalled.

If this does not work you may need to use the older kernel as default for the time being which you can do by editing the 
GRUB_DEFAULT=
line in file /etc/default/grub.  See [https://help.ubuntu.com/community/Grub2/Submenus#Setting_a_Submenu_entry_as_the_default](https://help.ubuntu.com/community/Grub2/Submenus#Setting_a_Submenu_entry_as_the_default)

---

### Post by Lucetius on 2015-11-10
Doesn't get to the login screen I'm afraid

I will just use the older kernel for now as it works fine... hopefully a fix will come along at some point

Thanks for your help :)

---

