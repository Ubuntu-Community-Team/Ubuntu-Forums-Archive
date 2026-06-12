---
title: "Upgrade from 14.04 to 16.04. Mysql server error. System won't boot even failsafe."
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by wogga on 2016-08-30
I had been behind on updates for a while. Old kernels piled up in /boot - i run encrypted. Graphical software updater was giving me the 'not enough free space in boot' message. 

I reset "[COLOR=#333333][FONT=UbuntuMono]Unattended-Upgrade::Remove-Unused-Dependencies "false";"
[/FONT][/COLOR]
To "true". 

I ran sudo apt-get autoremove --purge and sudo purge-old-kernels and sudo apt-get update. Afer doing so, the graphical software updater ran without giving me the 'not enough free space in boot' error. Ran it twice. 

Then i ran the upgrade to 16.04. At the end of the install i got an error message about mysql server, with only the option to click 'ok'. I finished the upgrade with that being the only reported error. The system would not restart; would not power down. I manually shut down the system with the physical power button. 

Now the system won't boot even in failsafe graphical. In normal boot, i get the crypt unlock prompt, enter passphrase, then it flashes between a black screen, ubuntu progress screen, command prompt, and a blinking command cursor. No boot. 

What do i do now??? Please help.

EDIT:

When i run dpkg in recovery mode, i ge this error:
[FAILED] Failed to activate swap /dev/mapper/ubuntu--vg-swap_1.
see 'systemctl status "dev-mapper-ubunt...\x2dvg\\x2dswap_1.swap"' for details.
[DEPEND] Dependency failed for Swap

---

