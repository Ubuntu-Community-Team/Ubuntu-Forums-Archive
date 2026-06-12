---
title: "Problem installing nvidia driver"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by ubunt12 on 2010-11-13
Hi, im trying to install the NVIDIA-Linux-x86-100.14.11-pkg1.run driver with the command:  install NVIDIA-Linux-x86-100.14.11-pkg1.run nvidia  then:  ./nvidia  and the output:     WARNING: The NVIDIA GeForce4 MX 420 GPU installed in this system is supported through the NVIDIA 1.0-96xx legacy Linux graphics            drivers.  Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more information.  The 100.14.11 NVIDIA Linux            graphics driver will ignore this GPU.                                                                   OK  then when i press enter:     WARNING: You do not appear to have an NVIDIA GPU supported by the 100.14.11 NVIDIA Linux graphics driver installed in this            system.  For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the            Linux driver download page at [www.nvidia.com](www.nvidia.com).                                                                   OK  then enter again:     ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section          INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).                                                                   OK  again:     ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on          fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).                                                                   OK  can anyone help me to install this driver pls?  Thanks in advance.

---

### Post by ubunt12 on 2010-11-13
sorry, it didn't look like that when i wrote it.

---

### Post by wojox on 2010-11-13
Why can't you go into Hardware Drivers and activate your driver there?

---

### Post by ubunt12 on 2010-11-13
nothing comes up.

---

### Post by ubunt12 on 2010-11-13
is there a command to see what driver is currently installed on my system??

---

### Post by wojox on 2010-11-13
```
lspci | grep VGA
```

---

### Post by wojox on 2010-11-13
> **ubunt12 said:**
> nothing comes up.

Try:

```
sudo apt-get update; sudo apt-get upgrade
```

Then look again.

---

### Post by ubunt12 on 2010-11-13
Thanks, ive updated and upgraded and the command:

lspci | grep VGA shows:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

---

### Post by ubunt12 on 2010-11-13
is that my graphics card or driver??

---

### Post by wojox on 2010-11-13
> **ubunt12 said:**
> Thanks, ive updated and upgraded and the command:

lspci | grep VGA shows:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

That's your card. Nothing showed up in Hardware Drivers?

---

