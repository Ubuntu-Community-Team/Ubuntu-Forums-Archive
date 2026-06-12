---
title: "Rlease upgrade to Vivid not workin correctly"
date: 2015-04-28
forum: Installation &amp; Upgrades
---

### Post by dwaltz on 2015-04-28
On my HTPC the upgrade from Utopic to Vivid did not complete.
The PC has a history of year of correct upgrades. 
Also note I already used the experimental version of systemd under Utopic.

What happens now is that [FONT=courier new]grub [/FONT]fails to complete the upgrade and blocked other packages.

The error I get is that the configuration fails when executing [FONT=courier new]/usr/sbin/grub-mkconfig[/FONT] with the error

```
/usr/sbin/grub-mkconfig: 1: /etc/default/grub.d/init-select.cfg: get-init: not found
```

[FONT=courier new]/etc/default/grub.d/init-select.cfg[/FONT] contains a single line:

```
GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT $(get-init)"
```

the point seems to be that the **[FONT=courier new]get-init[/FONT]** is bundled with the [FONT=courier new]init-select[/FONT] package, that is included in Debian Jessie, but it was [not included in Vivid]("https://launchpad.net/ubuntu/vivid/+missingpackages?batch=75&memo=150&start=150").
For the moment I commented the single offending line in [FONT=century gothic]/etc/default/grub.d/init-select.cfg[/FONT] and completed the installation.

Do you have on your installations the same reference to [FONT=courier new]get-init[/FONT] in [FONT=courier new]/etc/default/grub.d/init-select.cfg[/FONT]?
Is get-init present on your system? If so how?
Any suggestion?
Is, e.g., safe to try to install the package from the Debian repo even if it was left out?

thanks in advance
dwaltz

---

