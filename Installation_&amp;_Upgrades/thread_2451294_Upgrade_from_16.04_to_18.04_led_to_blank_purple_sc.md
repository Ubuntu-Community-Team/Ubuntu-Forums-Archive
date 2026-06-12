---
title: "Upgrade from 16.04 to 18.04 led to blank purple screen after boot."
date: 2020-10-01
forum: Installation &amp; Upgrades
---

### Post by dacinoorder on 2020-10-01
Hello!

I've elected to upgrade an old ASUS laptop's OS from 16.04 LTS to 18.04 LTS. 

The laptop's screen has died long ago, and thus I've been using a VGA cable to connect to a 4:3 monitor for display.

After the ubuntu boot loading screen, with those little white dots, finishes - I find myself greeted with a large, purple screen and no icons or buttons or anything, just my cursor.

On pressing Ctrl + alt + f6, I get the following error outputting to the terminal without end.
```
[NNN.NNNNNN] [drm:radeon_vga_detect [radeon]] *ERROR* VGA-1: probed a monitor but no|invalid EDID
```
NNN.NNNNNN is numbers that  increase endlessly, without any explicit pattern I can notice. I will include an attachment to show the pattern, taken by phone.

At this, I logged in, and tried to do a sudo apt update && upgrade. While this was happening, I noticed the above error code kept appearing even while I was typing or the terminal was giving me feedback on my upgrade command. Nothing noticeable changed.

I rebooted using terminal and through grub, went to recovery mode. In recovery mode, I tried to run the dpkg function, but I couldn't exactly see what it did as the screen was askew, and the monitor controls no longer work. Whatever it did, it finished and there was no change when I rebooted to test.

I rebooted again, and in command-line I checked 
```
dnesg | egrep 'drm|radeon'
```
The output was, as follows:
```
24.874133] [drm] VGACON disable radeon kernel modsetting
24.874221] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon modul!
```

The video card's model is as follows:
```
amd/ati rv516/64 mobility radeon x2300
```

This error has not been present before the upgrade, and I've only experienced it after upgrading.

Thank you for your help

---

### Post by dacinoorder on 2020-10-03
Attempted to follow [https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535) for troubleshooting.

When attempting to iterate over the boot options below, no improvement was experienced.
```


 nomodeset # note- remeber that "#", denotes a comment, do not type that or anything after that... just notes to you. 
 nouveau.modeset=0 
 radeon.modeset=0 
 i915.modeset=0 
 xforcevesa 
  ## vga=xxx # Note- where xxx is a vesa mode that your card supports, such as 771  # this worked previously, but is now deprecated and only work on earlier versions
 video=uvsesafb:mode_option=1024x768-32,mtrr=3,scroll=ywrap,noedid # use that noedid option if you get a bad edid read error in the xorg log 
 video=DVI-D:1024x768-16@60
```


When attempting the boot option below for troubleshooting
```
linux    /boot/vmlinuz-3.16.0-28-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro  nosplash --verbose text
```
No error codes were seen. All checks went "OK".


I saw a bit about updating my list of radeon drivers, but I am uncertain what to write in the 
```


sudo vim /etc/apt/sources.list
```

described list.

As a further note, I attempted a live disk to see if things work, using an USB drive, and it appears the laptop in question cannot boot from flash drive.

---

### Post by dacinoorder on 2020-10-05
Did some more attempts at troubleshooting.

I tried to revert to check desktop managers.

For ```
systemctl status lightdm
``` I got
[http://paste.ubuntu.com/p/sMxPFQqRR4/](http://paste.ubuntu.com/p/sMxPFQqRR4/)

for ```
systemctl status gdm
```
[http://paste.ubuntu.com/p/v6dYhV7dzd/](http://paste.ubuntu.com/p/v6dYhV7dzd/)

For ```
journalctl -xe
```
[http://paste.ubuntu.com/p/bnW2X2knvJ/](http://paste.ubuntu.com/p/bnW2X2knvJ/)



Attempting a liveCD had weird issues:

It boots up thru the boot splash screen, finishes loading, gives a blank black screen with backlight
stands there for ~5 minutes, then turns off a second, and the boot splash screen loads again. This time, I get the purple screen once more, and using Ctrl+alt+F2 I notice it's the normal installation

---

### Post by CelticWarrior on 2020-10-05
There's nothing to troubleshoot here.
When at the purple screen just press enter and type your password (blindly).

Here's what's happening: Although the internal monitor is broken it isn't disabled. It actually is the primary display where the login greeter would be displaying if it worked.

---

### Post by dacinoorder on 2020-10-06
> **CelticWarrior said:**
> There's nothing to troubleshoot here.
When at the purple screen just press enter and type your password (blindly).

Here's what's happening: Although the internal monitor is broken it isn't disabled. It actually is the primary display where the login greeter would be displaying if it worked.


Worked. Sort of

TTY console still spams the EDID error.

I can log into my admin account since it's the default on the log-in screen. However, I am unsure how to switch between users to let my mother use her user account. Toying with monitor settings to try and mirror did not yield results.

---

### Post by CelticWarrior on 2020-10-06
> [COLOR=#000000]Toying with monitor settings to try and mirror did not yield results.[/COLOR]

It doesn't. Those are user settings.
I haven't tried it yet but you may: First set the external monitor as primary; then disable the internal one.

EDIT (scratch that): [https://askubuntu.com/questions/1043337/is-there-to-make-the-login-screen-appear-on-the-external-display-in-18-04](https://askubuntu.com/questions/1043337/is-there-to-make-the-login-screen-appear-on-the-external-display-in-18-04)

---

### Post by dacinoorder on 2020-10-12
> **CelticWarrior said:**
> It doesn't. Those are user settings.
I haven't tried it yet but you may: First set the external monitor as primary; then disable the internal one.

EDIT (scratch that): [https://askubuntu.com/questions/1043337/is-there-to-make-the-login-screen-appear-on-the-external-display-in-18-04](https://askubuntu.com/questions/1043337/is-there-to-make-the-login-screen-appear-on-the-external-display-in-18-04)


Helped and solved, thanks!

---

