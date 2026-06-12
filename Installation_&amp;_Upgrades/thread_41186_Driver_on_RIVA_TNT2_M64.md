---
title: "Driver on RIVA TNT2 M64"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by titou on 2005-06-12
I am actually trying to make some kind of media center with an old PIII 800, 130 M RAM and a Riva TNT2 M64 GPU. 

I installed ubuntu with XFCE4...

When I activate nvidia driver "nvidia" in xorg.conf, the Nvidia splash appears and I get to gdm, there and after, the computer gets slow every time I move the mouse (CPU going 100%). and xorg crashes after 2 or 3 minutes ... 

xorg works fine with driver "nv" but I need the 3D acceleration ...

I tried to install an old nvidia driver but it tells me he doesn't have kernel source ... (2.6.10-5) and I cant find those, even with apt !

so if anybody can help, thx in advance ... ](*,)

---

### Post by skoal on 2005-06-12
I have an old Riva TNT PCI card on a Win box that dual boots to RedHat 7.3.  I believe I had similiar issues until I found the right Nvidia driver version.  It currently is using the 6629 driver without issues, but I believe I even had an older version on that at one time.

\\//_

---

### Post by titou on 2005-06-12
how do I install an old nvidia driver then ? is there a guide ?? :???:

---

### Post by skoal on 2005-06-12
Just go to the nvidia website and download from their archives: [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

* 1. Remove all instances of any Ubuntu nvidia packages from your system.
2. Install the kernel headers for your particular kernel version (probably 2.6.10)
3. You will need to make a runlevel without X, so you can init or reboot into it for the driver install.
4. In that non-X session, login as root or use sudo and "sh NVIDIA-Linux-x86-1.0-6629-pkg1.run"
5. reboot or init into X session (or runlevel 2).

That will build the nvidia driver and get you all setup.  You can pick andy driver version before 6629, just download them from that archive.

\\//_

---

### Post by titou on 2005-06-12
thanks but when I try to install nvidia manually, I get the error :

No precompiled kernel interface was found to match your kernel ...

then I get the error : Unable to load nvidia.ko, this is most likely because the kernel module was built using the wrong kernel version...

I have apt linux-headers-2.6.10 and linux-kernel-source-2.6.10, its in /usr/src/ 

...

---

### Post by skoal on 2005-06-12
You only need the kernel headers to build the Nvidia driver.  Are you sure you followed step 1?  The one with the asterisk by it.  If you were using the Ubuntu packages before trying to use the Nvidia installer, get rid of all those first.

\\//_

---

### Post by titou on 2005-06-17
I have removed all nvidia packages  and it's still not working ... to get to runlevel 2, I did a kill gdm, I have installed the kernel headers, and the nvidia-installer always tell me I don't have precompiled interfaces and then that I don't have kernel sources !

I don't understand because they are in /usr/src ! 

I also have a warning about rivaFB module ...

I think I am going to change the graphic card  ;-)

---

