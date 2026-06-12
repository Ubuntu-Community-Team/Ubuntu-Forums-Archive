---
title: "Ubuntu 10.10 works with nvidia proprietary drivers (after some effort)"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by pmp on 2010-11-06
Hello

Last night I upgraded from Ubuntu 10.04 to 10.10 64bit. Here are issues I had and how it all started to work after couple of hours struggling.

First after upgrade GDM did not start at all. I had before the upgrade Nvidia 195.36.24 that was working fine with Compiz visual effects.

I reinstalled the nvidia driver and procedure was fine. Still no gdm starting. I found following error messages
dlopen: /usr/lib/xorg/modules/drivers/nvidia-drv.so: undefined symbol: miEmptyData
failed to load /usr/lib/xorg/modules/drivers/nvidia-drv.so
failed to load module "nvidia"

Then I installed the neuveu driver as a temporary solution to see GUI starting in order to do some googling:
sudo apt-get install nvidia-current
sudo nvidia-xconfig

This installed nouveau 260.19.06 I also checked the config file that it was using nouveau, ie.

sudo nano /etc/X11/xorg.conf
    Driver         "nvidia" to     Driver         "nv"

Then I restarted the computer and vow GDM started. I could use computer but it was giving an annoying pop message of resolution definition on top of window and with nuveau compiz visual effects were not working. So I went on.

I removed the nouveau:
sudo apt-get remove --purge nvidia*


Then I fetched newest nvidia drivers from
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

and installed the new driver at the download directory:
sudo sh ./NVIDIA-Linux-x86_64-260.19.12.run

Installation and nvidia own configuration support again seemed to go fine as with 195.36.24. Then I restarted and gdm again did not come up. The computer was freezing at start with a black window. I pressed ctrl-alt-F2 and logged in via cli. I changed the following

sudo nano /etc/X11/xorg.conf
    Driver         "nvidia" to     Driver         "nv"

I did not touch anything else, did not install neuveau.

I restarted the computer and GDM gui started as when the nouveau installed. Annoying pop window telling about resolution not set during and some time after login. Visual effects not working. Somehow computer seemed to be using nv, nouveau, driver even if it was installed.

Then I run following reconfiguration steps what I think were crucial additions to the NVIDIAs own installations package

1. sudo dpkg-reconfigure xserver-xorg

I checked the configuration file
sudo nano /etc/X11/xorg.conf
and found that nouveau driver was still used.
Driver         "nv" 

I found this would not work better and I run
2. sudo nvidia-xconfig

again I checked the result:

sudo nano /etc/X11/xorg.conf
now driver definition was changed to nvidia
    Driver         "nvidia

I rebooted the computer and vow. It started nicely. Gui started up without any messages. I could start the extra visual effects etc.

So my ubuntu 10.10 is working now fine with nvidia 260.19.12 64 bit drivers with visual effects. What was the odd thing that the nvidia installation package's xorg.conf configuration support did not lead to right configuration as I had to do the 1&2 above.

If someone can get their issue solved with above explanation or if someone can explain the root cause then good.

Otherwise I have not had issues with ubuntu 10.10
Cheers:guitar:

---

