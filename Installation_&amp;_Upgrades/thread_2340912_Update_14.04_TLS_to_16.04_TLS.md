---
title: "Update 14.04 TLS to 16.04 TLS"
date: 2016-10-23
forum: Installation &amp; Upgrades
---

### Post by sharbich on 2016-10-23
Hi all,

after the Update i can only boot the System over the "Upstat" Menu in the Grub Bootmanager. When  I start over the Standard generic Boot Menü the System hold on the black Monitor. Okay, I can change over the Strg * F1 in the virtuell Console and can the folling commands drop.

"systemctl --failed"
```
UNIT           LOAD   ACTIVE SUB    DESCRIPTION
&#9679; vmware.service loaded failed failed LSB: This service starts and stops VMware services

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.

1 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.
```

"systemctl list-units-files", see Attachment. Have you any idea where I can search? Something seems to be charged with systemd?

Thanks for Helping

Stefan Harbich

---

### Post by T.J. on 2016-10-24
Because 14.04 uses Upstart, and 16.04  uses Systemd, I recommend that you perform a clean install rather than an upgrade.

---

### Post by sharbich on 2016-10-28
Hi T.J.,
the solution was too extensive for me. I have activated the debug logging in the Grub boot menu in the /etc/default/grub ```
GRUB_CMDLINE_LINUX="systemd.log_target=kmsg systemd.log_level=debug"
``` And execute the following commands ```
apdate-grub
reboot
``` and the reboot I see the following message in the boot process ```
[FAILED] Failed to start Simple Desktop Display Manager. See 'systemctl status sddm.service' for details.
``` When I searched the Internet for this error message I received the following solution [URL="http://askubuntu.com/questions/776926/upgrade-from-15-10-to-16-04-now-simple-desktop-display-manager-sddm-wont-star"]http://askubuntu.com/questions/776926/upgrade-from-15-10-to-16-04-now-simple-desktop-display-manager-sddm-wont-star
[/URL]Nevertheless, many thanks for your approach. This would have cost me a lot of time.
Thanks for helping
Stefan Harbich

---

### Post by T.J. on 2016-10-29
> **sharbich said:**
> Hi T.J.,
the solution was too extensive for me. I have activated the debug logging in the Grub boot menu in the /etc/default/grub ```
GRUB_CMDLINE_LINUX="systemd.log_target=kmsg systemd.log_level=debug"
``` And execute the following commands ```
apdate-grub
reboot
``` and the reboot I see the following message in the boot process ```
[FAILED] Failed to start Simple Desktop Display Manager. See 'systemctl status sddm.service' for details.
``` When I searched the Internet for this error message I received the following solution [URL="http://askubuntu.com/questions/776926/upgrade-from-15-10-to-16-04-now-simple-desktop-display-manager-sddm-wont-star"]http://askubuntu.com/questions/776926/upgrade-from-15-10-to-16-04-now-simple-desktop-display-manager-sddm-wont-star
[/URL]Nevertheless, many thanks for your approach. This would have cost me a lot of time.
Thanks for helping
Stefan Harbich


Well done!

I had not considered sddm.

---

