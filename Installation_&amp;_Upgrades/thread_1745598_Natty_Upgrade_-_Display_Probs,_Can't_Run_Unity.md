---
title: "Natty Upgrade - Display Probs, Can't Run Unity"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Wlo on 2011-05-01
Hi all.

I've upgraded my Thinkpad T420 from Maverick to Natty by downloading the alternate ISO and upgrading. I'm having problems though.  The installation seemed to go okay, but upon rebooting the display was at a diagonal slant and wrapped around.  I can boot into safe graphics mode using the recovery grub option and things work fine (without Unity).

If i open the nvidia-x-server-settings app I get a message which says:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I run sudo nvidia-xconfig and get:

--->
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
<---

I think this has done something useful as if I run it again I just get:

--->
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
<---

If I reboot after this the machine hang on "Checking battery state" before displaying the GUI.

I've done this an experimented with a few different things.  Downloaded and enabled the nvidia proprietary drivers.  This didn't help either.

Any ideas?

Thanks!

Wlo.

---

### Post by Wlo on 2011-05-01
Oh, just to add, I've disabled Optimus graphics in the BIOS and am just using Discrete as I needed to do this for Maverick to install and it seems all round more straightforward for getting this to work.

---

### Post by Wlo on 2011-05-01
Found something which helped in this thread, [http://ubuntuforums.org/showthread.php?t=1726575](http://ubuntuforums.org/showthread.php?t=1726575) .

It was autodetecting and resetting to Optimus each time in the bios.  Fixed now.

---

