---
title: "Issues Installing 16.04 on Custom Rig"
date: 2016-08-10
forum: Installation &amp; Upgrades
---

### Post by drcrook on 2016-08-10
Hey All,

I'm setting up my new rig for deep learning and want to put 16.04 on it.  I set up a rufus USB drive and am attempting to install.  On boot I get the options "install ubuntu", "check disk" etc.  Unfortunately when I select anything, the screen blanks out and nothing happens.

Here is the pc parts list if it helps...
[http://pcpartpicker.com/list/dJkYHN](http://pcpartpicker.com/list/dJkYHN) 

Thanks,
~David

P.S.  The TitanX's are the new ones.

P.S.S.  Decided to try to re-install Ubuntu onto the USB, the newest rufus throws me this issue: 
Deleting partitions...
Partitioning (MBR)...
Could not set drive layout: [0x00000032] The request is not supported.

---

### Post by ubfan1 on 2016-08-10
Well, starting with "nomodeset", you have a lot of options to try to get the video working.  There are lots of threads listing them, and newer ones with every new card.  At the try/install screen, type "e" to edit the boot commands, and add the option(s) on the linux kernel boot line.

---

### Post by oldfred on 2016-08-10
With my older Asus Z97, I could only get it to boot in UEFI mode with the UEFI setting UEFI only, not even UEFI & CSM. And changed other settings to UEFI only.
I also had to allow USB full support for boot.
I also turned off fast boot. Later I set warm reboot to fast boot but kept cold boot to normal.
Turned off network boot as I would not use that and saw no reason for it to try to search network.
I had to change OS type to "Other" not "Windows" which really is the secure boot setting.

I had to make a list of these settings as every UEFI update, reset to defaults and system would not work. Also make sure you have newest UEFI from Asus.

Then since you have nVidia, you need ubfan1's suggestions on nomodeset to see if you can boot in low quality graphics mode. Some with newer motherboards found it easier to use internal Intel video to install and then add nVidia drivers. But it looks like X99 does not have any Intel video.

I see it uses Asmedia. Some others have had issues with drivers for that.

---

