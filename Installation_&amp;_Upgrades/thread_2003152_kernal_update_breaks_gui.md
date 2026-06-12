---
title: "kernal update breaks gui"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by McMuffin1892 on 2012-06-13
I recently installed 12.04 (fresh new installation) and of course the updates have to start. Updating the kernel caused by GUI to break. It tells me my system has been placed in "low-graphics mode"--but there's no graphics at all, just the terminal.

My graphics driver is one of the ones that has to be enabled with the restricted driver thingy.

an attempt to run an update from the new kernel's command line didn't work, because it couldn't connect to the net... I think my wireless driver too doesn't work with the new kernel.

For now, I'm using GRUB to boot into the old pre-update kernel. Is there a fix to this problem, and if there isn't yet, is it possible to change GRUB so it automatically boots into this old kernel every time?

---

### Post by QIII on 2012-06-13
Problems with thingies, doohickies and whatchmacallits are fiendishly difficult to troubleshoot.

Could you give us a little more information about your hardware?

---

### Post by McMuffin1892 on 2012-06-13
Sorry. Guess I wasn't being specific enough .

The driver that is being used is called the "ATI/AMD properitary FGLRX graphics driver". Not sure what model the graphics card is.

The laptop as a whole is a HP Pavilion dv7

---

### Post by QIII on 2012-06-14
If you used the "Additional Drivers" route, two things may be going on.

1.  You did not immediately execute
```
sudo aticonfig --initial
```
In the terminal after installation.  This is not supposed to be necessary, but it seems that the Additional Drivers method does not always do it correctly.  The kernel may have updated and may still be loading the driver module, but it may not have marching orders without the file that command creates.

2.  For random and inexplicable reasons the Additional Drivers method sometimes does not work for some users.

Try to do the command I gave and reboot.  Tell me what happens.

If nothing changes, then go to the link in my signature for instruction on how to go around the Additional drivers method while staying in the Ubuntu repositories.

If you are not experienced, I would say to avoid instructions to go to ATIs website, download and extract the file, etc, etc.

---

### Post by McMuffin1892 on 2012-06-15
Okay, so the GUI problem seemed to fix itself on its own. As in, I booted the next day and it worked fine:confused:

Wireless driver doesn't work with new kernel (using ethernet now). It uses the Broadcom STA Wireless Driver; when I try to activate the driver in Additional Drivers it gives me a "Sorry, activation of this driver has failed" error.

Here's the logfile of it from the /var/log/jockey.log the error dialog referred me to:

2012-06-15 02:34:07,310 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-15 02:34:07,311 DEBUG: fglrx_updates is not the alternative in use
2012-06-15 02:34:07,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-06-15 02:34:07,413 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-15 02:34:07,414 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-15 02:34:07,699 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-06-15 02:34:07,800 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-15 02:34:07,801 DEBUG: fglrx_updates is not the alternative in use
2012-06-15 02:34:07,831 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-06-15 02:34:07,891 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-15 02:34:07,891 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-15 02:34:11,449 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-06-15 02:34:11,886 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-06-15 02:34:11,887 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-06-15 02:34:11,928 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

---

### Post by McMuffin1892 on 2012-06-15
Nvm. Poked around the forums for solutions to wireless problems, and this worked like a charm:

sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl

Appears that I have the latest kernel working fine now. Thanks to all for help.

---

