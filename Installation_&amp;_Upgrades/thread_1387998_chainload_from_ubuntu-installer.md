---
title: "chainload from ubuntu-installer"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by jandersonlee on 2010-01-22
I'm trying to set up an Ubuntu 9.10 amd64 (actually Nehalem) server cluster in a remote location.  We need to be able to do remote installs/reinstalls using just PXE boot and a serial console server.  I've managed to preseed most of the install.  The trouble I have is that the console server doesn't encode/transmit Fxx function-keys in a way that the nodes understand, so I cannot press F12 to PXE boot when I need a reinstall.  Go in to tweak the bios boot order each time would be possible, but painful.

I'd like to set it up so that the PXE-boot brings up the ubuntu-installer, but add a "boot from first disk" option to the boot/install menu and make it the default with a timeout of 30 seconds.  That way if a system reboots, the default action will be to restart the installed OS, but if I deliberately reboot it and monitor the serial console, I can see the boot menus and force a preseeded reinstall.

I'm trying to figure out how to tweak ubuntu-installer/amd64/boot-screens/* to add this hack.  So far I've not found the appropriate documentation or sample code.  Is it even possible?  (I believe some of the CDs have that option.)

Once I have that working, the next step would be to get rid of the "graphical" boot menus and make them strictly textual so that *all* the boot menus get displayed to the serial console port as well as to the screen.

Thanks in Advance.

---

### Post by jandersonlee on 2010-01-22
Step 1: added the following to text.cfg
```
timeout 300
label ^diskboot: Boot from local disk
        menu default
        localboot 0

```

Now I get a functional option to chain to the local disk (so long as booting from the local disk is a viable option in the bios boot order after PXE boot).  

I had to change **all** the "timeout 0" to "timeout 300" in other .cfg files as well as in the original pxeboot.cfg/default to get it to not hang at the menu forever.

Any suggestions on getting the menu text to show on the serial console port?

---

### Post by jandersonlee on 2010-01-22
I found a SYSLINUX wiki site which documents the PXELINUX.0 boot configuration file formats.  I ended up scraping most of the default multi-file menu system.  By putting a simple menu in the pxelinux.cfg/default file and adding "SERIAL 0 57600 0" and "SAY enter 'local' for local boot, 'install' to reinstall" commands I was able to get it to prompt me over the serial console port as well as on the console display.

---

### Post by jandersonlee on 2010-01-22
Added "console=ttyS0,57600" to the kernel parameters for the installation option and now I can watch the install progress on the serial console port. Sweet. :)

---

