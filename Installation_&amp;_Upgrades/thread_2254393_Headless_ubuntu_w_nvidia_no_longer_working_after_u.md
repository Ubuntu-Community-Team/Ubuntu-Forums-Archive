---
title: "Headless ubuntu w/ nvidia no longer working after upgrade"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by bfree on 2014-11-26
Years ago, I had set up a remote/hosted, headless server with an nvidia card, which I used for server-based GPU processing - 
using Ubuntu Karmic + nvidia proprietary drivers + XDMPC, gdm, x11vnc.  I was able to run dynamically GPU-generated images/videos through an apache server.

I hadn't touched the server in years and recently decided to upgrade it to a newer dist.  On Karmic, I was able to run NV_GLX-based rendering, display X11-based apps on my remote client, and connect remotely via x11vnc.

After upgrading to Lucid, x11vnc would only display a black screen (plus the local and remote mouse cursors); X11 still displayed fine (though slow, as if software rendered), and i could no longer do server-based GPU rendering.

After spending a day pouring over the thousands of posts on black screens (and seeing a message stating that gdm no longer supported XDMPC on Lucid), I decided to continue my stair-step upgrade - and I'm now up to Trusty 14.04.1 LTS (3.13.0-41-generic).

On Trusty - I got the same thing from x11vnc: black screen with local/remote cursors.

I spent two days hacking on my system, trying different window managers (gdm, lightdm, xdm), different desktop sessions (ubuntu, gnome, gnome-fallback, openbox), and endless different settings - and I'm now able to get a login screen via lightdm - but the desktop doesn't come up after login - just a orange-colored background.  X11 still runs slowly, and glxinfo (via ssh -XC tunnel) inexplicably shows: "server glx vendor string: SGI" despite the fact that I seem to be clearly using the nvidia driver:

nvidia-smi: GPU 0: GeForce 9800 GTX/9800 GTX+
lspci: NVIDIA Corporation G92 [GeForce 9800 GTX / 9800 GTX+]
dkms: nvidia, 340.32, 3.13.0-41-generic, i686: installed
/var/log/Xorg.0.log: NVIDIA dlloader X Driver 340.32

/var/log/Xorg.0.log reports:
[  5281.362] (II) NVIDIA GLX Module  340.32  Tue Aug  5 20:36:43 PDT 2014
[  5281.364] (II) NVIDIA dlloader X Driver  340.32  Tue Aug  5 20:13:14 PDT 2014
[  5281.364] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  5281.938] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[  5281.940] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX/9800 GTX+ (G92) at PCI:1:0:0
[  5281.940] (II) NVIDIA(0):     (GPU-0)
[  5281.940] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  5281.940] (II) NVIDIA(0): Validated MetaModes:
[  5281.940] (II) NVIDIA(0):     "NULL"
[  5281.940] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  5281.947] (II) NVIDIA(0): Setting mode "NULL"
[  5282.003] (II) NVIDIA(0): [DRI2] Setup complete
[  5282.003] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia

Here are my key settings in /etc/lightdm/lightdm.conf (I've tried every imaginable combination):
Section "Files"
    ModulePath      "/usr/lib/xorg/modules/extensions"
    ModulePath      "/usr/lib/xorg/modules"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "glx"
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
EndSection
Section "Screen"
    Option         "UseDisplayDevice" "none"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Headless"
    DefaultDepth    24
    Option         "AllowEmptyInitialConfiguration" "True"
    SubSection     "Display"
        #Option     "UseDisplayDevice" "none"
        #Virtual    1024 768
        #Modes      "nvidia-auto-select"
        Modes      "1024x768"
        Modes      "1600x1200"
        Depth       24
    EndSubSection
EndSection

Here are the parameters I'm using for x11vnc (also tried every imaginable combination):
sudo x11vnc -xkb -noxrecord -noxfixes -noxdamage -auth guess -rfbauth ~/.vnc/passwd -rfbport 5900 -display :0


If _anyone_ has any idea of what I can do to trouble-shoot/fix this, it would be much appreciated.  Let me know if you need specific config files or logs.

Telling me to switch to a different linux distro (gentoo/etc) is not an option at this point.  As for vnc servers, it needs to be x11-based, and I prefer x11vnc, as that has always worked cross-platform for me in the past.  I've always used gdm in the past, but I'm open to other window managers if that'll get me going again.  lightdm seems promising at this point.

Thanks in advance!

---

### Post by bfree on 2014-11-26
Ah - just noticed that I'm now able to right-click after the login - I get the normal GUI file system menu: create folder, etc.

So the desktop is there - but not the system menus.  Not that familiar with lightdm or setting up desktop sessions - what's the trick for getting the system menus to show up, or at least popup a shell window?

Note: ctrl+alt+F1 does nothing.

---

