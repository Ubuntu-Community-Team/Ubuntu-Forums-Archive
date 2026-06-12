---
title: "[SOLVED] Nvidia driver"
date: 2008-07-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chrismine on 2008-07-14
Todays updates:
Cannot install the new nvida-glx-177 version 6 driver.

This is the error:
E: /var/cache/apt/archives/nvidia-glx-177_177.13-0ubuntu6_i386.deb: subprocess pre-installation script returned error exit status 2

It is probably my own doing because I installed the driver from Nvidia's website.

What I tried to fix the problem:
1.Uninstall the NVIDIA driver by doing sudo sh NVIDIA* --uninstall - it reported a successful uninstall.
2. Tried to force the install from Synaptic
3. Tried to force from the terminal with sudo apt-get --force-yes install <package_name> and sudo dpkg --force-all -i <package_name>
4. Run sudo dpkg-reconfigure xserver-xorg -phigh to get an acceptable screen resolution.

I am stuck now - is there a workaround, does somebody else have the same problem or is it a bug?

Thanks guys!

---

### Post by chrismine on 2008-07-21
I filed a bug: [https://bugs.launchpad.net/bugs/250486](https://bugs.launchpad.net/bugs/250486)

---

