---
title: "usb in virtualbox"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by wvreeuwijk on 2008-04-30
Somehow I got my USB drive to work in a virtual Windows XP under Gutsy. The upgrade to Hardy went quick and OK.  I had to setup the virtualbox driver again (like it said) The virtual windows  XP is up and running but...... it only recognises my Epson scanner and absolutely refuses to recognise my USB stick drive (8 GB). The drive works OK under Ubuntu itself.
I made all the adaptions that I found on the web (the same I once had to do for Gutsy) but still does not work.Anybody........?????

---

### Post by amujunen on 2008-05-08
> **wvreeuwijk said:**
> Somehow I got my USB drive to work in a virtual Windows XP under Gutsy.

The same applies to me, too.  I was able to use an USB stick with virtualbox-1.5 and gutsy "as is".

> **wvreeuwijk said:**
> The upgrade to Hardy went quick and OK.

Equally well, I'd say, very smoothly.  I upgraded to Sun's "branded" virtualbox-1.6 at this time.

> **wvreeuwijk said:**
>   I had to setup the virtualbox driver again (like it said) The virtual windows  XP is up and running but...... it only recognises my Epson scanner and absolutely refuses to recognise my USB stick drive (8 GB).

I tried to do the same modifications but I think what happended is that the usbfs (/proc/bus/usb/...) entries now don't get the group ownership of usbusers (or as I chose to use it, vboxusers) but are still owned by root.root.  I don't really know how to "correctly " fix this in udev config files...

By reading the VirtualBox internal help on USB devices I was able to determine that in addition to having rw permissions with the VirtualBox user account privileges, the USB device must be in an "unclaimed" state by the Linux host.  This can be checked by looking at the 'Driver=...' entry in output of 'cat /proc/bus/usb/devices' at the point of the USB device that you wish to use.

My stick was with root.root; I changed it temporarily with just 'chown root.vboxusers /proc/bus/usb/002/007' (note that I use the same group vboxusers for USB as well as for VirtualBox usage in general and that the correct numbers to use was revealed by a 'lsusb' command showing the bus number 002 and device number there 007).  These temporary chowns will of course disappear with the next re-inster/reboot/whatever..

Now, this might have been sufficient, though in my experiments I had previously unplugged all my usb_storage devices and 'sudo rmmod usb_storage', ensuring that the "Driver=..." field is "unclaimed", "Driver=(none)".  This might not be necessary, though, VirtualBox might be clever enough to "unclaim" the device from its Linux host driver (though I couldn't find any std command to do that manually from command line).  (I haven't tried in VirtualBox is this clever, though, I'm just extrapolating that I apparently could do this in 1.5 before...)

Anyway, with "Driver=(none)" in /proc/bus/usb/devices and the /proc/bus/usb/nnn/nnn entry having permissive enough ownership for the VirtualBox user, then I was able to fire up VirtualBox command and then the (carefully unmounted) USB stick finally appeared inside the virtual machine for which I had added the USB filter matching the particular stick I was using.  I'm currently installing Hardy onto a 4GB stick, hoping to be able to create a bootablel "Hardy-stick"...

Cheers,
Ari Mujunen

---

