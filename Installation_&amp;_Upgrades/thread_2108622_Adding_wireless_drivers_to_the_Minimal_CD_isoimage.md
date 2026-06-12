---
title: "Adding wireless drivers to the Minimal CD iso/image before burning to CD"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by purity89 on 2013-01-25
I was wondering if it's possible to add wireless drivers to the Ubuntu [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD"), before burning it to a CD and installing it..?

I only have Windows 7 installed now, and I realize it's probably difficult to configure the Minimal CD from here. But maybe if I boot a Live CD, and do it from a linux enviroment?

I have a desktop PC that only has wireless access to the internet, so I need the wireless drivers. 

The reason for using the Minimal CD is that I only want to install the most basic functions of Ubuntu, since I'm purely using it as a C++ and LaTeX development enviroment. Most likely I will also use xubuntu-desktop instead of the default ubuntu-desktop.

**SOLUTION:** The native Linux drivers, which I think are included in the kernel, works for the Wifi USB dongle I'm using (a D-Link DWL G122) ([source]("http://www.toysdesk.com/hardware/d-link-dwl-g122-and-linux/")). So I just burned the Minimal CD, booted it, and got the option of connecting to the internet via the USB dongle during installation, which worked great for my secured Wifi network.

---

### Post by purity89 on 2013-01-25
I think I can solve this problem by just installing Ubuntu with the Minimal CD, and then use the method mentioned [here]("http://askubuntu.com/a/1005") to install packages from an offline source afterwards. Hopefully this will let me connect to the internet, so I can download the other stuff I want.

But does anyone know which packages (and dependencies) that contain the wireless drivers that are included in a standard Ubuntu Live CD? My wireless USB adapter works fine when booting from a Ubuntu Live CD, so I was thinking I could just download them from [Launchpad]("https://launchpad.net/ubuntu/quantal") or [here]("http://packages.ubuntu.com/"), and then install them using "sudo dpkg -i *.deb".

EDIT: Apparently my Wifi USB dongle has native Linux drivers ([source]("http://www.toysdesk.com/hardware/d-link-dwl-g122-and-linux/")), so now I only need to figure out which packages that has these drivers. Or are they perhaps included in the kernel? I have no idea what I'm talking about here though, so I might be completely wrong.

---

