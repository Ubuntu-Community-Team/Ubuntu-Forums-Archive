---
title: "Install Ubuntu 10.04 on powerpc ibook g3"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by rfabian on 2010-07-26
Ok,
I created an installation cd of 10.04 powerpc. I managed to get the mac to boot off the cd and ubuntu ran successfully. I have tried to install the software onto the hard disk but have hit a snag.
The software appeared to install correctly but I cant boot into the gui.
The system boots up as far as the ubunto logo and moving dots. When these disappear I get a blank screen and the computer just sits there.
If I hit ctrl-option-f1 I can get to the terminal.
I am told it might be a problem with the xorg.conf file (which the system does not generate) The graphics card appears to be a ati m7 lw radeon mobility 7500.
Any ideas ?

---

### Post by dante.jones on 2010-07-27
Hi rfabian,

Unfortunately there seems to be regression in the Ubuntu support for Radeon Mobility 7500 in 10.04. I have this graphics card in a Thinkpad T42, and it's causing me much frustration attempting to have it perform as power efficiently with decent graphic speeds, as delivered in Ubuntu 8.04. It's especially power hungry in suspend sleep.

KMS might be the source of your display problems. You could test and see without rebooting, by running this from a virtual console:

```
$ sudo stop gdm
$ sudo modprobe -r radeon drm
$ sudo modprobe radeon modeset=0
$ sudo start gdm
```

If this helps, then you can commit the changes by using your favourite text editor (I'm using vim as an example) and making this file:

```
$ sudo vim /etc/modprobe.d/radeon-kms.conf
```

Within this file add these lines:

```
# Prevent KMS from loading
options radeon modeset=0
```

Then to commit these changes, rebuild initrd.img~ by using:

```
sudo update-initramfs -u
```

and reboot.

Some more KMS details are available here:

[INDENT][https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting")[/INDENT]

Hope that helps for starters.

---

### Post by gordo on 2010-09-06
Thanks! It worked for me (900 mhz G3 iBook).

---

