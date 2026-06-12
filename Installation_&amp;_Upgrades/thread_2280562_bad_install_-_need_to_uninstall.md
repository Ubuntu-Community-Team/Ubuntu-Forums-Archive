---
title: "bad install - need to uninstall"
date: 2015-05-31
forum: Installation &amp; Upgrades
---

### Post by Lewis_fulkerson on 2015-05-31
I accidentally installed Ubuntu 14 onto the removable hard drive plugged into a USB port, so now if I remove that drive, my computer will not boot. How can I Uninstall Ubuntu 14, remove the drive and reinstall alongside Windows 7 Professional?

---

### Post by papibe on 2015-05-31
Hi Lewis_fulkerson. Welcome to the forum ):P

**Reinstall:**

Unplug the external USB disk and boot into the installation media and install Ubuntu. Be careful not to remove Windows (In order to boot from the installation media, you don't need the external disk).

**If you want to recover your Windows ASAP:**

I recommend reinstalling/reconfiguring grub so that exclude the external drive and only discover the drivers you want (even a disk with only Windows).

Unplug the external USB drive. Boot into the live media, and select 'Try Ubuntu' instead on install. When you get to the desktop follow this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") to repair/reinstall grub. Since the external drive is not available, grub would not include it, and would only recognize the local OSes (like Windows 7).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Mike_Walsh on 2015-05-31
Hallo, Lewis.

Hmm. Hardly surprising; as part of the install process, Ubuntu will have installed GRUB2 to the root of the partition it's just installed the system to. And GRUB2 takes over the boot -loader duties of any other systems you have installed. Just use gParted to delete the install from the external drive.....but AFTER installing it on the main drive. You'll need to leave it there while you're sorting the 'proper' install out.

We'll need to see what your Windows install looks like. Can you use Gparted to view your main drive.....and post a screenshot? It would be quite helpful. (I do things a little bit differently to many others. I know the command-line is the preferred method.....but I know newcomers are usually used to GUI stuff.....so that's what I prefer to work with.) 

Your main drive is usually 'sda'.


Regards,

Mike. :)

---

