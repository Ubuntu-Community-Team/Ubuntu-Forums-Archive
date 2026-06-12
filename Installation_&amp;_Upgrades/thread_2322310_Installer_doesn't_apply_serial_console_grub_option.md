---
title: "Installer doesn't apply serial console grub options"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by Eric_van_Vliet on 2016-04-27
Hi,

As long I can remember ubuntu, if installed over serial console redirection (console=ttyS0,115200), the installer would automatically add these kernel option to the freshly installed GRUB.

I install over PXE, using the network installer kernel & initrd.gz with the following commands.

#Ubuntu 16.04 LTS x86_64
LABEL ubuntu1604lts_64
MENU LABEL Ubuntu 16.04 LTS x86_64
KERNEL images/ubuntu/16.04LTS/x86_64/linux
APPEND tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false text initrd=images/ubuntu/16.04LTS/x86_64/initrd.gz console=ttyS0,115200


Worked fine with 12.04/14.04, however I now install 16.04 and it doesn't.

Of course I solve this by not rebooting the system, executing a shell in the installer and manually updating the /boot/grub/grub.cfg. 
Upon first boot adding it to /etc/default/grub and running update-grub, to make sure on upon kernel update it won't be removed.

Is there something I need to add to the kernel options of the installer of 16.04?
Eric

---

### Post by stefan.hausmann on 2016-05-02
Hi Eric,

I've had the same problem recently - just check [https://help.ubuntu.com/16.04/installation-guide/amd64/ch05s03.html#boot-console](https://help.ubuntu.com/16.04/installation-guide/amd64/ch05s03.html#boot-console) for what to do.

Quote: "[COLOR=#000000][FONT=liberation sans]You may need to specify parameters for the serial port, such as speed and parity, for instance [/FONT][/COLOR]**console=ttyS0,9600n8**[COLOR=#000000][FONT=liberation sans]; other typical speeds may be 57600 or 115200. Be sure to specify this option after [/FONT][/COLOR][COLOR=#000000][FONT=liberation sans]“---”[/FONT][/COLOR][COLOR=#000000][FONT=liberation sans], so that it is copied into the bootloader configuration for the installed system (if supported by the installer for the bootloader).[/FONT][/COLOR]"

So "APPEND tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false text initrd=images/ubuntu/16.04LTS/x86_64/initrd.gz --- console=ttyS0,115200"

should work!

Stefan

---

### Post by Eric_van_Vliet on 2016-05-19
works thanks!

---

