---
title: "Ubuntu 13.10 - xwindow problem with network manager"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2014-02-09
Folks,

In our setup, we install Ubuntu without any UI component initially and then add openbox to it. Starting version 12.x, I had created a list of steps for installing Ubuntu for our purpose. It worked fine until 13.04 but now I am running into a problem in 13.10.
 
After installing base Ubuntu and Openbox, and testing to make sure everything works as expected, the next step is to install network-manager.

$ sudo apt-get install network-manager
$ sudo vi /etc/network/interfaces


Comment out the lines: 
auto em1
iface em1 inet dhcp


$ sudo rm /etc/xdg/autostart/nm-applet.desktop
$ sudo reboot

After this change, when xwindow is started using startx, it goes into a la la land. The error in .xsession-errors is "CRITICAL: We failed but the fail whale is dead.."


Fortunately, I had cloned an image before installing network-manager. So I am back to a working environment. However, I do need to install network manager for our needs. I am wondering if anyone has any idea on what could be going wrong.

Thank you in advance for your help.

Regards,
Peter

---

### Post by PeterTaps on 2014-03-05
Ok. I tried creating a new minimal Ubuntu image + openbox. However, NetworkManager still has problems. I decided to let go NetworkManager. Built a new machine and installed "wicd" instead. Works like a charm.

If you are using Ubuntu minimal + openbox, my recommendation would be to go with wicd instead of NetworkManager.

Regards,
Peter

---

