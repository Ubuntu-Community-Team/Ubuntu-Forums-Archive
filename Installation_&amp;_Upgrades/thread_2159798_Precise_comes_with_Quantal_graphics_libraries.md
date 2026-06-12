---
title: "Precise comes with Quantal graphics libraries???"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by soccermiles on 2013-07-04
So, I'm trying to get my video drivers in action. I'm unable to install nvidia-173 from the repositories. Here's a command line sample...

```

uberblah@glade:~$ sudo apt-get install nvidia-173
[sudo] password for uberblah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-173 : Depends: xorg-video-abi-11
              Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.

```

So, I try installing xserver-xorg-core to see why it doesn't want to install, and I get this monster. Look at the libraries it would have to remove. They all belong to Quantal. Why do I have these packages installed by default? This is a fresh Ubuntu 12.04 install, so this is completely unexpected for me.

```

uberblah@glade:~$ sudo apt-get install xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11-apps x11-session-utils x11-xfs-utils linux-headers-3.5.0-23-generic
  linux-headers-3.5.0-23 xinit
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgl1-mesa-glx libglapi-mesa xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa
Suggested packages:
  xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze
  firmware-linux
The following packages will be REMOVED:
  libgl1-mesa-dri-lts-quantal libgl1-mesa-glx-lts-quantal
  libglapi-mesa-lts-quantal libxatracker1-lts-quantal ubuntu-desktop
  x11-xserver-utils-lts-quantal xorg xserver-common-lts-quantal
  xserver-xorg-core-lts-quantal xserver-xorg-input-all-lts-quantal
  xserver-xorg-input-evdev-lts-quantal xserver-xorg-input-mouse-lts-quantal
  xserver-xorg-input-synaptics-lts-quantal
  xserver-xorg-input-vmmouse-lts-quantal xserver-xorg-input-wacom-lts-quantal
  xserver-xorg-lts-quantal xserver-xorg-video-all-lts-quantal
  xserver-xorg-video-ati-lts-quantal xserver-xorg-video-cirrus-lts-quantal
  xserver-xorg-video-fbdev-lts-quantal xserver-xorg-video-intel-lts-quantal
  xserver-xorg-video-mach64-lts-quantal xserver-xorg-video-mga-lts-quantal
  xserver-xorg-video-modesetting-lts-quantal
  xserver-xorg-video-neomagic-lts-quantal
  xserver-xorg-video-nouveau-lts-quantal
  xserver-xorg-video-openchrome-lts-quantal
  xserver-xorg-video-r128-lts-quantal xserver-xorg-video-radeon-lts-quantal
  xserver-xorg-video-s3-lts-quantal xserver-xorg-video-savage-lts-quantal
  xserver-xorg-video-siliconmotion-lts-quantal
  xserver-xorg-video-sis-lts-quantal xserver-xorg-video-sisusb-lts-quantal
  xserver-xorg-video-tdfx-lts-quantal xserver-xorg-video-trident-lts-quantal
  xserver-xorg-video-vesa-lts-quantal xserver-xorg-video-vmware-lts-quantal
The following NEW packages will be installed:
  libgl1-mesa-glx libglapi-mesa xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa
0 upgraded, 28 newly installed, 38 to remove and 0 not upgraded.
Need to get 4,086 kB of archives.
After this operation, 13.9 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

Oh, and by the way, I tried going through with this, and I had to reinstall Ubuntu because I couldn't boot back into it.

---

### Post by gifford on 2013-07-04
12.04.2 uses some of the Quantal libraries and the 3.5.xx kernel as opposed to 12.04.1 using 3.2.xx. Is the driver not available from system settings, additional drivers?

---

### Post by soccermiles on 2013-07-04
I heard somewhere I'm supposed to install it using the repositories, and that doing otherwise can result in errors with Steam (which is the application I've been trying to get working this whole time). Steam is such a pain to get working. You can't really debug the problems it has, because you can only have either Steam's output or the game's output, never both.

---

### Post by gifford on 2013-07-04
The driver used by the system settings, additional drivers does come from Ubuntu repositories. Have you tried installing it this way?
Here is a link you might find helpful: [http://askubuntu.com/questions/216286/difference-between-additional-drivers-nvidia](http://askubuntu.com/questions/216286/difference-between-additional-drivers-nvidia)

---

### Post by soccermiles on 2013-07-04
Solved it. It turns out I didn't need to use anything besides the additional drivers interface. I guess I shouldn't have made such a big deal about one forum post saying that it was a bad idea to do it that way. Maybe it was an old post or something. I remember hearing about graphics driver difficulty in certain versions of Ubuntu.

How do I set this as solved?

---

