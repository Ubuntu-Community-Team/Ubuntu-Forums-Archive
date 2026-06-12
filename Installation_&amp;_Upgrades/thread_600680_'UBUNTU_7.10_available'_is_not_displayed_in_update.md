---
title: "'UBUNTU 7.10 available' is not displayed in update manager"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by heinbloed on 2007-11-02
Dear All,

I really want to upgrade my business laptop from Ubuntu 7.04 to Ubuntu 7.10, but when I follow the recommended method (click on SYSTEM ==> Administration ==> Update Manager): All updates are installed, so the system is in a defined, current, state.

But in the top of Update Manager window, it does *not* say that 'Ubuntu 7.10 is available', the field is empty.

Keeping Ubuntu 7.04 or a fresh install to 7.10 is not an option, upgrading to 7.10 is my preferred choice

What do I do now?

Thanks for help,

Peter

---

### Post by Pumalite on 2007-11-02
Try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade

---

### Post by oilchangeguy on 2007-11-02
> **heinbloed said:**
> Dear All,

I really want to upgrade my business laptop from Ubuntu 7.04 to Ubuntu 7.10, but when I follow the recommended method (click on SYSTEM ==> Administration ==> Update Manager): All updates are installed, so the system is in a defined, current, state.

But in the top of Update Manager window, it does *not* say that 'Ubuntu 7.10 is available', the field is empty.

Keeping Ubuntu 7.04 or a fresh install to 7.10 is not an option, upgrading to 7.10 is my preferred choice

What do I do now?

Thanks for help,

Peter

is there a special reason you "need" to upgrade to 7.10. if 7.04 is working fine for you, there's no real reason to upgrade. and it's always best to do a fresh install, rather than an upgrade.

---

### Post by heinbloed on 2007-11-02
> **oilchangeguy said:**
> is there a special reason you "need" to upgrade to 7.10. if 7.04 is working fine for you, there's no real reason to upgrade. and it's always best to do a fresh install, rather than an upgrade.

The main reason is that my current 7.04 runs at 1024x768 which is extremely annoying; while the LiveCD of 7.10 ran at 1280x1024, which is what I need.

Thanks, Peter

---

### Post by oilchangeguy on 2007-11-02
> **heinbloed said:**
> The main reason is that my current 7.04 runs at 1024x768 which is extremely annoying; while the LiveCD of 7.10 ran at 1280x1024, which is what I need.

Thanks, Peter

if you read the forums you'll note, that just because the live cd does something. does not mean it will be that way when it's installed. and if you search the forums the resolution can be adjusted.

---

### Post by Pumalite on 2007-11-02
Here is a collection of links and tips that might or might not help you with your problem:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html](http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html)

[http://ubuntuforums.org/showpost.php?p=3484653&postcount=15](http://ubuntuforums.org/showpost.php?p=3484653&postcount=15)

 Re: Changing screen resolution?
Hi. The solution is in that page; I would just add that since you're using the i810 driver, you probably need to install the 915resolution package. Here's what Synaptic says about it:
Quote:
resolution modification tool for Intel graphic chipset

915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots in order for its changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

The 915resolution package becomes obsolete with the newer xorg,
especially if you have the xserver-xorg-video-intel package installed.
Newer xorg brings modesetting support by default.

Homepage: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)
Or, you could use the intel driver instead of the i810.

---

### Post by heinbloed on 2007-11-02
Thanks for your suggestions !

I spend countless hours trying to get my screen resolution up to 1280x1024 in 7.04, but I have a Radeon Mobility FireGL card in my laptop, and I tried all kind of drivers: fglrx, ati, and vesa. All of them supported the desktop effects (except vesa), which is nice, but not really useful. I made numerous modifications to Xorg.conf, but the highest resolution I got was 1024x768.

I have to be honest, strange things happened when I ran on LiveCD 7.10 in 1280x1024:

Gnome's top menu bar (with the Ubuntu-logo on the left and the power button on the right), had a *fixed* width of 1024 pixel !

The lower menu bar (with the trash can in the right corner), was 1024 pixels wide as well, and was sitting on top of any application, 768 pixels below the top edge of the screen ==> Looks like Gnome thinks that it's still running at 1024x768. The Screen Resolution tool still listed a max resolution of 1024x768.

I could drag the lower menu bar to the real bottom of the screen and it would expand to 1280 pixels when doing so.

All applications I tried from the LiveCD ran at 1280x1024: Firefox, OpenOffice, you name it.

Hence I'm optimistic to get 1280x1024 by installing 7.10, even if the top menu bar is a little short ;-)

What do you think?

Peter

---

### Post by Pumalite on 2007-11-02
I'd save /home and data and do a clean install. That's what I've done in 3 of my computers. In one I did a clean install of Beta and through updates I now have the Final Release. In the other 2, I just did a clean install of Gutsy Final. I've had no problems. As oilchangeguy said, look around, Clean install is the safe bet.

---

