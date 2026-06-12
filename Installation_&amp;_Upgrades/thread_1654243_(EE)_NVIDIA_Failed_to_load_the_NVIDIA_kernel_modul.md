---
title: "(EE) NVIDIA: Failed to load the NVIDIA kernel module."
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by Super Brava on 2010-12-28
Okay, after an update my system is stuffed. The 3 kernels I've got to choose from in Grub all do the same thing, I get this error:

(EE) NVIDIA: Failed to load the NVIDIA kernel module.
Please check your
(EE) NVIDIA: system's kernel log for additional error
messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

I've tried recovery mode, the system gets to a point and then just hangs, I can't boot from a CD because it start loading, gets to the purple screen with Ubuntu 10.04, screen goes black, system hangs. I can't get into a terminal to try anything. I'm typing this from windows, I dislike Windows with a passion, but it's currently working! Please be gentle with me, I'm really not very good at command line stuff, (if I can actually manage to get to a terminal session).

---

### Post by Super Brava on 2010-12-28
I posted previously in here:
[http://ubuntuforums.org/showthread.php?t=1480660](http://ubuntuforums.org/showthread.php?t=1480660)

But the thread is closed and my problems are deeper. I've tried to boot from CD and it won't play, from a suggestion in another thread I've tried hitting any key while the CD is loading and I can get to the menu, if I "try Ubuntu without install" it starts loading then sits at the purple screen with scrolling dots for more than 25 minutes and goes no where. At other times it'll give the error "(process:335) GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)"

If I use the 3rd option I have in Grub, 2.6.32-24-generic (recovery mode) I get to INITRAMFS, but only have limited commands to play with. (Not that I know what I'm doing anyway)

From reading other threads, I assume I have to reload my NVIDIA driver, but I can't get to a terminal session that will allow me to do that.

---

### Post by davidmohammed on 2010-12-28
before you "try without installing" - press e to edit (or F6?) and edit the boot string.  Add "nomodeset" immediately before "quiet splash"

when you get to the live CD desktop, try mounting the hard-drive and see if there is a file called /etc/X11/xorg.conf.  Rename it.

e.g.

sudo fdisk -l

this will list all your partitions

create a mount point to whatever partition ubuntu is installed into.

sudo mkdir /media/mymount
sudo mount /dev/sda1 /media/mymount

then run nautilus as root

gksudo nautilus

you should be able to browse down through /media/mymount/etc/X11

to rename xorg.conf


n.b. all of this is from memory - syntax might not be quite correct...!

---

### Post by davidmohammed on 2010-12-28
...

also - have you tried to boot your current installation with nomodeset? i.e. press e to edit your grub2 kernel boot options?

---

### Post by amsterdamharu on 2010-12-28
Continued here:
[http://ubuntuforums.org/showthread.php?t=1480660&page=6](http://ubuntuforums.org/showthread.php?t=1480660&page=6)

The drivers usually aren't loaded because nouveau is already there.

---

### Post by Super Brava on 2010-12-28
> **davidmohammed said:**
> ...

also - have you tried to boot your current installation with nomodeset? i.e. press e to edit your grub2 kernel boot options?

OK, tried that, it ends up at a black screen with a dialog box in the middle containing:

Ubuntu is running in low graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernel module.
Please check your
(EE) NVIDIA: system's kernel log for additional error
messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

It has an "enter" arrow with OK in the box, I have no mouse or keyboard input at this stage, so that's as far as it gets.

Tried "nomodeset" from the CD, after a while of hopeful CD drive noises it ends up with a screen of Ubuntu panic errors.




> **amsterdamharu said:**
> Continued here:
[http://ubuntuforums.org/showthread.php?t=1480660&page=6](http://ubuntuforums.org/showthread.php?t=1480660&page=6)

The drivers usually aren't loaded because nouveau is already there.

I can't log in, log out or get to a terminal session to do any editing. I can't boot from a live CD, the only success I have is booting into windows from grub.

---

### Post by amsterdamharu on 2010-12-28
Hi, sorry I continued on the other thread because I thought you started that one.

When you get the (EE) messages there should be a button to on the window and something to choose restart X but it's been a while since I've seen it.

Pressing control + alt + F1 or F2 doesn't get you to a non graphic login screen? From there you can try the commands.

> I have no mouse or keyboard input at this stage, so that's as far as it gets.
That would make it difficult. Could you download the tinycore iso and unetbootin on Windows and then use unetbootin to make a bootable USB. Tinycore is only 10MB and I am sure it will boot with that. You need a cable Internet though to install the browser.
If you don't just try to mount your Ubuntu partition and rename the /etc/X11/xorg.conf file to xorg.conf.org or something. Then restart Ubuntu and see what happens.

---

### Post by Super Brava on 2010-12-28
OK, thanks guys, we're progressing. I managed to download a CD iso that I can boot from with F6 "nomodeset", then with a combination of the above replies I've managed to edit the xorg.conf and change the nvidia line to vesa. I can now boot from grub and see my desktop/ files etc, although I can't do anything with them as I don't have mouse or keyboard input.

> **amsterdamharu said:**
> 
log out
press control + alt + F1
Log in to (text only terminal) and type the following commands:
```
sudo apt-get purge nvidia*
sudo apt-get purge xserver-xorg-video-nv
sudo apt-get purge xserver-xorg-video-nouveau
sudo apt-get purge nouveau-firmware
sudo nano /etc/X11/xorg.conf 
```Now find a line with:
Driver         "nvidia"
and replace nvidia with vesa
Now save it with control + o -> enter and control + x to exit.
(you might need a reboot here because the nouveau driver is persistent and still isn't unloaded)
One more last command:
```
sudo service gdm start
```When you see your desktop you can either wait a while and see if the system detects nvidia drivers for you to install or press alt + F2, type jockey-gtk and click run.

Tried the above with limited success. There was no text to edit in xorg.conf, so I probably wasn't opening the correct file. I managed using nautilus to copy xorg.conf to the desktop, rename the original, edit the desktop version and replace it in the X11 folder. Now that I can bootup with limited success using grub or the CD, if someone can point me in the direction that I can have mouse and keyboard control I'll be a happy chappy.
One consolation with all this, I've been too busy to see us lose the cricket!

---

### Post by amsterdamharu on 2010-12-28
Sorry for all your troubles and for losing the cricket.

There is something wrong with the xorg.conf, now when you start you get a graphic login screen but no keyboard or mouse?

Could you post the xorg.conf so we can check the values for keyboard and mouse, I don't use usb keyboard or mouse. This is my xorg.conf (only keyboard and mouse settings)
```
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

```

---

### Post by Super Brava on 2010-12-29
This is all that's in my xorg.conf file:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "vesa"
    Option    "NoLogo"    "True"
EndSection

Nothing about input devices!

---

### Post by amsterdamharu on 2010-12-29
You can try replacing it with this:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "Device"
    Identifier     "Default Device"
    Driver         "vesa"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    DefaultDepth     24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Super Brava on 2010-12-29
No go. I can get to my desktop, a lovely background photo of my car and all my desktop icons, but no mouse or keyboard input. Very frustrating.

---

### Post by Super Brava on 2010-12-29
It seems that dramas with NVIDIA driver setup is not uncommon. From another thread, this code is suggested as an xorg.conf update:

```
apt-get --reinstall install x11-xserver-utils gnome-core  
apt-get install gdm
dpkg-reconfigure gdm
depmod

```Will that take me in the right direction, or add to my dramas? And how do I reinstall when I'm running from a live CD?

---

### Post by Super Brava on 2010-12-29
Hopefully I can called this problem solved. After 2 days of trying to modify xorg.conf from a live CD and managing to get to my desktop, but not having keyboard or mouse, I had a brainwave this morning. I disconnected the keyboard and mouse, plugged them back in and they worked. I used the above code and everything seems to be doing what it's supposed to. Thanks for the help, I would have lost everything if it wasn't for this forum resource.

Mick.

---

### Post by zoidbergs on 2012-04-02
Hi there! I have similar problem on my _Mint 9 Isadora_, which is based on _Ubuntu 10.04_.
I can't boot into my Mint OS, but I can boot from CD/DVD, USB and Windows XP (which I only use for the newest and bad supported in Wine games).
Maybe I got those errors after "--recovery mode", I used the "clean" and "dpkg" functions to repair broken packages on Synaptic.
After that in normal boot I have an error window which freeze the system (keyboard and mouse doesn't work):
"***Ubuntu is running in low-graphics mode ***
[I]The following error was encountered. You may need to update your configuration to solve this. 
(EE) Failed to load /usr/lib/xorg/modules/libglx.so 
(EE) Failed to load module "glx" (loader failed, 7) 
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your 
(EE) NVIDIA:  system's kernel log for additional error messages. 
(EE) Failed to load module "nvidia" (module-specific error, 0) 
(EE) No drivers available.[/I]"
In recovery mode I have next:
"*[ 2.846917] Console: switching to colour frame buffer device 128x48*" But I'm able to use "Ctrl+Alt+Del" to reboot.
I read from other forum a suggestion - rename "*xorg.conf"* from */etc/X11/xorg.conf*
I tried that and saw splash screen and user select screen but the system hangs (keyboard and mouse doesn't work) with other error.
My PC specs: Asus M2N-E SLI, AMD Athlon 64 X2 4000+, DDRII 2GB, GeForce GTS 250 E-Green 1GB
Is there any solution or way to fix my Mint 9 or I need to do fresh install? Can Ubuntu be recovered from DVD like Windows?
Thanks a lot in advance!

---

