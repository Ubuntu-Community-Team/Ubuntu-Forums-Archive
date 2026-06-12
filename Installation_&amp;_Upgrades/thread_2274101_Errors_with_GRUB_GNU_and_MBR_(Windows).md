---
title: "Errors with GRUB GNU and MBR (Windows)"
date: 2015-04-17
forum: Installation &amp; Upgrades
---

### Post by jack133 on 2015-04-17
Sorry If I'm not in the right room/section.
I recently tried installing Ubuntu and dualbooting it. I selected the  "install alongside Windows 7" option and created a ~60GB partition, and  it followed through well. When I wanted to return to Windows, though,  GRUB GNU would select it but return to the menu shortly after, so I  uninstalled Ubuntu (via "Try Ubuntu" from USB) with OS-Remover. Now,  when I try to boot from HDD, it gives me "error: unknown filesystem" and  is stuck in grub restore mode. I have tried the following:

  -Used Boot Repair from Ubuntu (USB)
  -Inserted an installation USB and tried bootrec /fixmbr and bootrec  /fixboot, says successful yet only made the USB unbootable and had to  reformat and burn, still brings to grub rescue
  -Tried burning eBCD (wouldn't boot)
  -Doing "cd boot" from CMD via installation USB gives me an error saying the path doesn't exist
  -Tried a multitude of other tutorials
  Can someone help me completely remove GRUB and restore MBR? Help would be much appreciated. Thanks!

---

### Post by oldfred on 2015-04-17
It sounds like your fixmbr & fix boot were run on flash drive not on hard drive.
Do you have boot flag on the Windows partition with boot files, usually the 100MB boot partition but could be the main install or c: "drive". 

Boot-Repair should have just installed a Windows boot loader to the MBR when you uninstalled.
Run the Summary Repair from Boot-Repair and post link it gives to pastebin entry.

---

