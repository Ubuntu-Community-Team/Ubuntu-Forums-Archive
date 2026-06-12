---
title: "Quantal re-installation results in The system is running in low-graphics mode"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by Peter Bell on 2013-02-21
I have two Intel machines, both with embedded Intel Graphics.  One of these machine had been running Quantal (as online upgrade for many versions - perhaps as far back as 2007 ... I can't remember whether I'd ever done a re-install since then).  One machine is an Intel Core2 Duo machine from 2007, the other is an i3-530/H55 system.

Now, because I'd had a problem with the disk drive, I decided to re-install from a flash drive.

The flash drive boots fine and will run with a 1920x1080 desktop.  However, if I go through the reinstall process from this flash drive, the resulting sytem produces the "The system is running in low-graphics mode" error (even though the grub menu had been displayed in 1920x1080).  At this point the mouse and keyboard are non-functional, but I can c-alt F1 to select an alternate session.  However, the problem with this is that I can't login - I enter user and password and get permission denied.  I know exactly what username/password I entered during the installation process - I've even repeated the installation to confirm.

I've been through the procedures [here]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error"), most of which don't apply because I'm not using AMD/ATI/NVidia graphics.

If I inspect the lightdm log files, I see an entry there about not being able to find 'org.freedesktop.Accounts'.

I have followed instructions to set gdm as the default display manager - now I just get an endless hourglass during startup (on the ubuntu welcome screen with red/white dots in 1920x1080).

If I boot into recovery mode, I can get to a root shell, which is where I've been doing all the system updates etc.

For the life of me, I cannot understand why, if the simple boot image/grub/ubuntu welcome screen can all display hi-res 1920x1080, the fully installed and updated system should fail to do this.

A little further info:
If I boot into recovery, and select failsafe graphics, after 'Loading extension GLX', I get a: 'Fatal server error:AddScreen/ScreenInit failed for driver 0".  The only additional info I see in the Xorg.failsafe.log is that VBESetVBEMode failed.

---

### Post by MAFoElffen on 2013-02-23
(Most) Intel graphics is OpenSource, so is a native driver installed with it. In the instances where that is not true, usually that's when Intel came out with something new hardware wise and their sharing of code hasn't made it downstream yet... In your case that doesn't apply.

I would say that since it worked "before" on Quantal as native without installing or changing anything else, that there was a problem with Xorg when it installed on the re-install.

You could go two avenues... 

One way would be to verfify your USB install ISO, which would be to boot off it... At the first panel (purple with the keyboard/person icon at the bottom) press any key. That will bring up a language panel, then the Advanced install menu. Check disk will be one of the menu options. If good, then completely re-install.

The other way would be to remove-purge the desktop and re-install it. This would be from the commandline:
```

sudo apt-get update
sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop

```
This might seem like hitting it with a 4x4, but the desktop manager and desktop environment are layers above the Xserver. 

In a third way, yould just remove (purge) the XServer and reinstall it... But... If you remove the X layer and reinstall it, you orphan the layers above it/ that link into it. In that way, you'd have go back to reconfigure the layers above it to get it all working together again anyways... IMO Less work to re-install the desktop package that includes everything.

---

