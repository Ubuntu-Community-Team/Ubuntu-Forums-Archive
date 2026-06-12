---
title: "Plasma 5 Error (All shell packages missing)?"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by Terone on 2016-04-22
So the other day I tried upgrading kubuntu 15.10 to 16.04

Apparently the distribution upgrader was bugged and couldn't complete the upgrade

I happened to be at my computer as I watched in horror as my computer froze. What I do know is that Kubuntu already downloaded all the packages and was upgrading already half of the packages before it froze.

After a forced reboot, everything was booting up fine (kubuntu splash screen and all) to a black screen. Luckily commandline was working (ctrl + alt + f1)

I updated and dist-upgraded the system hoping that would fix it, and after another reboot, same black screen.

But in the commandline, it shows that it is in 16.04. When trying ```
startx
```

The photo in the attachments is what shows up.

What can I do to fix this?

I already tried purging 'plasma-desktop' and 'kubuntu-desktop' and installing them back.
I even went so far as to reinstall 'libqtcore4'

I do a lot of my important work on kubuntu, and I would really appreciate anyone's help.

---

### Post by Terone on 2016-04-22
And is it normal for 'sudo apt-get update' to hit 3 websites only? Seems way too small. I would like to know where I can get a new sources.list for 16.04

---

### Post by Rezy on 2016-04-23
Hi all,

I have the same issue :(
 When I upgrade distribution I had error with mysql-server dependency.

---

### Post by QDR06VV9 on 2016-04-23
> **Rezy said:**
> Hi all,

I have the same issue :(
 When I upgrade distribution I had error with mysql-server dependency.

Hi Rezy Please do not hijack someone's support thread as it will not be the same as the Op and will hinder you from getting the help you seek.
So if you would start your own support thread in the proper area and proper title IE:** "error with mysql-server dependency"**
Thanks

---

### Post by encolpe on 2016-04-24
I got the same problem and i didn't solve it.

You can check the $HOME/.local/share/xorg/Xorg.0.log and search for the "(EE)" string. The error should be related to GLX or a propriatery driver (nvidia/radeon).

Check out the new nvidia PPA didn't work for me but you should give it a try :

[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)

Regards

---

### Post by Tom_Kidman on 2016-04-26
I've got exactly the same problem here - Frozen upgrade to 16.04 from 15.10, forced reboot and then exactly the same issues as OP.  His image capture matches mine exactly.  My wifi was also broken after the upgrade, so I had to plug into ethernet.  Funnily enough I also got errors related to upgrading mysql!  Any advice would be much appreciated.

After running startx, I get an error in ~/.local/share/xorg/Xorg.1.log: (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I've tried to install the latest drivers using the nvidia ppa as suggested above, but no luck.

Could this just be a problem with the new version of plasma?  I'm using asus laptop with a fancy nvidia card.

---

### Post by dpeets on 2016-04-28
I'm getting the same thing.  X is totally functional, but icons are missing in programs like emacs, and Plasma is entirely absent.  The screen unlocker fails, so I have to unlock from a virtual terminal.  Trying to start the Plasma shell manually from Konsole:[br]
$ plasmashell[br]
Icon theme "breeze" not found.[br]
Icon theme "oxygen" not found.[br]
Error: standard icon theme "oxygen" not found![br]
Failed to load the OSD QML file file from ""[br]
We have no shell handlers installed[br][br]

How I got Konsole in the first place:  Thunderbird was set to open minimized on startup, and putting the cursor in the upper left corner allows me to switch windows and access it.  Finding an e-mail with a link, I can get my default Chrome browser, and from Downloads I can open a folder using Konsole (Dolphin doesn't work).  So technically I can use this setup... but it's extremely clunky and annoying.[br][br]

Prior to the upgrade I was using FGLRX from [http://ppa.launchpad.net/costamagnagianfranco/locutusofborg-ppa/ubuntu](http://ppa.launchpad.net/costamagnagianfranco/locutusofborg-ppa/ubuntu) for which there's no 16.04 driver yet (it looked like it hadn't been released as of yesterday).  On startup, X starts and the colours and resolution seem fine.  in Xorg.0.log, the only two error lines are[br]
[    37.003] (EE) Failed to load module "fglrx" (module does not exist, 0)[br]
which is followed by loading an x.org ATI module instead, and the one here:[br]
```
[    37.085] (II) [KMS] Kernel modesetting enabled.[br]
[    37.085] (WW) Falling back to old probe method for modesetting[br]
[    37.085] (WW) Falling back to old probe method for fbdev[br]
[    37.085] (II) Loading sub module "fbdevhw"[br]
[    37.085] (II) LoadModule: "fbdevhw"[br]
[    37.085] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so[br]
[    37.096] (II) Module fbdevhw: vendor="X.Org Foundation"[br]
[    37.096]    compiled for 1.18.3, module version = 0.0.2[br]
[    37.096]    ABI class: X.Org Video Driver, version 20.0[br]
[    37.096] (EE) open /dev/fb0: Permission denied[br]
[    37.096] (WW) Falling back to old probe method for vesa[br]
[    37.096] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support[br]
[    37.096] (**) RADEON(0): Depth 24, (--) framebuffer bpp 32[br]
[    37.096] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)[br]
[    37.096] (==) RADEON(0): Default visual is TrueColor[br]
[    37.096] (==) RADEON(0): RGB weight 888[br]
[    37.096] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)[br]
[    37.096] (--) RADEON(0): Chipset: "OLAND" (ChipID = 0x6610)[br]
[    37.096] (II) Loading sub module "fb"[br]
[    37.096] (II) LoadModule: "fb"[br]
[    37.096] (II) Loading /usr/lib/xorg/modules/libfb.so[br]
[    37.102] (II) Module fb: vendor="X.Org Foundation"[br]
[    37.102]    compiled for 1.18.3, module version = 1.0.0[br]
[    37.102]    ABI class: X.Org ANSI C Emulation, version 0.4[br][br]
```

I'm having trouble uploading the entire log file.

---

### Post by Tom_Kidman on 2016-04-28
This bug looks like it could be related, even though it's about installing fresh from install media and not an upgrade - [https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/1571564](https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/1571564)

---

### Post by dpeets on 2016-04-29
Filed a new one just in case, we'll see what happens:
[https://bugs.launchpad.net/ubuntu/+source/plasma-desktop/+bug/1576500](https://bugs.launchpad.net/ubuntu/+source/plasma-desktop/+bug/1576500)

---

### Post by dpeets on 2016-05-06
There's a solution that's worked for at least two of us so far: See comment #13 at [https://bugs.launchpad.net/ubuntu/+source/plasma-desktop/+bug/1576500](https://bugs.launchpad.net/ubuntu/+source/plasma-desktop/+bug/1576500)

---

