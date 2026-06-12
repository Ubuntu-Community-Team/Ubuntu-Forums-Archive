---
title: "No graphics/no boot after upgrade"
date: 2017-08-01
forum: Installation &amp; Upgrades
---

### Post by martinkellner on 2017-08-01
My girlfriend updated my 14.04 system to 17.04. At least I think that is what it is. At first I got an error message saying it couldn't find a backlight controller and it wouldn't start the GUI. After specifying nomodeset in /etc/default/grub, the latest kernel (4.4 something) failed to boot completely even in recovery mode. The problem persisted even when I removed nomodeset. Older kernels would boot, but only to command line. Manually trying to start lightdm would lock the computer and this is where I stand now. Any suggestions?

---

### Post by martinkellner on 2017-08-01
And I should have said this is a HP Envy running a dual boot with Windows 10.

---

