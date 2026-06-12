---
title: "No graphics after Nvidia upgrade"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by Scootm on 2011-05-25
There's no login screen and I can't get to a tty. I have tried editing xorg with the backup, but the name of the driver is the same.

Is there anyway to roll back the driver from a livecd?

---

### Post by cbowman57 on 2011-05-25
> **Scootm said:**
> There's no login screen and I can't get to a tty. I have tried editing xorg with the backup, but the name of the driver is the same.

Is there anyway to roll back the driver from a livecd?

Maybe, but from the recovery terminal (from the grub menu)

**sudo apt-get purge nvidia-current nvidia-common** that should get you back to a desktop where you can try a different one.  The experimental gallium drivers are pretty good if the proprietary drivers give you a problem.

---

### Post by Scootm on 2011-05-25
> **cbowman57 said:**
> Maybe, but from the recovery terminal (from the grub menu)

**sudo apt-get purge nvidia-current nvidia-common** that should get you back to a desktop where you can try a different one.  The experimental gallium drivers are pretty good if the proprietary drivers give you a problem.

Thank you, but I can't get into grub. I tried following the sticky that pretty much covers this subject, but I am getting an error any time I apt-get anything. I first noticed this when I tried to reinstall grub.

 ```
root@ubuntu:/etc/X11# sudo apt-get purge nvidia-current nvidia-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-session : Depends: gnome-session-common (= 3.0.1-0ubuntu1~build2) but 3.0.2-0ubuntu1~natty1 is to be installed
 nvidia-185-libvdpau : Depends: nvidia-current but it is not going to be installed
 ubuntu-desktop : Depends: nvidia-common but it is not going to be installed
                  Recommends: evolution-exchange but it is not going to be installed
                  Recommends: gnome-accessibility-themes but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```Anyway, that's what it says...and apt-get -f install only brings up 
```
dpkg: error processing /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu1~natty1_all.deb (--unpack):
 trying to overwrite '/usr/share/xsessions/gnome-shell.desktop', which is also in package gnome-shell 3.0.1-0ubuntu1~build1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu1~natty1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by cbowman57 on 2011-05-25
Ok, how are you managing to get a terminal to apt-get anything?

I think I have a solution that will fix it but it would require adding a couple extra ppa's. Then run update & upgrade again.

I have to get to some errands and will likely not be back on for a few hours, so if you decide to take the risk you can add:

sudo apt-add-repository ppa:ricotz/testing

---

### Post by Scootm on 2011-05-25
I am using a live cd and chroot

---

### Post by cbowman57 on 2011-05-25
Ah, that makes it difficult.

If you have another method of reaching the internet & can create a CD or USB you might try repairing your grub using Rescatux.

---

### Post by Scootm on 2011-05-25
thanks, i'll try it out

---

### Post by Scootm on 2011-05-25
Update: 
I can remove xorg.conf and boot into the system. Of course, it looks wonky, but I will see what I can do from there.

---

### Post by Scootm on 2011-05-25
So I am still stuck. I followed the sticky and am still getting a few errors. Here are some of them (kind of in the order that they appear):

Directly after logging on - "Could not apply the stored configuration for monitors"

Trying to use nvidia-settings - "You do not appear to be using Nvidia X Driver. Please edit x config file and restart x server"

After configuring and trying to start X again - "Failed to initialize GLX (Compatible NVIDIA X driver not found" 

And somewhere along the way - "Failed to acquire org.gnome.DisplayManager"

---

### Post by Scootm on 2011-05-25
I think I have found THE error. It goes something like this:

NVidia kernel module has version 270.41.19 but this Nvidia driver has version 270.41.06. Please make sure that the kernel module and all Nvidia driver components have same version.

I'm currently searching for a fix. If anybody can help, please do. Thanks.

---

