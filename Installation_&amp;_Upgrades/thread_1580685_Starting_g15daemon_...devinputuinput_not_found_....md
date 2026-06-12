---
title: "Starting g15daemon: .../dev/input/uinput not found ..."
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by Recon20k on 2010-09-23
I'm having alot of diffuculty with g15daemon since i installed it for using the wireless logitech

The following error message is one i get consistently when installing other programs:

Starting g15daemon: .../dev/input/uinput not found ...

Any ideas how to fix this?

thanks in advance :)

---

### Post by efflandt on 2010-09-23
I thought g15daemon was supposed to support the g13 now.  But I could not even install the g15daemon version from Synaptic in Lucid because it is looking for the wrong (old?) path to non-existing /dev/input/uinput (it is actually at /dev/uinput).  I tried symlinking it where it was looking for it:

cd /dev/input
sudo ln -s ../uinput .

That got rid of the error about missing /dev/input/uinput, but it still would not install and configure completely.  Maybe g13 is not properly supported by it yet, and it could not find a real g15.  Either that or the symlink doesn't really satisfy it.  If g15daemon works properly it is supposed to put a clock on the gamepad LCD display.

I did find sources of something else specifically for the g13 (which also uses uinput) and after I compiled that it works up to a point, setting graphics on the LCD, colors, and assigning keys (which respond).  But it is missing details about what to put in /lib/udev/rules.d to set proper permissions of the named pipes (like files).  So the g13 daemon only runs for a period of time before it exits with -9 error.

---

