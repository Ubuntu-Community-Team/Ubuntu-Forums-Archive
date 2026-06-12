---
title: "Upgrade from 14.04 to 16.04 failed. IrDA: script fa"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by leozinho29_eu on 2016-04-30
Hello

I tried to upgrade my notebook to Lubuntu 16.04 from 14.04 and it failed. It is a ASUS M2400N. To upgrade it from 12.04 to 14.04, I had to add the PAE flag and had to install the linux-image-generic-pae. Here is the summary from hardinfo.

```

-Computer-
Processor        : Intel(R) Pentium(R) M processor 1.70GHz
Memory        : 1248MB (465MB used)
Operating System        : Ubuntu 14.04.4 LTS
User Name        : user (User)
Date/Time        : Sex 29 Abr 2016 19:06:34 BRT
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : ICH4 - Intel 82801DB-ICH4
-Input Devices-
 Sleep Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 SynPS/2 Synaptics TouchPad
 Video Bus
 Asus Laptop extra buttons
-Printers-
No printers found
-SCSI Disks-
ATA WDC WD1600BEVE-0
TOSHIBA DVD-ROM SD-R2512


```


Due to minor problems which I was having, as the first letter in searches being ignored, a part where the boot stopped for a long time (ASUS_laptop CWAP, I'm unsure right now), missing icons, well, many minor things, I decided to upgrade the system. It worked with my desktop perfectly, so I supposed it would be fine to upgrade the notebook too.

It wasn't.

There was a part where I was sure there would be errors: the kernel upgrade. And there were errors, but the upgrade was still fine. However, when installing IrDA, the computer froze. Completely froze. When I am using the notebook, it's normal to hear when the processor is working. It completely stopped, the disk stopped, nor NumLock nor CapsLock were working, Ctrl+Alt+Fnumber didn't work. Absolutely nothing was working. After a long time, I had to turn it off keeping the shutdown button pressed and it took a long time (longer than other times) to turn off.

Sadly, the lxtask window was partly in front of the terminal. I was able to read " IrDA: script fa" only. I suppose it "failed".

Obviously, the system was no longer booting, but I was able to restore the files and the configurations. Now I am with 14.04 version using forcepae instead of a PAE kernel. It is faster now and there are no longer that annoying bugs, probably the upgrade from 12.04 to 14.04 was not that smooth as I imagined or the PAE kernel was problematic.

I am posting this here because there is no log, so I don't have much technical information about.

Thank you.

---

### Post by mörgæs on 2016-05-01
If you consider a fresh install of 16.04 here is a guide:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by Autodave on 2016-05-01
I have used Ubuntu and Xubuntu for years. I was hoping that the newest upgrade to 16.04 would work, but after trying 8 different machines so far, it only worked on 1 machine and I had to re-install a couple programs even then. Sadly, my advice to you is to wipe it and start on a fresh install.  Save what you can and then do a clean install.

---

### Post by leozinho29_eu on 2016-05-02
I am aware about the PAE issue. Gladly, the solution using forcepae is way better than a PAE kernel. I have reinstalled Lubuntu 14.04 and it is working better than before. Thank you.

However, the computer has a really strange behavior when I try to install or test the Lubuntu 16.04 from a pen-drive: the window to choose to test or to install the system appears, I click to choose to test and then it returns to the command line options (that options are systemd, I suppose) and stops, never access the graphical interface again, and I can't even change the consoles (Ctrl+Alt+Fnumber). Here is a photo of the screen where it stopped. The 46s stopped too, so the timer froze too.

[IMG]http://i.imgur.com/CB3YhxF.jpg[/IMG]

Ubuntu 16.04 completes the boot, and I can access the graphical interface, but it demands so much, so much resources that it is barely usable. When I try to use the lateral bar, compiz uses the whole CPU when I search the bottom icons, and when I press the "start" button, it needs more than 5 seconds to start the animation and another 10 seconds to finish the animation, it is slow to search and the icons never appear.

[IMG]http://i.imgur.com/zDeJjij.jpg[/IMG]

I know that a workaround would be to after installing Ubuntu 16.04 install the lxde package, but there would be so much configuration to do that it would be annoying.

From the 16.04 versions, Lubuntu has this problem, but Ubuntu don't. I should test if Xubuntu has it too later (Lubuntu uses xfce4-power-manager, and it stopped in the power management part, looks like) to see if this is a Lubuntu-only issue or not.

And I still can't use the infrared interface of my notebook ;-;

PS.: to boot the 16.04 systems, I removed "quiet splash" and added "forcepae -- forcepae" in the boot lines.

---

