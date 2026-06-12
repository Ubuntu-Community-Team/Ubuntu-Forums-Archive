---
title: "VmWare not working after ubuntu upgrade to 24.04 LTS"
date: 2024-05-05
forum: Installation &amp; Upgrades
---

### Post by moelharrak on 2024-05-05
Hi,
After I did Ubuntu Upgrade from 22.04 LTS to 24.04 LTS , the vnware-player (17.5.0.22583795) is no more working.
when I try to open it, it ask me compile several modules and load them into the running kernel, when I try to do so it fails with a message "unable to install all modules..."
any idea what could be the issue?

Thank you

---

### Post by MAFoElffen on 2024-05-05
<< This should be moved to the Virtualization Section. >>

It's a failure of VMware modules vmmon-only & vmnet-only to compile with Linux kernel 6.8. Not really a Linux or Ubuntu problem, but rather a problem with the VMware code.

Here are the proposed patches for VMware Player/Workstation 17.5.1: [https://github.com/mkubecek/vmware-host-modules/tree/workstation-17.5.1](https://github.com/mkubecek/vmware-host-modules/tree/workstation-17.5.1)

Here are the instructions to compile them: [https://unix.stackexchange.com/questions/773558/vmware-vmmon-vmnet-17-5-1-and-linux-kernel-6-8-0-wont-compile](https://unix.stackexchange.com/questions/773558/vmware-vmmon-vmnet-17-5-1-and-linux-kernel-6-8-0-wont-compile)

---

