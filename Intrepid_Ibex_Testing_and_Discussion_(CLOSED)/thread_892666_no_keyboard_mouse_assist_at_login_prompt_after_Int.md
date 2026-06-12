---
title: "no keyboard mouse assist at login prompt after Intrepid upgrade"
date: 2008-08-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by normie on 2008-08-17
Hello All,

I upgrade my Hardy to Intrepid. Now I get the login screen but mouse and keyboard does not respond. I can log in via command line (alt-F1). Also I can login via VNC/NX with issue. But the mouse/keyboard does not respond at the login prompt.
I had a similar issue when upgraded from Dapper to Hardy on a Xubuntu box.
Anyone having or had similar and can assist please post, thx.

---

### Post by 1fl on 2008-08-17
Really cant assist, Having the same issue running a usb kvm. Get to the login screen and keyboard, mouse does not work. Got to the last 45 seconds and hardy froze during the install process. installing the nvidia drivers.

---

### Post by normie on 2008-08-22
:confused:
no takers? I guess I am running solo on this one. Was trying to avoid a re-install.
Still open to any ideas out there.:popcorn:

---

### Post by macabro22 on 2008-10-19
bump

---

### Post by autocrosser on 2008-10-19
Take a look at my Hal .fdi files info--looks like you have the same problem that I did----

[http://ubuntuforums.org/showthread.php?t=948154](http://ubuntuforums.org/showthread.php?t=948154)

---

### Post by tielie on 2008-10-19
I fixed it by editing my xorg.conff file

but when i read your solution about hal i just say WHAT THE **** no no no not yeat another messy configurution to get damn X11 to work!???!!!!!!!

xorg.conf is ofcourse a shitty file to editing but configure it via XML and HAL!????

I really hope this is NOT an ubuntu solution!!!!! I hope this is a solutionm ALL dists have decided to use or else this will be another stupid mess and make ATI/NVida and other gfx developers more frustrated cause they have to be compatible to yet another configuration!!!!!!

I dont like xorg.conf syntyax but learning yet another XML shitty sol,ution if only ubuntu communmity has decided to use it then I will for sure leave ubuntu cause we DONT need hundreds of different solution for 100 diferent linux dists...


I see another mess atm:

* Bluetooth is broken cant configure it via consolke anymore :-( 

* Compiz has THREE different backend to configure it (Gconf/Inifiles/kdeconf) IMHO all should use ~/config/compiz/*.ini format instead of messy gconf/kdeconf

* Network framework (Why the hell do I have to login to X11 before I can connect to WPA network!?!?!?!?!?!? network backend should NOT depend of X11!!! It should use dbus and a console backend!!!

---

### Post by autocrosser on 2008-10-19
xorg.conf is not "broken" --as I said, EVERYTHING has been moved to /etc/hal/fdi/profile for "mods"--reason is that HAL can hotplug, so moving it all to HAL allows Xorg to respond "better"--this came in with Xorg 1.5

Take a look at the links I have provided for more info & adjust your system accordingly.


DO NOT MODIFY YOUR XORG ANYMORE......use the methods outlined in the links provided

---

### Post by autocrosser on 2008-10-19
This is a Xorg "solution"--again, they decided to use HAL to allow hotplugging. XML files are easier to edit than xorg.conf & we have provided several examples/links to work with the new method--Everyone will be moving to this, we are just the first to do so. 

As for the video/device sections--they are still edited thru xorg.conf--I don't know when they will be modified.

My xorg.conf (using nvidia) looks like:

#Custom Xorg

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
        Option          "AllowSHMPixmaps" "0"
        Option          "PixmapCacheSize" "2000000"
    SubSection "Display"
    Depth    24
        Modes    "1920x1200_60"    "1680x1050_60"    "1600x1200_60"    "1440x900_60"    "1280x1024_75"    "1280x1024_60"    "1024x768_75"    "1024x768_60"
    EndSubSection
EndSection

Section "Device"
    Identifier    "Videocard0"
    Driver        "nvidia"
    Vendorname    "NVIDIA Corporation"
    Boardname    "GeForce 8600 GT"
        Option        "Coolbits"    "1"
        Option        "TripleBuffer"    "True"
    Option        "NoLogo"    "False"
    Option        "SLI"    "SFR"
    BusID            "3:0:0"
EndSection

Section "ServerLayout"
    Identifier    "Single-Monitor"
        Screen          "Screen0"
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    Vendorname    "HannsG"
    Modelname    "HG-281DPB"
    Horizsync    24.0-80.0
    Vertrefresh    56.0-75.0
    Displaysize    593.28    370.8
EndSection


As you can see--your only edits right now are in the video area.


> **tielie said:**
> I fixed it by editing my xorg.conff file

but when i read your solution about hal i just say WHAT THE **** no no no not yeat another messy configurution to get damn X11 to work!???!!!!!!!

xorg.conf is ofcourse a shitty file to editing but configure it via XML and HAL!????

I really hope this is NOT an ubuntu solution!!!!! I hope this is a solutionm ALL dists have decided to use or else this will be another stupid mess and make ATI/NVida and other gfx developers more frustrated cause they have to be compatible to yet another configuration!!!!!!

---

