---
title: "NVIDIA drivers not working after 11.04 Update. Why can I only see terminal?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Sixthlaw on 2011-04-28
Hey guys.

Tonight I upgraded to 11.04. Once I had finished the upgrade, I restarted my computer as it told me too. When I got past the ubuntu 11.04 (purple background orange dots), it simply went to the terminal and asked me to log in. I tried to restart the X server with "sudo service gdm restart" but no display popped up. I happened to have a few NVIDIA drivers in my downloads file also so I gave these a try, but the "install script" failed.

After all this I booted Ubuntu in graphic failsafe mode. I then decided to see what would happen if I removed the proprietary driver. Upon doing this and rebooting my Ubuntu booted into graphical mode "yay!". So without the Nvidia drivers I can finally see something other than terminal, but, I need those NVIDIA drivers for my work. So what can I do? I have tried installing the new NVIDIA linux drivers from the NVIDIA website, and have tried Installing the recommended driver via "additional drivers", but both have resulted in my being stuck in terminal.

If you can help or give me some advice PLEASE DO! I am really in a very bad situation...

---

### Post by patsimon12 on 2011-04-29
I think it's something to do with incompatibility with the kernal that comes with 11.04 and the nvidia driver. You can revert back to the non-nvidia drivers by doing the following.

cd /etc/X11
sudo mv xorg.conf xorg.conf_bu
sudo mv xorg.conf_failsafe xorg.conf  

NOTE - the xorg.conf_failsafe file MAY be called something different on you PC.

Then you can restart X (Ctrl-Alt-Backspace) or simply reboot.

This will give you a window manager but NOT with the nvidia drivers.

---

### Post by borner on 2011-04-30
I'm having exactly the same issue, my system won't boot when the nvidia drivers are installed. Graphics card is a GT220. Can we expect a fix for this or is it better for me to reinstall 10.10?

---

### Post by ebbr.bugs on 2011-04-30
Your problem is that you have the nvidia driver installed as a deb package but not the driver itself, for which you need the kernel headers.
Install the package kernel-headers-blabla corresponding to your current kernel (see uname -a). Then do install --reinstall of the nvidia package or install --reinstall of the linux kernel - this will force the creation of the nvidia kernel module. Reboot.

Those commands:
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae

---

### Post by dino99 on 2011-04-30
dkms package needed too (see synaptic)

---

### Post by borner on 2011-04-30
> **ebbr.bugs said:**
> Your problem is that you have the nvidia driver installed as a deb package but not the driver itself, for which you need the kernel headers.
Install the package kernel-headers-blabla corresponding to your current kernel (see uname -a). Then do install --reinstall of the nvidia package or install --reinstall of the linux kernel - this will force the creation of the nvidia kernel module. Reboot.

Those commands:
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae

I used those two commands to update and my system will now not boot at all? Even to recovery mode? Why is all of this needed? It was fine in 10.10?

---

### Post by lcnrj on 2011-05-03
Try:
 sudo gedit /etc/modules
 and add a line containing "nvidia"

---

### Post by pearlbear on 2011-05-03
> **ebbr.bugs said:**
> Your problem is that you have the nvidia driver installed as a deb package but not the driver itself, for which you need the kernel headers.
Install the package kernel-headers-blabla corresponding to your current kernel (see uname -a). Then do install --reinstall of the nvidia package or install --reinstall of the linux kernel - this will force the creation of the nvidia kernel module. Reboot.

Those commands:
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae

This worked great for me, with the addition of doing a reinstall of the nvidia-common package.

---

### Post by artoonie on 2011-05-15
> **ebbr.bugs said:**
> Your problem is that you have the nvidia  driver installed as a deb package but not the driver itself, for which  you need the kernel headers.
Install the package kernel-headers-blabla corresponding to your current  kernel (see uname -a). Then do install --reinstall of the nvidia package  or install --reinstall of the linux kernel - this will force the  creation of the nvidia kernel module. Reboot.

Those commands:
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae


Dearest Bug,
Thank you so much. I've spent so many hours trying to get this to work. I wish this thread would find its way to Google soon.

Crawl on, my little friend.

---

### Post by beast2k on 2011-07-08
> **ebbr.bugs said:**
> Your problem is that you have the nvidia driver installed as a deb package but not the driver itself, for which you need the kernel headers.
Install the package kernel-headers-blabla corresponding to your current kernel (see uname -a). Then do install --reinstall of the nvidia package or install --reinstall of the linux kernel - this will force the creation of the nvidia kernel module. Reboot.

Those commands:
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae

Puting graphics drivers into Ubuntu was a no brainer last verson and has been real user friendly for a long time . What is going on all of a sudden. As if unity wasn't enough.

---

### Post by MAFoElffen on 2011-07-08
> **ebbr.bugs said:**
> Your problem is that you have the nvidia driver installed as a deb package but not the driver itself, for which you need the kernel headers.
Install the package kernel-headers-blabla corresponding to your current kernel (see uname -a). Then do install --reinstall of the nvidia package or install --reinstall of the linux kernel - this will force the creation of the nvidia kernel module. Reboot.

Those commands:
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae
Just for refrence to others... This will work if you are on 32bit, looking to use that version of kernel...  For a more generic commndline that will work for what your current installed kernel, instead try:
```

sudo apt-get install --reinstall linux-headers-'uname -r'
sudo apt-get install --reinstall linux-image-'uname -r'

```If you get an error on the --reinstall option flag, try using aptitude instead of apt-get.

The first command especially helps when trying to install new drivers under Natty.

---

