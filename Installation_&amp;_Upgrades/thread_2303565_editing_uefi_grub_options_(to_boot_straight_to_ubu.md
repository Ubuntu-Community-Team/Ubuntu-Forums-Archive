---
title: "editing uefi grub options (to boot straight to ubuntu 14.04)"
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by Hodor on 2015-11-19
[COLOR=#000000]I've tried the suggestions in this the following thread, no joy: [/COLOR]http://ubuntuforums.org/showthread.php?t=2298577

[COLOR=#000000]At /etc/default/grub I have the following (excluding commented lines)[/COLOR]
[COLOR=#000000]Code:
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
GRUB_CMDLINE_LINUX=""
[/COLOR]
[COLOR=#000000]after updating I ran sudo update-grub and rebooted (a few times for good measure) - still the grub menu[/COLOR]

[COLOR=#000000]I have a dual boot setup but only ever boot into ubuntu from the grub menu.[/COLOR]
[COLOR=#000000]Is there an alternative configuration file that sometimes gets used?[/COLOR]

---

