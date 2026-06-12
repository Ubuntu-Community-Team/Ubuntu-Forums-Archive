---
title: "Lenovo X201 workaround that works"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by allaboutsam on 2010-08-22
Finally got my Lenovo X201 up and running by combining a couple of different workarounds suggested for the graphics driver problem that is plaguing so many.

This works on my X201 3249CTO, running BIOS version 1.17, with Ubuntu 10.04.1 (kernel version 2.6.32-24). I have tested it to differing degrees with all four relevant installers (32- and 64-bit, desktop and alternate).

STEP 1. Add "xforcevesa i915.modeset=0" at install.
--When you first start the desktop installer, you should see "ISOLINUX..." in the upper lefthand corner of the screen, followed by a couple of white logos at the bottom of an otherwise blank screen. As soon as you see these logos, press the space bar to get the advanced install menu. If you are using the alternate installer, you will get the install menu automatically.
--Make sure "Install Ubuntu" is highlighted.
--Press F6. You should see the install command line near the bottom of the screen, plus a popup menu with additional options.
--Pres Esc to close the popup menu. A cursor should appear at the end of the install command line.
--Type "xforcevesa i915.modeset=0" (without the quotes), and press enter.
--Install Ubuntu as usual.
--Shut down your computer.

STEP 2. Configure grub to use "xforcevesa i915.modeset=0" at startup.
--Start up your computer and boot into recovery mode. To do this, press and hold the shift key as soon as the BIOS splash screen finishes displaying. You should see the grub boot menu. Use the up and down arrows to select "recovery mode," and press enter.
--At the recovery menu, select "failsafeX - Run in failsafe graphics mode" and press enter.
--At the "Ubuntu is running in low-graphics mode" warning, press okay.
--At the next popup menu, select "Run Ubuntu in low-graphics mode for just one session."
--Ubuntu should boot normally. Log in as usual.
--sudo into your favorite text editor, open /etc/default/grub, and edit the GRUB_CMDLINE_LINUX= line to read GRUB_CMDLINE_LINUX="xforcevesa i915.modeset=0" (with the quotes).
--Save changes and close the text editor.
--Open a terminal, and type "sudo update-grub" (without the quotes). You should get a few lines of output, then "done."
--Close the terminal and restart your computer.

(Thanks to Dennis Stone at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569") for steps #1-2.)

STEP 3. Configure X to use failsafe graphics mode by default.
--Boot into recovery mode as above.
--At the recovery menu, scroll down and select "root - Drop to root shell prompt."
--At the prompt, type "X -configure" (without the quotes), and press enter. This should create a file at /root/xorg.conf.new .
--Using vi, open xorg.conf.new, find the line that says Driver "intel" in the device section with Boardname "Core Processor Integrated Graphics Controller", and edit it to read Driver "vesa" (with the quotes).
--Save changes and exit vi.
--If you already have a file at /etc/X11/xorg.conf, this would be a good time to back it up.
--Then move or copy /root/xorg.conf.new to /etc/X11/xorg.conf.
--When you are finished, restart your computer and it should run normally--or normally enough for use, at any rate.

(Thanks to [this post]("http://www.uluga.ubuntuforums.org/showthread.php?t=1553412") for step #3.)

I don't see this as a true fix, but as a workaround that enables me to use my new computer until a true fix is available for installation without the need to compile a custom kernel.

Please post if it works or doesn't work!
allaboutsam

---

### Post by droople on 2010-08-28
Nope, it seems step 2 sometimes working, sometimes not :(

---

### Post by allaboutsam on 2010-08-28
Oh, well. Sorry!

---

### Post by luraze on 2010-09-02
Is seems that everything is working with the new kernel update (2.6.32-25). First you need to remove the boot parameter (i915.modeset=0) from the grub config.

Now I can use the brightnesskeys, watch streamed videos i fullscreen without lag, and have desktop effects enabled (compiz).

On the downside (well, maybe its just my imagination), the battery is charging incredibly slow. Wireless is still a little unstable (had major problems with this before the kernel update), but seems like it has been improved.

---

