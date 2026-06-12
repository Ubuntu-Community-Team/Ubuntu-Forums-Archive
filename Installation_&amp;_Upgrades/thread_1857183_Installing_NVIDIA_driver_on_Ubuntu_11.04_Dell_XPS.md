---
title: "Installing NVIDIA driver on Ubuntu 11.04 Dell XPS"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by MoizBhukhiya on 2011-10-09
Hello there,

I have NVIDIA 540M chipset 2GB and I am trying to install NVIDIA driver offered by Additional Driver after the installation of Ubuntu 11.04.

It successfully installed the driver and I restarted but I never reached login screen again. So I logged in to recovery mode and reconfigure graphics and it comes back again. Then I can login successfully. But still when I open NVIDIA X Server Settings I get the following message 

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.
```when I run nvidia-config it creates the file "etc/X11/xorg.conf". But everytime I run it I get the same window..."You do not appear..."

Also when I open Additional Drivers window I see the following note:

```
This driver is activated but not currently in use.
```Also, installation of NVIDIA X Server disables Unity. When I uninstall the NVIDIA driver, everything works fine. 

If anyone could point me right direction on what is going wrong.

Any help is greatly appreciated. Thank you very much in advance.

Thanks!

---

### Post by papibe on 2011-10-09
First let's make sure you don't have [Optimus]("http://www.nvidia.com/object/optimus_technology.html") (which would mean another course of action). Could you post the result of this command?
```
$ lspci | grep VGA
```
Regards.

---

### Post by MoizBhukhiya on 2011-10-11
Hello Papibe,

Thank you for responding to my thread. 

Here is the output you asked:
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)

```

Thank you for you help.

---

### Post by papibe on 2011-10-11
Hi MoizBhukhiya, you have indeed Optimus. Which is a kind of new graphic architecture and it's not fully supported yet in Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

Then, I would research about your machine in order to see if you can disable that feature on the BIOS (the most simple solution).

I hope that helps,
Regards.

---

