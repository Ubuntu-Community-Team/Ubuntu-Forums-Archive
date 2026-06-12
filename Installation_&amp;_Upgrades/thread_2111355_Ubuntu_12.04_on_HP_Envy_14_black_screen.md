---
title: "Ubuntu 12.04 on HP Envy 14 black screen"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by Niemand000 on 2013-02-01
So, I installed Ubuntu 12.04 on an HP Envy 14 laptop and now I'm having issues loading.  Long story short, I'm getting a black screen/purple screen/black screen with a blinking cursor.  Upon looking up this issue, I find that others have encountered the same thing and have found a fix for it, but the best fix is one that I'm not sure how to duplicate:

**"Black console**

 Right after the installation, I notcied that the console remained  black after the boot menu (the display turns off) before the KDE login  screen appears. After some testing, I found out that is is due to the  switchable graphics. It seems as running the *i915* and *radeon* kernel modules causes some conflicts.
 Fixing this is quite simply: Simply put the unneeded module (e.g.  radeon) on the blacklist in */etc/modprobe.d* and recreate the ramdisk with *mkinitrd*. Reboot to check whether it woked out." ~ Andreas Demmer
[http://www.andreas-demmer.de/en/2010/07/18/testbericht-linux-auf-dem-hp-envy-14/](http://www.andreas-demmer.de/en/2010/07/18/testbericht-linux-auf-dem-hp-envy-14/)


Could someone please explain how I can do what he did when I can't even get past the log in screen?  Or access Grub, or anything.  Thanks so much in advance

---

### Post by oldfred on 2013-02-04
If you have only one system or grub only found one, you do not get grub menu automatically.

You should be able to hold down shift key from BIOS until frub menu appears.

Some screen shots.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
       Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

### Post by Niemand000 on 2013-02-07
When I try to log into GRUB it starts loading, but then the screen goes purple, then black and I hear that signature ubuntu drum sound.  Any idea what's going on?

---

### Post by MAFoElffen on 2013-02-07
> **Niemand000 said:**
> When I try to log into GRUB it starts loading, but then the screen goes purple, then black and I hear that signature ubuntu drum sound.  Any idea what's going on?

Take a breath... At the grub menu display, hit a <down-arrow> to make the menu stay there...

What oldfred tried to explain to you... was that if you edit you grub boot line for starting Ubuntu, you can tell the kernel to pass along a KMS flag to not set modes (nomodeset) or to set a certain video GPU or VGA mode.

Sounds like you may not be too experienced with a commandline text editor and commandline commands, right? If so, then if you edit to add the boot option ""--single" you could go commandline and edit the  /etc/modprob.d/balcklist file using vim...

If not, then boot a LiveCD, mount the installed filesystem and edit that file. That way you could edit your files from gedit (graphical editor) in the Live Environment, install or make any system changes directly to your installed system from a graphical environment. 

For editing the bootline of a Grub Menu at boot or to Mount a filesystem from a LiveCD... I have tutorials and instructions for those as they relate to graoghics issues on Post #2 and the LiveCD and mounting on Post#3 of my Graphics sticky... link in my sig line. Look for the petrinent 

Other wise, off the top of my head, I know of about 10+ other ways to get there, but those are the best 3 options, depending on what tools "you" feel comfortable with using.

---

