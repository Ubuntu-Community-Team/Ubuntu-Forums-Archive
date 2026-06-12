---
title: "Unusual software update just now regarding kernel"
date: 2018-01-23
forum: Installation &amp; Upgrades
---

### Post by nick210 on 2018-01-23
Hi,

I've just done the latest security update on 16.04 and it seemed a bit unusual, in the sense that:

* if I used update-manager, it appeared to do a dist-upgrade rather than plain upgrade
* if I use command-line apt, it kept back some packages, specifically the following (all kernel or bootloader related):

grub-common
grub-efi-amd64
grub-efi-amd64-bin
grub-efi-amd64-signed
grub2-common
linux-generic-hwe-16.04
linux-headers-generic-hwe-15604
linux-image-generic-hwe-16.04
linux-signed-generic-hwe-16.04
linux-signed-image-generic-hwe-1604
shim

In the end I let the update-manager do the dist-upgrade and it appears to have "worked" without any obvious errors (successful reboot, internet still working etc) but the behaviour did seem a bit odd. I've noticed now my kernel is "efi.signed" which I don't think it was before.

Is there anything odd here? I'm presuming it's related to the recent security hole in CPUs earlier this month?

Thanks,
Nick

---

### Post by deadflowr on 2018-01-23
Update-manager always runs dist-upgrade.
Or what would be a comparable command to dist-upgrade.
> Is there anything odd here? I'm presuming it's related to the recent security hole in CPUs earlier this month?
Yes indeed, new updated kernels with patches were released yesterday:
[https://usn.ubuntu.com/usn/usn-3541-2/]("https://usn.ubuntu.com/usn/usn-3541-2/")
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown")

---

