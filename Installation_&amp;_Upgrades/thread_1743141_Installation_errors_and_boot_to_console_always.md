---
title: "Installation errors and boot to console always"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by sgol on 2011-04-29
I installed and then reinstalled UBUNTU 11.04 /x86 server into clean HDD1. It was done however with errors and boots in console tty mode

After the last installation there was message regarding  4 errors 
 [  7.664167]  [drm:drm_crtc_helper_set_config]  *Error* failed to set mode on [CRTC:6]
[   7.664174] fbcon_init: detected unhandled fb_set_par *Error*, error code -22  
[   7.664287]  [drm:drm_crtc_helper_set_config]  *Error* failed to set mode on [CRTC:6]
[ 20.806376]  [drm:drm_crtc_helper_set_config]  *Error* failed to set mode on [CRTC:6]

Then login prompt. 

Could someone who is aware of similar issues provide some kind advice   what it could be and what shall be done?

I am novice user and my goal is to have server with Unity-2d.

Thanks for help!

------------- 
Configuration: 
Intel Pentium 4/2,4 MHz, 512 RAM
Graphic card GeForce 4 MX440 /AGP8
2 HDD (HDD0- 230 GB Windows XP+GRUB, HDD1-180 GB UBUNTU 11.04) 
CD ROM Plextor, FDD 
GRUB boot to UBUNTU

---

### Post by dabl on 2011-04-29
Apparently there was a bug in the nouveau driver that came with 10.10:  [https://bugs.freedesktop.org/show_bug.cgi?id=32864](https://bugs.freedesktop.org/show_bug.cgi?id=32864)

On your other drive, an upgrade must have fixed it.  If your heart is set on 10.10, then you'll have to chroot into the installed (500GB) system, and run dist-upgrade to upgrade it.  Or, probably you could install 11.04 and not see the bug (test with a Live CD first).

---

### Post by sgol on 2011-04-29
> **dabl said:**
> Apparently there was a bug in the nouveau driver that came with 10.10:  [https://bugs.freedesktop.org/show_bug.cgi?id=32864](https://bugs.freedesktop.org/show_bug.cgi?id=32864)

On your other drive, an upgrade must have fixed it.  If your heart is set on 10.10, then you'll have to chroot into the installed (500GB) system, and run dist-upgrade to upgrade it.  Or, probably you could install 11.04 and not see the bug (test with a Live CD first).

---------------------------------------------

Thank you dabl!
after analysis of the situation prompted by you and two more attempts to reinstall UBUNTU 11.04 server (min configuration, etc) I decided not to go back to v10 but to try CentOS 5.6. 

Done, straightforward, easy without any (!) hint of a problem.
Impressive. So the issue of installing UBUNTU 11.04 is fixed in different way.

---

### Post by MAFoElffen on 2011-04-29
> **sgol said:**
> I installed and then reinstalled UBUNTU 11.04 /x86 server into clean HDD1. It was done however with errors and boots in console tty mode

After the last installation there was message regarding  4 errors 
 [  7.664167]  [drm:drm_crtc_helper_set_config]  *Error* failed to set mode on [CRTC:6]
[   7.664174] fbcon_init: detected unhandled fb_set_par *Error*, error code -22  
[   7.664287]  [drm:drm_crtc_helper_set_config]  *Error* failed to set mode on [CRTC:6]
[ 20.806376]  [drm:drm_crtc_helper_set_config]  *Error* failed to set mode on [CRTC:6]

Then login prompt. 

Could someone who is aware of similar issues provide some kind advice   what it could be and what shall be done?

I am novice user and my goal is to have server with Unity-2d.

Thanks for help!

------------- 
Configuration: 
Intel Pentium 4/2,4 MHz, 512 RAM
Graphic card GeForce 4 MX440 /AGP8
2 HDD (HDD0- 230 GB Windows XP+GRUB, HDD1-180 GB UBUNTU 11.04) 
CD ROM Plextor, FDD 
GRUB boot to UBUNTU
Okay, so which iso are you installing from?  I am assuming by what you are trying to do that you would be using 32bit server 11.04, which will bring you up on a server PAE kernel and install the server packages you want to install.  

After the server install you, you will come up in a tty text console.  From the command line, you will then
```

sudo apt-get install ubuntu-desktop

```which will install the Ubuntu desktop.  During it's install, it will reconfigure grub to start in the Graphical Interface.  If you want to be able to start in the text console from grub, you are going to have to add it to 40_custom as a copy of your 10_linux menu entries with "text" appende to your kernel boot line.

After the GDM login screen for Ubuntu comes up, press on the user > the password box will pop up... look on the bottom bar about halfway across and select "classic" in the dropdown box... Boot up the Xwindows seesion > goto synaptic and install the Unity 2D package...

With your hardware, what server "service" are you planning on running? You know that with each graphical "enhancement" you add, you're taking away resource that you might want to be using for your server services right?  If you are doing it to add ease to administering your server in a graphical environment... and with the memory and harware you are running... You might want to check out Xubuntu (xubuntu-destop) as an option to use a little less overhead for that.

On my test servers for the the dev versions, I ran ubuntu-desktop, kubuntu-desktop and xubuntu-desktop on both 32bit and 64bit server versions to see how they faired...

---

