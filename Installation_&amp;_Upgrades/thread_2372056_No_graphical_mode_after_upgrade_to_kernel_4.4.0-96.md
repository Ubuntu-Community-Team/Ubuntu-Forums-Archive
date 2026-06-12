---
title: "No graphical mode after upgrade to kernel 4.4.0-96 -DELL Latitude 3550,Ubuntu 16.04.3"
date: 2017-09-21
forum: Installation &amp; Upgrades
---

### Post by konstant@mail.ntua.gr on 2017-09-21
After upgrading from 4.4.0-93 -> 4.4.0-96 (the default update using the Software Updater yesterday), I get the following:

1. A menu:
    The system is running in low-graphics mode
    Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself.
2. I press OK and obtain a new one offering choices:
    What would you like to do?
      Try running with default graphical mode
      Reconfigure graphics
      Troubleshoot the error
      Exit to console login

At this point **I cannot use the mouse/touchpad/keyboard at all** to make a choice or press ENTER to continue. After pressing ESC I get the black screen with boot messages:

/dev/sda2: clean xxxx/xxxx files, xxx/xxx blocks
. bbswitch: No suitable _DSM call found.
. bbswitch: No suitable _DSM call found.
. bbswitch: No suitable _DSM call found.
. bbswitch: No suitable _DSM call found.
. bbswitch: No suitable _DSM call found.
............... indefinitely .......
Then I press the switch button to reboot.

I cannot find a way out, so I reverted to kernel 4.4.0-93 and everything seems back to normal.
================================================================
A reminder to all panicked visitors on how to revert to the previous kernel:
. reboot
. If the GRUB menu does not show (like in my case, I only have Ubuntu), hit ESC once
. Choose Advanced Options for Ubuntu and from the menu pick the kernel that works for you (in my case 4.4.0-93)
After you boot, uninstall the unwanted kernel and update the grub menu: (everything after > is a command line)
>  dpkg --list | grep linux-image                                                                       [COLOR="#696969"] *(select the packages relevant for you and add them to the next line instead of my *4.4.0-96* packages)*[/COLOR]
> apt-get remove linux-image-extra-4.4.0-96-generic linux-headers-4.4.0-96 linux-image-4.4.0-96-generic linux-signed-image-4.4.0-96-generic
> update-grub
================================================================
Information on my laptop:

DELL Latitude 3550
Ubuntu 16.04.3 LTS
kernel that works: Linux 4.4.0-93-generic #116-Ubuntu SMP Fri Aug 11 21:17:51 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

The output of the commands lshw , lspci , lsusb, lsmod is attached to the corresponding files.

(Note: they are created on the 4.4.0-93 working environment. The second monitor is irrelevant, the problem persists when the laptop is not attached to anything - mouse,keyboard,monitor, ...)

---

### Post by konstant@mail.ntua.gr on 2017-09-21
Related??: [https://askubuntu.com/questions/887682/low-graphics-mode-after-16-04-2-hwe-upgrade](https://askubuntu.com/questions/887682/low-graphics-mode-after-16-04-2-hwe-upgrade)

---

### Post by crononauta on 2017-09-25
Same here on Acer Aspire E17.
It seems something broken in bbswitch, for in older kernel it works.
It's not a solution the change to nouveau, for the bbswitch is broken when loaded in the kernel. It doesn't matter which driver (nouveau or nvidia) you are using.
I think the issue il kernel-related for xrandr --listproviders shows *just one* card with kernel 4.4.0-96, while the same with older kernel shows correctly the *two *card (the integrated and the discrete one).
It looks like for whatever reason, the 4.4.0-96 kernel is not able to access properly the graphic card.

---

### Post by viktor-engelmann on 2017-09-27
After "upgrading" to kernel 4.4.0-96, my screen flickered like crazy.
 primarily at the window borders and title bar of chromium-browser (also google-chrome-stable, but not as bad).
and when dragging the chromium-browser or google-chrome-stable around, the pages flicker badly.
The flickering also happens on other windows, if chromium-browser/google-chrome-stable are behind them.
Passing "nomodeset" to the kernel (added that in /boot/grub/grub.cfg) stopped the flickering, but now everything is very slow (14 FPS on WebGL example "aquarium" with 1 fish)

interrestingly, glxgears claims it had 1000 fps, but you can see it being choppy, so that number can't be right.

here is the relevant part of lspci
[FONT=monospace]> [COLOR=#000000]00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)[/COLOR]
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

I'm using KDE Plasma 5, all packages are up to date.
[/FONT]

---

### Post by viktor-engelmann on 2017-09-27
Ah, in systemsettings -> Display and Monitor -> Compositor, setting "Rendering backend" to OpenGL 3.1 solved the issue for me (it was set to OpenGL 2.0 before)

---

### Post by sirtetris on 2017-09-29
I have the exact same problem as described in the frist post on a Lenovo U430p.
Switched to an ealier kernel version for now and everything is back to working normally.

---

