---
title: "proprietary graphic driver"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by telescopic on 2011-02-01
I use 10.04 Xubuntu, 

1)I wonder where is the file /etc/X11/xorg.config 
I have in the directory:

app-defaults             xinit                          Xreset.d
cursors                  xkb                            Xresources
default-display-manager  xorg.conf-backup-101225181054  Xsession
fonts                    xorg.conf-backup-101227145410  Xsession.d
rgb.txt                  xorg.conf.failsafe             Xsession.options
X                        Xreset                         Xwrapper.config

but no file has the name xorg.config

b)I have problem with graphic driver(cannot install GeForce proprietary driver). So, currently using a generic graphic driver.

I tried Application>System>Hardware Drivers, but the Nvidia driver doesn't show up. I thought i could change the line for driver in the xorg.config file, then reboot and call up Application>System>Hardware Drivers in order to detect a NVidia proprietary driver. But it does not work.

Any help, please.

---

### Post by tommcd on 2011-02-01
> **telescopic said:**
> 
1)I wonder where is the file /etc/X11/xorg.config 

The name of the file is */etc/X11/xorg.conf*, not xorg.config.
Newer versions of Xorg like the one in Ubuntu 10.04 use kernel mode setting to enable graphics and do not need an xorg.conf file.
> **telescopic said:**
> 
I have problem with graphic driver(cannot install GeForce proprietary driver). So, currently using a generic graphic driver.

I tried Application>System>Hardware Drivers, but the Nvidia driver doesn't show up. ...
What nvidia card do you have? If you have a Gforce 6 series or newer card, you can just install the *nvidia-current* driver from the Ubuntu repos. Also install *mesa-utils* and *nvidia-settings*. Then run *sudo nvidia-xconfig* to enable the driver. Then reboot and you should be good

---

### Post by telescopic on 2011-02-01
I have Geforce 6150, I use Synaptic and search for files nvidia-current, nvidia-current-dev, mesa-utils. and installs them.

Now, I type in terminal, sudo nvidia-xconfig...

elvin@elvin-laptop:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found

---

### Post by tommcd on 2011-02-02
> **telescopic said:**
>  I use Synaptic and search for files nvidia-current, nvidia-current-dev, mesa-utils. and installs them.
Also install *nvidia-settings* as I said in my last post.
> **telescopic said:**
> 
Now, I type in terminal, sudo nvidia-xconfig...
sudo: nvidia-xconfig: command not found
I don't know why some people have this problem. I have seen it reported before, but it has never happened to me. Try rebooting and then stop X with:
```
sudo service gdm stop
```
Then see if you can run *sudo nvidia-xconfig*. Then restart X with:
```
sudo service gdm start
``` Or just reboot with *sudo reboot*. And see if the driver is enabled.

Did installing the nvidia driver create an xorg.conf file? If so, then you could just try changing the driver from "nv" to "nvidia" to enable the driver.

---

