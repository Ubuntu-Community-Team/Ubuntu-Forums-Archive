---
title: "Installer won't display after dead graphics card (with troubleshooting video!)"
date: 2014-02-10
forum: Installation &amp; Upgrades
---

### Post by stretch3 on 2014-02-10
Hi there,

I have a old computer nearly 10 years old that was running in dual boot Windows XP and Lubuntu until the graphics card died of old age. I use it for basic tasks like internet browsing/streaming, PDFs etc in my shed.

I removed the graphics card and now use the integrated graphics VGA port but it seems like Lubuntu doesn't support the VGA port where XP does. Then I decided to install Lubuntu again but the installer only gets so far. I have uploaded a video to better describe what happens during install:

[https://www.youtube.com/watch?v=3jLsMpPcLXo](https://www.youtube.com/watch?v=3jLsMpPcLXo)

Near the end of the video, I press ALT + CTRL + DEL which brings the screen back and prepares to restart the computer. What I think is happening when the mouse cursor disappears at 4:09 is that the computer is adjusting the screen mode but cannot pick one as I can hear some changing high frequency noise from the screen (I can also hear it in the video).

It is a Intel P4 3GHz, 1Gb ram, Gigabyte GA 8S661FXM-775, had a Nvidia Geforce FX 5200, running XP and was running Lubuntu until the graphics card died.

I also tried Linux Lite 1.0.8 (based on Ubuntu LTS and similar installer to Lubuntu) which installed and works fine and Linux Mint but the installer for Mint acts the same as Lubuntu.

What can I try to get Lubuntu working again?

---

### Post by mörgæs on 2014-02-11
Have you tried the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by ppjdee on 2014-02-11
the falling wrenchs is loud >.<
could lubuntu possibley be to heavy for your old vga device?

---

### Post by sudodus on 2014-02-11
Welcome to the Ubuntu Forums :-)

You might have a problem with the video acceleration, that might be fixed if you change according to the following tips

1. Try a flavour, re-spin or distro based on Ubuntu 12.04 LTS. See this link

[http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12918552#post12918552](http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12918552#post12918552)

(and maybe some other post in the same thread)

2. If Lubuntu 13.10 is installed (but not quite working), try a *temporary* boot option, maybe **text** according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and try to change the video acceleration

> John Hupp <lubuntu@prpcompany.com> wrote:

There was this helpful bug report on file at [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982).

It described behavior on Dell PC's with integrated Intel graphics, in which Adobe Flash Player would display only with shades of purple and green in a horizontally compressed window (or at least that's how I would describe what I see on a Dell Dimension 2400).

The work-around (Comment #1) was to change the Xorg acceleration method to UXA. 

User reported a work-around:

-o-

Edit (or create)** /etc/X11/xorg.conf** as follows: (ugh, can't format, should be a ***tab*** before each line except the first and the last).

```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

```
Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

-o-

I forgot to include, however, that the bug workaround messes up the login screen (LightDM).  You can make out an entry box that one assumes is for the password entry, but everything else is largely unidentifiable.

So as a workaround it leaves a lot to be desired, unless we can also figure out how to fix the login screen.

This method works for me to restore good graphics in an old IBM Thinkcentre with Lubuntu Saucy alpha-2 and the following Intel graphics.

VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

There is no issue with the login screen.

---

### Post by stretch3 on 2014-02-11
Thank you for your replies, and sorry about the falling spanners! Needed them to help prop up my Nexus 7.

> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

You might have a problem with the video acceleration, that might be fixed if you change according to the following tips

1. Try a flavour, re-spin or distro based on Ubuntu 12.04 LTS. See this link

[http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12918552#post12918552](http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12918552#post12918552)


Thanks for that, downloaded Lubuntu 12.04 and that worked fine. :D

---

### Post by sudodus on 2014-02-12
I'm glad Lubuntu 12.04 runs well for you, but unfortunately it has no long time support, and has passed end of life. It means that the Lubuntu specific program packages receive ***no security updates***. I suggest that you install a flavour, re-spin or distro (based on Ubuntu 12.04) that has long time support, for example

Bento, Bodhi, LXLE, Precise Gnome Classic Tweaks, Linux Mint Maya

---

### Post by mörgæs on 2014-02-12
Maybe it's time we hear about the graphics card in use, assuming you have removed the dead Nvidia.

Please post the results from 
```
lspci | grep -i vga
```

---

