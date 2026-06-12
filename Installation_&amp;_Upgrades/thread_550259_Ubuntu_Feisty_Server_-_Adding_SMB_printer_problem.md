---
title: "Ubuntu Feisty Server - Adding SMB printer problem"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by rocketero on 2007-09-13
I just installed ubuntu feisty (7.04) server from a single CD wich installs just the basic web and mysql servers and nothing else living you just a black screen with a command prompt. I have been adding upgrades and installed kde, kdm, xserver and other utilities. 

Now I want to install a SMB shared printer from one of my Windows machines, but when I try to add the printer through the add-printer-wizard I get the window with tne SMB shared printer radio button dimmed as in the pincture included in this post, how can I fix this ??

Any help would be greatly appreciated.
rocketero

---

### Post by rocketero on 2007-09-14
Before this thread gets burried and dead, let me give some more  info on this issue:

the system in matters is UBUNTU FEISTY 7.04, UBUNTU EDGY 6.10. as virutal machines set with vmware, the host OS is Windows XP,  both show the same problem with setting or adding a windows SMB shared printer throught the KDE-add-printer wizard.

the radio button for "SMB shared printer (windows)"  is dimmed, not selectable as shown in the picture in the first post.

NOTE THIS:    I have in the same host other guests Linux versions (virtual machines) like SUSE10.1, Knoppix, RedHat. All of these virtual machines use the windows SMB shared printer WITH NOT PROBLEM AT ALL. The shared printer is located in another computer in the network running Microsoft WindowsXP

It's only the UBUNTU virtual machines that present this symtom, and till now I have not been able to find out why this is occurring.

I have installed the following packages:

sudo apt-get install cuypsys

sudo apt-get install samba

I have checked that both cupsd and samba server are up and running.

One curious thing thou is that when I type [http://localhost:631](http://localhost:631) shows an UNAVAILABLE page.
and after installing WEBMIN and going to the printers session also says cups server is not running but I thing is due to the location of the configuration file that webmin doesn't find that indeed cups deamon is running otherwise the command: /etc/init.d/cupsys status wouldn't say so.

So please jump into this and let's have a solution to this mistery.

---

### Post by Pumalite on 2007-09-14
Here is the collection I came up with:

[http://ubuntuforums.org/archive/index.php/t-59205.html](http://ubuntuforums.org/archive/index.php/t-59205.html)

[https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/58403](https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/58403)

[https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/8125](https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/8125)

[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/8124](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/8124)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg431729.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg431729.html)

Hope it helps.

---

### Post by rocketero on 2007-09-14
thanks Pumalite for the guidance, even that not solution was presentend on those links it was very intresting reading.

The solution so far was as follows:

I installed the GNOME GDM manager to see how different was adding a printer from there, and voila, the SMB shared printer for Windows is listed and available.

So I think I should report this bug as with KDE the SMB shared printer radio button is dimmed.

Now the problem that I have is that the printer I need to add is not listed in the add-printer wizard with GNOME (HP Photosmart C3100), althoug most other linux distributions I have installed come with this driver (Fedora 7, Knoppix 5.1.1 , RedHat 5EL, SUSE 10.2), but Ubuntu doesn't. 

is there a package to install additional print drivers with ubuntu?

meantime I try to find the linux driver for HP Photosmart C3100

---

### Post by Pumalite on 2007-09-14
Hope this helps:

[https://blueprints.launchpad.net/ubuntu/+spec/printerdriverautodownload](https://blueprints.launchpad.net/ubuntu/+spec/printerdriverautodownload)

---

