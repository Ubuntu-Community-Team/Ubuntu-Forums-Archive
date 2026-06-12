---
title: "Held Back Updates"
date: 2008-07-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by awam66 on 2008-07-11
I have 43 held back updates in Update Manager all to do with xserver. Any news of when they will be available?

---

### Post by caryb on 2008-07-11
If you do a dist-upgrade you will pickup the changes.


Cary

---

### Post by vhaarr on 2008-07-11
But don't do it, since X is broken currently.

---

### Post by psyke83 on 2008-07-11
> **vhaarr said:**
> But don't do it, since X is broken currently.

For whom? It works fine here.

> **awam66 said:**
> I have 43 held back updates in Update Manager all to do with xserver. Any news of when they will be available?

Run "sudo apt-get dist-upgrade" in the terminal, but *do not* allow it to run. Check the output to see if it will remove any packages. If it will not remove anything, allow the upgrade. If it wants to remove packages, cancel the operation and paste the terminal output here.

---

### Post by cecilpierce on 2008-07-11
The following packages will be REMOVED:
  nvidia-glx-new xserver-xorg-video-cyrix xserver-xorg-video-imstt
  xserver-xorg-video-newport xserver-xorg-video-via
The following NEW packages will be installed:
  libdns43 libgnutls26 libpciaccess0 libxcb-render-util0 libxcb-render0
The following packages will be upgraded:
  bind9-host dnsutils libbind9-40 libcairo2 libisccfg40 libldap-2.4-2
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-dummy xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nsc
  xserver-xorg-video-nv xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-radeonhd
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
50 upgraded, 5 newly installed, 5 to remove and 0 not upgraded.
Need to get 8160kB of archives.
After this operation, 19.8MB disk space will be freed.
Do you want to continue [Y/n]? 

Should I do it ?

---

### Post by Kevbert on 2008-07-11
I've got 57 held back updates (Kubuntu 64 bit).  Maybe some of them will be used tomorrow when Alpha2 is released.

---

### Post by Seisen on 2008-07-11
I only have one package being held back. :(

---

### Post by psyke83 on 2008-07-11
> **cecilpierce said:**
> The following packages will be REMOVED:
  nvidia-glx-new xserver-xorg-video-cyrix xserver-xorg-video-imstt
  xserver-xorg-video-newport xserver-xorg-video-via
The following NEW packages will be installed:
  libdns43 libgnutls26 libpciaccess0 libxcb-render-util0 libxcb-render0
The following packages will be upgraded:
  bind9-host dnsutils libbind9-40 libcairo2 libisccfg40 libldap-2.4-2
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-dummy xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nsc
  xserver-xorg-video-nv xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-radeonhd
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-vmware
  xserver-xorg-video-voodoo
50 upgraded, 5 newly installed, 5 to remove and 0 not upgraded.
Need to get 8160kB of archives.
After this operation, 19.8MB disk space will be freed.
Do you want to continue [Y/n]? 

Should I do it ?

No. You could use the Nvidia PPA mentioned in this forum a few days ago, but you're probably better off waiting until the new nvidia packages hit the official repositories.

---

### Post by vhaarr on 2008-07-11
I tried updating Xorg a few days ago when the packages first hit, then rebooted and got lots of errors with stack traces including libgdk-x11 and such. I hopped on #ubuntu+1 on IRC and the topic said "X is broken".

I downgraded all my xorg packages and X worked again.

Xorg packages have NOT been updated since then.
Which leads me to conclude that if I update xorg now, it will still be broken.

---

### Post by psyke83 on 2008-07-11
> **vhaarr said:**
> I tried updating Xorg a few days ago when the packages first hit, then rebooted and got lots of errors with stack traces including libgdk-x11 and such. I hopped on #ubuntu+1 on IRC and the topic said "X is broken".

I downgraded all my xorg packages and X worked again.

Xorg packages have NOT been updated since then.
Which leads me to conclude that if I update xorg now, it will still be broken.

You probably updated xserver-xorg-core before the updated input/video driver packages were ready. Almost all the drivers are working now (except nvidia, fglrx, and possibly "cyrix" and "imstt" cards, although those could be obsolete).

Edit: I see the new nvidia packages are in the repository now.

---

### Post by plun on 2008-07-11
> **vhaarr said:**
> 
I downgraded all my xorg packages and X worked again.

Xorg packages have NOT been updated since then.
Which leads me to conclude that if I update xorg now, it will still be broken.

Yup I can confirm this because I downgraded to Hardys Xorg to get
a working X.  Then all packages was fixed and a dist-upgrade to Xorg 7.4 went fine.

I must also use recovery mode because the tty terminal was and is broken, Ctrl-Alt-F1  to  F6  

I am rather sure that a dist-upgrade works now without any trouble directly from Intrepids Xorg 7.1 > 7.4.

(se earlier posted dist-upgrade output within this thread)

------------------

Can also someone else confirm if a tty terminal works or not
in normal mode with Xorg 7.4 ?

---

### Post by ccw on 2008-07-11
> **psyke83 said:**
> 
Run "sudo apt-get dist-upgrade" in the terminal, but *do not* allow it to run. Check the output to see if it will remove any packages. If it will not remove anything, allow the upgrade. If it wants to remove packages, cancel the operation and paste the terminal output here.

sudo apt-get -s dist-upgrade

       ```
-s, --simulate, --just-print, --dry-run, --recon, --no-act
           No action; perform a simulation of events that would occur but do
           not actually change the system. Configuration Item:
           APT::Get::Simulate.
```

---

### Post by awam66 on 2008-07-11
OK,
I think I'll wait.

---

### Post by caryb on 2008-07-11
From what I can see is that the new  drivers are dependent on the new xorg being installed, once that is installed the rest will install. I have no held back packages at all I had what you have but only till I installed the new xorg.


Cary

---

### Post by Gina on 2008-07-12
I ran the update and got the new stuff installed but lost nVidia driver and display went back to low res.  I'm currently downloading the Alpha 2 and will install that rather than messing about with the updated version.  I want to reinstall stuff anyway to rationalise my AMD64 desktop HD.

---

### Post by caryb on 2008-07-12
What Nvidia card are you running Gina:confused:


Cary

---

### Post by Gina on 2008-07-12
> **caryb said:**
> What Nvidia card are you running Gina:confused:


Cary Onboard Nvidia® Geforce 6100GS graphics supporting up to 256MB (quoted from mobo spec).

---

### Post by plun on 2008-07-12
> **Gina said:**
> Onboard Nvidia® Geforce 6100GS graphics supporting up to 256MB (quoted from mobo spec).

Gina..

Please take a look at this package

[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)

Also install nvidia-settings   (run from terminal if you want to change settings)

sudo nvidia-xconfig  is probably also needed after a install.


Jockey is "out of order" for driver installs so it must be a manual
procedure as I sees it....:)

---

### Post by Kevbert on 2008-07-12
Just performed a
```
sudo apt-get dist-upgrade
```
and all 63 held-back packages have gone.  My nVidia Geforce 7600GS is working fine.

---

### Post by plun on 2008-07-12
> **plun said:**
> Gina..



sudo nvidia-xconfig  is probably also needed after a install.


Jockey is "out of order" for driver installs so it must be a manual
procedure as I sees it....:)

**sudo nvidia-xconfig**  is NOT needed....


It brakes the xserver atleast for me.

To get 3D rendering I must have this within my /etc/X11/xorg.conf

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
```

](*,)

---

### Post by ronacc on 2008-07-12
I'll confirm what plun said , the upgrade does not pull in the Nvidia driver you have to install that after the upgrade ( which ever one is correct for your card) . then you can enable the driver .
edit I did not need to alter my xorg.conf been using the same one since fiesty . good idea to check it though low graphics sometimes trashes it.

---

### Post by Gina on 2008-07-12
> **plun said:**
> Gina..

Please take a look at this package

[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)

Also install nvidia-settings   (run from terminal if you want to change settings)

sudo nvidia-xconfig  is probably also needed after a install.


Jockey is "out of order" for driver installs so it must be a manual
procedure as I sees it....:)Thank you - looks useful :) I hope to get back to this in the next day or two.

---

### Post by plun on 2008-07-12
> **Gina said:**
> Thank you - looks useful :) I hope to get back to this in the next day or two.

Well... don't do a nvidia-xconfig... it writes rubbish for xorg..:)

tseliot still works with the drivers and I managed
to get Jockey working with todays update in his PPA.

But I went back to my patched driver, its "stable"  ....:)

---

