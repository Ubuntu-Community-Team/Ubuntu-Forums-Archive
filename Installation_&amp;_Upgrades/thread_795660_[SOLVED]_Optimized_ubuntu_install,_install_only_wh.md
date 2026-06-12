---
title: "[SOLVED] Optimized ubuntu install, install only what I want?"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by zeusalmighty on 2008-05-15
Hi, I was wondering whether an optimized installation of Ubuntu is possible. That is, starting COMPLETELY clean, and building upwards. Also, would it possible to optimize the kernel for the specific computer while doing so?

The main idea is increasing speed while decreasing unneeded applications, libraries and used disk space. I would also like to include a package manager, like synaptic and a GUI (could you also recommend a fast -but usable- gui? I hear XFCE is fast).

---

### Post by logos34 on 2008-05-15
yeah, at the very least a software selection option like you have in Suse would be nice.   But what you're talking about is more along the lines of Arch Linux, where you basically start with a minimal command-line install and then add the desktop and everything else. [Edit]

As far as the kernel goes you can build your own afterwards.  There are a couple of howto threads on that in the forums and maybe an entry in the community documentation wiki

---

### Post by zeusalmighty on 2008-05-15
So is there no way to do this? That's...disappointing...!

I was thinking if I could have only the applications I wanted, I could have a more optimal system. How about installing the server version, isn't that lighter? And is there not a way to install xfce without installing xubuntu-desktop (which installs all those other applications). How about UbuntuLite?

---

### Post by NightwishFan on 2008-05-15
It is possible to install a custom system with the minimal cd.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Install only a cli, and then:
```
sudo apt-get update && sudo apt-get install xorg xfce4
```

You can exchange xfce4 with a wm like fluxbox or icewm or something like kde-core (which is surprisingly light)

---

### Post by zeusalmighty on 2008-05-15
Thanks! I'll try that! Which WM do you reccomend? Can I also install other programs like synaptic, mplayer, firefox or are these depended on gnome?

---

### Post by NightwishFan on 2008-05-15
Depends on what you like. Unless you are really tight on ram there is no loss in using any gnome/kde apps. I personally use kde-core, but fluxbox and icewm are light and simple. My base built kde-core system with 64-bit uses about 80mb of ram on boot, which is good for me, since I have about 900mb of ram. Firefox and synaptic can be installed. Note you should be a more advanced user to attempt such a minimal install, as configuring some stuff can be confusing. (such as mounting hard drives)

---

### Post by logos34 on 2008-05-15
> **zeusalmighty said:**
> Thanks! I'll try that! Which WM do you reccomend? Can I also install other programs like synaptic, mplayer, firefox or are these depended on gnome?

nightwishFan is right--the minimal is probably the way to go (forgot about how it sets up--been a while since I tried it).

Here's a link you might want to check out--talks about the different wm/de options avail:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by zeusalmighty on 2008-05-16
It seems that the minimal install takes longer than the normal install :(

Either way, I've installed XFCE4, but I don't have audio! Is there a guide to install audio on such systems?

---

### Post by zeusalmighty on 2008-05-16
Ok, I've got everything working!

For anyone that wants to do the same:

1. Download the [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD") iso and burn it to a CD.
2. Boot from the CD and install without selecting any desktop packages (xubuntu-desktop or ubuntu-desktop etc).
3. After you're done, you have rebooted and are back at the terminal screen. Login and type:

```
sudo apt-get install xdm xorg xfce4
```This will install the XFCE window manager, and what else is needed to get a graphical-based startup.
When done, type:

```
sudo xdm
```This will start xdm, and allow you to login graphically. Once loaded you have a fully operational XFCE window manager, with ubuntu at it's base.

Optionally,

Go to a terminal (you may notice there is no option for a terminal, just hit Alt-F2 and type "xterm" -without quotes- in the run program.
[SIZE=3]
_**Graphics Drivers**_[/SIZE] 

If you have nvidia, type:

```
sudo apt-get install nvidia-glx-new nvidia-settings
sudo nvidia-xconfig
```[U]You can then configure your resolution with

```
sudo nvidia-settings
```Don't forget to press save for the changes to be saved!
(You can also start nvidia-settings from System --> Nvidia X Server Settings, but when you try to save the settings, there will be an error. This is because you are not running root.)

** Sound settings**[/U]

Run:

```
sudo apt-get install alsa-utils
```This will install the terminal based alsa-mixer along with other utilities. which should have all audio settings to mute. Unmute them and now you have sound! (**when you reboot, there is a good chance these settings will be reset. I have yet to find a work-around**)

[SIZE=3]**_Mount NTFS drives_**[/SIZE]

If you have NTFS drives you need to automatically mount, before you do any mounting of your own (or, if you already have, just unmount them) run:

```
sudo apt-get install ntfs-config
sudo ntfs-config
```This will bring up a small utility that lets you select which disks to mount and whether to enable read/write support.

[SIZE=3]**_Multimedia_**[/SIZE]

For full multimedia, follow [this guide]("http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia").

[SIZE=3]**_Extras_**[/SIZE]

Also useful utilities that don't get installed with XFCE are available in Synaptic. They all start with "**xfce**" so you should be able to find them relatively easy. My recommendations are:

- **xfce4-taskmanager** (basic but very good process manager)
- **geany** (advanced notepad utility)
- **mplayer** (video player, although if you followed the multimedia guide above you don't really need to install it)
- **deluge** (torrenting application, quite fully featured and fast. Transmission is also good)
- **xarchive** (archive manager. Note, "XArchive" not "Xarchiver". "Xarchiver" has many problems for me).

[SIZE=3]**_Themes_**[/SIZE]

If you feel you need to make XFCE a bit more beautiful, just visit [xfce-look]("http://www.xfce-look.org") and download your XFCE themes, Icon themes or Pointer themes. For these to be installed, simply **extract the archives** in the following directories:

- Themes:  ~/.themes
- Icon themes: ~/.icons
- Pointer themes: ~/.icons

That's it!!!

---

### Post by logos34 on 2008-05-16
> **zeusalmighty said:**
> It seems that the minimal install takes longer than the normal install :(

right, because you have to download EVERYTHING

> Either way, I've installed XFCE4, but I don't have audio! Is there a guide to install audio on such systems?

Hopefully this will help:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

EDIT: just saw your last post.  So good luck and enjoy ubuntu!

---

