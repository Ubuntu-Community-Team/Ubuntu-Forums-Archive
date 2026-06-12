---
title: "Upgraded from 22.04 LTS to 24.04 and now the GUI is not starting"
date: 2024-10-03
forum: Installation &amp; Upgrades
---

### Post by k-burkart on 2024-10-03
I upgraded from Ubuntu 22.04 to 24.04 and am using a MSI delta 15 Notebook with an integrated and a dedicated AMD GPU.

After the upgrade, the GUI doesn`t start. I end up with a white screen and a message "... something went wrong... contact the administrator..."

I switch to tty2 ctrl + alt + F2 and run: $ sudo systemctl status display-manager.service 

It`s active and running but gives me the following mesages, too:

...
gdm3 [1779]: Gdm: GdmDisplay: Session never registered, failing
gdm3 [1779]: Gdm: GdmDisplay: Child process -1826 was already dead
...

I followed all the instructions in forums related to gdm3 reinstallation and ... --fix-broken ..., sudo dpgk --configure -a ... to make sure, the upgrade is generally ok, and there were no issues.

I can only assume, that there`s a grafics driver problem?!  Note: I have AMD ROCm installed which may have to be considered in this context.

$ journalctl -b includes the following:
systemd-udevd[487] /etc/udecv/rules.d/70-amdgpu.rules:1 Invalid operator for GROUP.  Note: I have AMD ROCm installed

How can I fix this issue so the GUI starts?

---

